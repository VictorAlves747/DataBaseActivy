# Validação do script no MySQL

Data: 02/11/2026. MySQL Community Server 8.4.13. Instância local isolada, sem conexão TCP e com dados exclusivamente fictícios.

## Resultado

- Script completo executado em banco vazio sem erros. Resultados: 310 linhas.
- 11 tabelas e 1266 registros: contagens conferidas após UPDATE/DELETE com ROLLBACK.
- Valores das três parcelas fictícias somam exatamente o valor de cada proposta, sem diferença de centavos.
- G01: 35 linhas; Qual é o histórico integrado do cliente selecionado?
- G02: 90 linhas; Quais cotações estão sem proposta e quais propostas ainda não geraram apólice?
- G03: 38 linhas; Quais parcelas vencidas continuam sem pagamento?
- G04: 10 linhas; Quais apólices vencem nos próximos 30 dias e já possuem renovação registrada?
- G05: 5 linhas; Quais sinistros estão em acompanhamento?
- G06: 4 linhas; Quantos atendimentos e visitas foram registrados por mês?
- G07: 2 linhas; Qual a taxa de conversão das cotações de cada mês em contratação até a data de referência?
- G08: 1 linhas; Qual percentual do valor vencido permanece sem pagamento na data de referência?
- G09: 2 linhas; Quantas apólices iniciaram vigência e qual o valor médio de suas propostas por mês?
- G10: 1 linhas; Quantas renovações concluídas foram registradas por mês?
- A01: 0 linhas; Existem CPFs duplicados?
- A02: 0 linhas; Existe proposta vinculada a mais de uma apólice?
- A03: 0 linhas; Existe parcela com mais de um pagamento?
- A04: 0 linhas; Existem parcelas cujo status contradiz a existência de pagamento?
- A05: 0 linhas; Existe sinistro fora da vigência informada?
- A06: 0 linhas; Existem renovações sem data de conclusão ou sem apólice válida?
- A07: 0 linhas; Existem números de parcela repetidos na mesma apólice?
- A08: 0 linhas; Existem períodos de vigência inválidos?
- Indicadores G06–G10 e parcelas de G03 comparados com resultados esperados calculados independentemente.
- REJEIÇÃO OK: PK duplicada (erro MySQL 1062).
- REJEIÇÃO OK: CPF duplicado (erro MySQL 1062).
- REJEIÇÃO OK: CPF com letras (erro MySQL 3819).
- REJEIÇÃO OK: Nome em branco (erro MySQL 3819).
- REJEIÇÃO OK: Nascimento ausente (erro MySQL 1048).
- REJEIÇÃO OK: Cliente inexistente na cotação (erro MySQL 1452).
- REJEIÇÃO OK: Seguradora inexistente na cotação (erro MySQL 1452).
- REJEIÇÃO OK: Tipo inexistente na cotação (erro MySQL 1452).
- REJEIÇÃO OK: Proposta com cotação inexistente (erro MySQL 1452).
- REJEIÇÃO OK: Apólice com proposta inexistente (erro MySQL 1452).
- REJEIÇÃO OK: Duas apólices para mesma proposta (erro MySQL 1062).
- REJEIÇÃO OK: Vigência invertida (erro MySQL 3819).
- REJEIÇÃO OK: Valor de parcela negativo (erro MySQL 3819).
- REJEIÇÃO OK: Parcela sem valor positivo (erro MySQL 3819).
- REJEIÇÃO OK: Número de parcela zero (erro MySQL 3819).
- REJEIÇÃO OK: Número repetido na mesma apólice (erro MySQL 1062).
- REJEIÇÃO OK: Parcela com apólice inexistente (erro MySQL 1452).
- REJEIÇÃO OK: Dois pagamentos para mesma parcela (erro MySQL 1062).
- REJEIÇÃO OK: Pagamento em parcela inexistente (erro MySQL 1452).
- REJEIÇÃO OK: Pagamento sem valor positivo (erro MySQL 3819).
- REJEIÇÃO OK: Forma de pagamento vazia (erro MySQL 3819).
- REJEIÇÃO OK: Status inválido (erro MySQL 3819).
- REJEIÇÃO OK: Sinistro sem apólice (erro MySQL 1452).
- REJEIÇÃO OK: Renovação sem conclusão (erro MySQL 1048).
- REJEIÇÃO OK: Renovação sem apólice (erro MySQL 1452).
- REJEIÇÃO OK: Atendimento sem cliente (erro MySQL 1452).
- REJEIÇÃO OK: Exclusão de cliente referenciado (erro MySQL 1451).
- REJEIÇÃO OK: Exclusão de apólice com parcelas (erro MySQL 1451).
- A04: anomalia inserida em transação foi detectada e revertida; auditoria voltou a zero.
- A05: anomalia inserida em transação foi detectada e revertida; auditoria voltou a zero.
- Cenários válidos preservados: várias propostas por cotação, apólice sem parcelas e vários sinistros por apólice.

## Correção realizada

A divisão de algumas propostas em três parcelas produzia uma diferença de R$ 0,01. A massa passou a ser calculada em centavos, com o restante na última parcela. O arquivo corrigido foi executado novamente do zero. Essa distribuição é um cenário fictício de teste; não estabelece uma nova regra comercial.

## Limites

A04 e A05 detectam inconsistências entre tabelas, mas não as bloqueiam automaticamente. Não foram implementadas regras de juros, descontos ou estornos que ainda dependem de informação da organização. Estes testes foram realizados na versão indicada; outra instalação deve executar o mesmo arquivo antes da apresentação.

SHA-256 do texto SQL validado (UTF-8, quebras de linha LF): `112fd5e638570eeeb33e417bee1ddfcbe712f373a0b25a9f9b20b933dd045dd0`.
