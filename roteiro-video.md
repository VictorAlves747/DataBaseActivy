# Roteiro do vídeo — Entrega 2

[Relatório](README.md) · [DER conceitual](der/der-conceitual.png) · [Modelo lógico](modelo-logico/modelo-logico.png) · [SQL](docs/script.sql) · [Guia de execução](docs/guia-execucao.md)

## Duração e divisão

Vídeo de aproximadamente 6 minutos, com limite máximo de 8 minutos. Cada bloco reserva cerca de 1min30 para fala e demonstração. A divisão abaixo organiza a gravação, sem atribuir autoria exclusiva das etapas aos integrantes.

| Tempo | Integrante | Tema | Mostrar na tela |
|---|---|---|---|
| 0:00–1:30 | João Gustavo Bento de Souza | Organização, entrevista e problema | README, seção da pesquisa e uma foto da entrevista |
| 1:30–3:00 | Mateus Martins Gonçalves | Processos e DER conceitual | Fluxo comercial e DER com zoom nas relações |
| 3:00–4:30 | Raul Borges Sim | Modelo lógico, dicionário e integridade | Modelo lógico, dicionário e trechos do SQL |
| 4:30–6:00 | Victor Alves Rodrigues Braulino | Consultas, validação e conclusão | Resultados G03/G04 e A04; registro dos testes |

As falas são sugestões para ensaio. O tempo depende do ritmo e das pausas para mostrar os arquivos; medir a gravação real. A margem até 8 minutos serve para transições e explicações, não precisa ser preenchida.

## 1. João — pesquisa e problema

**Tela:** começar no título e integrantes do README; depois mostrar a caracterização e uma foto da entrevista. Evitar permanecer sobre telefone ou outros contatos, que não são necessários à explicação.

**Fala sugerida:**

“Olá, professor. Nosso trabalho trata da modelagem de um banco de dados para a operação de seguros pesquisada junto ao Bradesco. O grupo é formado por João, Mateus, Raul e Victor. A visita ocorreu na agência 1363, em São Paulo, e a entrevista registrada foi realizada em 2 de novembro de 2026, com Patrícia dos Santos Souza.

Na pesquisa, identificamos informações distribuídas entre Excel, Google Planilhas e anotações em papel. Também foi relatado o uso de um quadro de vidro para organizar visitas. Esse cenário exige atualizações manuais e dificulta reunir o histórico do cliente.

Por isso, o projeto propõe centralizar clientes, cotações, propostas, apólices e os registros relacionados ao atendimento e acompanhamento dos seguros. O escopo é essa operação de seguros, e não todos os serviços bancários da agência. Aqui no repositório estão a documentação da pesquisa e as evidências da visita. A partir dessas informações, organizamos os requisitos e as regras que orientam os modelos que vamos mostrar.”

## 2. Mateus — processos e modelo conceitual

**Tela:** abrir um fluxograma comercial e o DER; ampliar Cliente–Cotação, Cotação–Proposta e Proposta–Apólice. Não tentar ler as 11 entidades uma por uma.

**Fala sugerida:**

“O fluxo principal começa no cliente, passa pela cotação, segue para a proposta e pode resultar em uma apólice. Essas etapas foram separadas porque nem toda cotação avança para uma contratação. Assim, conseguimos preservar também os registros que não geraram um seguro contratado.

O modelo conceitual tem onze entidades e mostra os atributos, os relacionamentos e suas cardinalidades. Por exemplo, uma cotação pode originar várias propostas, mas cada proposta pertence a uma única cotação. Já uma proposta pode gerar no máximo uma apólice.

Também consideramos as regras confirmadas na entrevista: uma apólice pode ser cadastrada antes de suas parcelas e pode ter vários sinistros. Cada parcela admite no máximo um pagamento, sem pagamentos parciais. As renovações registradas representam somente processos concluídos.

Os losangos representam relações como realiza, origina e possui. Neste modelo ainda não aparecem tipos SQL nem chaves estrangeiras. Ele apresenta a organização dos dados e as regras do negócio; no próximo modelo, essas relações são transformadas em tabelas e campos.”

