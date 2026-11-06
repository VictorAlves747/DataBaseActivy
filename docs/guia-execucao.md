# Execução e demonstração no MySQL

## Ambiente

SQL para MySQL 8.0.16 ou superior, testado em MySQL Community Server 8.4.13. Utilizar uma instalação de testes e dados fictícios. A conta usada na importação precisa poder criar banco, tabelas, índices, triggers e rotinas. O arquivo não cria usuários, senhas ou permissões de produção.

## Importação

1. Abra uma conexão no MySQL Workbench.
2. Abra `docs/script.sql` pelo menu File → Open SQL Script.
3. Execute o arquivo inteiro. Os comandos DELIMITER devem ser preservados.
4. Confira as mensagens de execução antes de prosseguir. O banco `corretora_seguros_e2` não pode existir previamente: o script falha nessa situação e não apaga dados.
5. Se já importou outra versão, faça a nova importação em uma instância de testes vazia. Não continue manualmente após erros de criação.

Alternativa pelo cliente mysql: conecte-se com o usuário da instalação e execute `SOURCE C:/caminho/do/projeto/docs/script.sql;`, ajustando o caminho. Não execute em SQLite ou PostgreSQL.

## Conferência inicial

```sql
USE corretora_seguros_e2;
SHOW TABLES;
SHOW TRIGGERS;
SELECT COUNT(*) AS clientes FROM cliente; -- 90
SELECT COUNT(*) AS apolices FROM apolice; -- 120
SELECT COUNT(*) AS pagamentos FROM pagamento; -- 156
```

São 11 tabelas, 3 triggers e 1 rotina. A massa tem 1.266 registros. As consultas A01–A08 devem retornar zero linhas. Os exemplos UPDATE/DELETE do arquivo são revertidos por ROLLBACK.

## Registro de pagamento

A rotina recebe parcela, data, valor efetivamente pago e forma. Ela bloqueia a parcela durante a gravação, recusa duplicidade e desfaz a operação inteira em caso de erro. Chamar isoladamente, sem transação anterior aberta, pois a rotina executa START TRANSACTION e COMMIT/ROLLBACK. Não envolver a chamada em uma transação esperando desfazê-la depois.

Exemplo para uma cópia descartável da base: o comando abaixo efetiva um pagamento e altera as contagens da massa.

```sql
SELECT MIN(r.id_parcela) INTO @parcela_teste
FROM parcela r LEFT JOIN pagamento p ON p.id_parcela=r.id_parcela
WHERE r.status='Pendente' AND p.id_pagamento IS NULL;
SELECT valor INTO @valor_teste FROM parcela WHERE id_parcela=@parcela_teste;
CALL registrar_pagamento(@parcela_teste,'2026-10-31',@valor_teste,'Pix');
SELECT r.id_parcela,r.status,p.data_pagamento,p.valor_pago
FROM parcela r JOIN pagamento p ON p.id_parcela=r.id_parcela
WHERE r.id_parcela=@parcela_teste;
```

Uma segunda chamada para a mesma parcela deve ser recusada. A rotina não implementa estorno nem altera regras de juros/descontos. O valor informado deve refletir a quitação; o banco não compara esse valor ao da parcela enquanto tais regras não forem esclarecidas. Acesso direto às tabelas continua possível para o usuário administrador e deve ser conferido pela auditoria A04.

## Vigência de sinistros

Os triggers bloqueiam INSERT/UPDATE de sinistros fora da vigência, inclusive ao trocar a apólice vinculada. Também impedem que uma mudança de vigência da apólice deixe sinistros existentes fora do período. Os dias inicial e final são aceitos. Em caso de concorrência, a aplicação deve tratar eventual bloqueio ou deadlock e repetir a transação integralmente quando apropriado.

## Roteiro de demonstração

- G03: parcelas vencidas sem quitação na data de referência.
- G04: apólices próximas do vencimento e renovações registradas.
- G07: conversão de cotações sem duplicação por várias propostas.
- G08: percentual do valor vencido ainda em aberto.
- A04/A05: consistência financeira e temporal.

Executar os blocos correspondentes do script, incluindo suas variáveis. A referência fixa é 31/10/2026; não é a data atual. Os integrantes devem explicar as junções, as cardinalidades e os resultados. Repetir a demonstração no computador que será usado em sala.

## Limites conhecidos

CPF tem validação de formato e unicidade, sem dígitos verificadores; os números são fictícios. O modelo não inclui funcionalidades bancárias não levantadas, nem regras ainda não confirmadas para renovação, estorno, juros ou desconto. A rotina de pagamento é um caminho transacional seguro, não substitui controle de permissões de uma aplicação. As consultas analíticas não constituem prova de desempenho em produção.
