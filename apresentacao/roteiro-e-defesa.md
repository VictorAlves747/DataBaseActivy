# Roteiro de apresentação e defesa

[Slides em PDF](apresentacao-entrega-2.pdf) · [Relatório](../README.md) · [Execução do SQL](../docs/guia-execucao.md)

## Oito minutos

| Slide | Tempo | Explicação e demonstração |
|---|---|---|
| 1. Contexto | 50 s | Descrever os controles observados e o problema de informação fragmentada. Distinguir a operação de seguros da agência inteira. |
| 2. Solução | 50 s | Percorrer Cliente → Cotação → Proposta → Apólice. Explicar por que uma cotação sem contratação continua registrada. |
| 3. Conceitual | 45 s | Ler Cotação–Proposta nos dois sentidos e apontar a posição dos pares. Abrir o DER completo se necessário. |
| 4. Lógico | 45 s | Mostrar FK + NOT NULL + UNIQUE em Pagamento. Explicar a ausência de linha enquanto não ocorre pagamento. |
| 5. SQL | 90 s | Mostrar as tabelas no MySQL, um CHECK e a rotina registrar_pagamento. Explicar bloqueio, COMMIT e ROLLBACK; apresentar os testes executados. |
| 6. Consultas | 100 s | Executar G03, G04 e G07 com referência 31/10/2026; interpretar a unidade de cada linha. Mostrar A04/A05 sem inconsistências. |
| 7. BI/IA | 50 s | Explicar G08 e a diferença entre valor em reais e percentual. Separar demonstração fictícia de previsão real. |
| 8. Benefícios | 50 s | Relacionar histórico, controle de vencimentos e integridade às decisões. Indicar os limites reais ainda não confirmados. |

Total: 480 segundos. Responsáveis por cada trecho: conteudo pendente. A divisão deve refletir a participação efetiva; todos devem conhecer o conjunto.

## Preparação da demonstração

1. Executar o script completo em ambiente de testes com MySQL 8.0.16 ou superior e banco de destino ainda inexistente. Não apagar um banco existente para liberar o nome.
2. Confirmar versão, 11 tabelas e 1.266 registros. Deixar o arquivo aberto nos trechos G03, G04, G07 e A04/A05.
3. As variáveis de data pertencem à sessão: executar novamente os SETs se abrir uma nova conexão.
4. G04 deve retornar dez apólices, cinco com renovação e cinco sem. G07 deve mostrar 90 cotações e 55 com vigência iniciada em cada mês, 61,11%.
5. A massa varia: 80 atendimentos/visitas em setembro e 100 em outubro; a média de propostas de G09 passa de R$ 1.700 para R$ 1.870. Nada disso é resultado comercial real.
6. Ensaiar com cronômetro, conexão e permissões do computador da apresentação. A execução local registrada não substitui esse ensaio.

## Perguntas para a defesa individual

| Pergunta | Fundamento da resposta |
|---|---|
| Por que há três entidades comerciais? | Cotação, proposta e apólice são etapas distintas; algumas ocorrências não avançam. Separá-las preserva o histórico sem exigir campos de contrato antes dele existir. |
| Como ler Cotação–Proposta? | Uma proposta pertence a uma cotação; uma cotação origina zero ou várias propostas. O par junto à entidade conta ocorrências dela. |
| Por que uma apólice pode não ter parcelas? | A entrevista confirmou que o contrato pode ser cadastrado primeiro. A FK em Parcela obriga cada parcela a ter uma apólice, mas não obriga a apólice a ter parcelas. |
| FK sozinha impede dois pagamentos? | Não. A FK assegura existência da parcela; UNIQUE em pagamento.id_parcela limita a um pagamento. NOT NULL torna o vínculo obrigatório. |
| Quais são as chaves candidatas? | Além das PKs: CPF; id_proposta em Apólice; id_parcela em Pagamento; (id_apolice, numero_parcela) em Parcela. |
| O que a 2FN exige da chave composta? | Valor e vencimento dependem da parcela identificada pela combinação completa, não só da apólice ou do número isolado. |
| Qual anomalia a 3FN evita? | Repetir nome da seguradora em cada cotação exigiria várias atualizações. O nome fica em Seguradora e é recuperado por JOIN. |
| Como uma falha no pagamento é tratada? | A rotina controla sua própria transação, bloqueia a parcela, insere o pagamento e atualiza a situação. O tratamento de erro executa ROLLBACK e propaga a falha. Deve ser chamada sem transação anterior aberta. |
| E duas gravações simultâneas? | O bloqueio serializa o acesso à parcela e UNIQUE é uma proteção adicional. O teste com duas conexões aceitou um pagamento e rejeitou o outro. |
| Por que G07 usa EXISTS? | Cada cotação deve ser contada uma vez, mesmo com várias propostas. JOIN sem cuidado pode multiplicar o numerador. |
| O que G08 mede? | Percentual do valor vencido ainda sem pagamento na data de referência, não percentual de clientes nem previsão de inadimplência futura. |
| Por que G09 não é faturamento? | Agrupa pelo início da vigência e usa o valor da proposta. Comissão, prêmio e receita não foram equiparados pelo levantamento. |
| A04 impede inconsistências? | Não; detecta divergência. A rotina transacional evita a falha no fluxo previsto, mas alterações diretas por administrador continuam exigindo controle e auditoria. |
| Por que não impor igualdade ao valor pago? | O grupo ainda precisa confirmar juros, descontos e estornos. Uma restrição sem essa informação poderia rejeitar uma quitação válida. |
| Como provar uma renovação concluída? | Data e FK válidas demonstram integridade estrutural; não comprovam conclusão comercial. O vínculo com a nova apólice ainda precisa ser confirmado. |
| Qual é a proposta de IA? | Evolução exploratória com histórico real e validação temporal. Nenhum modelo preditivo foi treinado ou validado com a massa fictícia. |

## Fontes e autoria

Slides e guia foram preparados com apoio de IA, com base no relatório, nas respostas do grupo e nos testes de 07/11/2026. A fala, a conferência das informações de campo e a defesa individual cabem aos integrantes. Não se declara ensaio nem apresentação já realizados.