## 3. Raul — modelo lógico e SQL

**Tela:** mostrar Cotação e seu id_cliente no lógico; abrir o dicionário; no SQL, localizar pagamento, UNIQUE e registrar_pagamento.

**Fala sugerida:**

“No modelo lógico, as entidades foram convertidas em onze tabelas. Aqui aparecem as chaves primárias, que identificam os registros, as chaves estrangeiras, que conectam as tabelas, e os tipos de dados. Por exemplo, a tabela Cotação possui uma referência ao cliente.

O dicionário detalha o significado dos campos, os tipos, a obrigatoriedade e as restrições. A separação das tabelas evita repetir informações, como o nome da seguradora em todas as cotações, e ajuda a manter consistência quando um dado é atualizado.

No SQL, usamos restrições para proteger os registros. O CPF deve ser único, as referências precisam existir e a data final de vigência deve ser posterior à inicial. Na tabela Pagamento, uma restrição UNIQUE na referência à parcela impede dois pagamentos para a mesma parcela.

A rotina registrar_pagamento reúne a inserção do pagamento e a atualização da parcela em uma transação. Se ocorrer uma falha, as alterações são desfeitas. Existem também verificações para que a data do sinistro respeite a vigência da apólice. Essas regras foram implementadas e testadas, além de serem documentadas.”

## 4. Victor — demonstração e conclusão

**Tela:** mostrar resultados reais de execução de G03 e G04, com os parâmetros do script; mostrar A04 e o registro de validação. Se o banco não estiver disponível, mostrar o SQL e o relatório de testes, dizendo explicitamente que são registros de execução anterior.

**Fala sugerida:**

“Para testar a implementação, a massa de dados contém mil duzentos e sessenta e seis registros fictícios. Eles não são dados reais de clientes. O registro de validação documenta a execução em MySQL 8.4.13, a conferência de dez consultas gerenciais, oito auditorias e trinta e um casos de rejeição de dados inválidos.

A consulta G03 identifica parcelas vencidas sem pagamento na data de referência. A G04 mostra apólices próximas do vencimento e permite verificar renovações registradas. A janela de trinta dias é uma decisão técnica da demonstração, e não uma regra confirmada da organização.

A auditoria A04 verifica divergências entre a situação da parcela e a existência de pagamento. Na massa válida, o resultado esperado é não encontrar inconsistências. Também foram registrados testes de pagamentos simultâneos e de reversão em caso de falha.

Com isso, o projeto oferece uma base para consultar o histórico, acompanhar vencimentos e reduzir inconsistências. Ele ainda tem limites documentados, como regras de juros e descontos não confirmadas. Uma evolução futura poderia apoiar painéis gerenciais; nenhum modelo de inteligência artificial foi treinado com esses dados. Obrigado.”

## Antes de gravar e entregar

1. Abrir os arquivos na ordem de cada bloco, usar zoom legível e fechar notificações e abas pessoais.
2. Para demonstrar execução, seguir o [guia](docs/guia-execucao.md) em ambiente de testes. Não apagar um banco existente. Executar os parâmetros de data na mesma conexão das consultas.
3. Usar a data de referência do script para reproduzir a demonstração. Não substituir pela data atual sem explicar a mudança de resultados.
4. Gravar cada trecho com cronômetro. Falar com as próprias palavras e apontar o que está sendo explicado na tela, sem rolar rapidamente pelo relatório inteiro.
5. Juntar os quatro trechos na ordem proposta, conferir áudio, legibilidade e duração total inferior a 8 minutos. Se algum resultado divergir, conferir antes de narrá-lo como correto.
6. Inserir no README o link do vídeo final e conferir se o professor consegue acessá-lo. A gravação e a entrega ainda precisam ser realizadas pelo grupo.

Roteiro preparado com apoio de IA a partir da documentação do projeto e dos testes registrados. Os integrantes devem conferir e adaptar a fala ao que efetivamente demonstram.
