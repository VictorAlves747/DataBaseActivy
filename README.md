# PROJETO DE MODELAGEM DE BANCO DE DADOS

## Corretora de Seguros — Bradesco

> **Entrega 1 — Modelo Conceitual (DER)** · Versão revisada — validação de campo pendente nos pontos indicados na seção 6.5.

[Dicionário de dados em HTML](dicionario_de_dados.html) · [Diagrama Entidade-Relacionamento](DER-corretora.jpeg)

## Metadados

| Integrante | RGM |
| --------------------------- | -------- |
| Mateus Martins Gonçalves    | 47812222 |
| Raul Borges Sim             | 48247634 |
| João Gustavo Bento de Souza | 42283671 |
| Victor Alves Rodrigues Braulino | 48216305 |

---

# 1. Caracterização da Organização

## 1.1 Nome e natureza da organização

O objeto deste projeto é a operação de **corretagem de seguros que atua junto ao Bradesco**, conforme relato do grupo. As fotografias identificam o local visitado como **Bradesco Empresas e Negócios**. O modelo abrange a operação de seguros descrita na entrevista, e não o banco Bradesco como um todo. A razão social da corretora e o vínculo com a unidade visitada ainda precisam ser confirmados pelo grupo.

A organização atua no segmento de seguros, oferecendo diferentes modalidades de produtos para seus clientes. Entre os tipos de seguros trabalhados estão:

- Seguro Auto;
- Seguro Residencial;
- Seguro Empresarial;
- Seguro de Vida;
- Seguro Saúde;
- Seguro Dental;
- Outros tipos de seguros disponibilizados pelas companhias parceiras.

A corretora possui fins lucrativos e está em funcionamento desde **2016**.

## 1.2 Contexto e porte

Atualmente, a organização conta com aproximadamente **6 funcionários**.

De acordo com as informações obtidas durante a pesquisa de campo, a corretora atende aproximadamente **50 a 100 clientes por mês** e comercializa cerca de **50 a 60 seguros mensalmente**, considerando todos os produtos oferecidos.

O faturamento médio mensal informado é de aproximadamente **R$ 60.000,00**.

A operação envolve diversas atividades, incluindo cadastro de clientes, atendimento, elaboração de cotações, acompanhamento de propostas, contratação de seguros, controle de apólices, acompanhamento de parcelas e pagamentos, atendimento de sinistros e renovação de apólices.

## 1.3 Problemas e necessidades identificados

Durante a pesquisa de campo, foi observado que grande parte das informações operacionais é controlada por meio de **Excel e Google Planilhas**.

As cotações e propostas são acompanhadas por planilhas, assim como os pagamentos e parcelas dos seguros.

O acompanhamento dos atendimentos também utiliza planilhas. Em determinadas situações, durante uma visita ao cliente, as informações são inicialmente anotadas em **folhas de papel** e posteriormente utilizadas para atualizar os controles.

A organização também utiliza um **quadro de vidro** para organizar as visitas que serão realizadas durante a semana.

Outro processo específico é o acompanhamento de sinistros, que é realizado por uma funcionária especializada nessa atividade, responsável pelas listagens e pelo acompanhamento dos casos.

As renovações são acompanhadas por Excel e Google Planilhas. A corretora também recebe um link da sucursal, no qual são registrados os seguros fechados, auxiliando na identificação das apólices próximas ao vencimento.

### Principais problemas identificados

- Informações distribuídas entre Excel e Google Planilhas;
- Dependência de controles manuais;
- Utilização de papel durante determinados atendimentos e visitas;
- Necessidade de atualizar informações manualmente após as visitas;
- Controle visual de visitas por meio de quadro de vidro;
- Dificuldade de centralizar o histórico dos clientes;
- Controle manual de parcelas e pagamentos;
- Necessidade de acompanhar constantemente os vencimentos das apólices;
- Controle das renovações realizado por diferentes ferramentas;
- Informações de sinistros concentradas em um controle específico.

Diante desse cenário, o projeto propõe a modelagem de um banco de dados capaz de **centralizar e organizar as principais informações da corretora**.

---

## 1.4 Justificativa da escolha

A corretora foi escolhida por ser uma organização real na qual o grupo teve acesso para realizar pesquisa de campo e levantar informações diretamente relacionadas aos processos de negócio.

A organização apresenta características adequadas para um projeto de banco de dados, pois trabalha diariamente com grande quantidade de informações relacionadas a clientes, seguros, seguradoras, cotações, propostas, apólices, pagamentos, atendimentos, sinistros e renovações.

Além disso, a utilização de Excel, Google Planilhas e registros manuais demonstra uma oportunidade de melhoria por meio da centralização das informações em um banco de dados.

A escolha também possibilita desenvolver um modelo que poderá futuramente ser utilizado como base para um sistema informatizado de gerenciamento da corretora.

---

## 1.5 Evidências da organização e da pesquisa de campo

A pesquisa de campo foi realizada presencialmente nas instalações da organização.

As fotografias abaixo foram fornecidas pelo grupo como evidências das instalações visitadas durante a pesquisa de campo.

### Foto 1 — Ambiente interno da organização

A primeira fotografia apresenta uma área interna da organização, com salas individuais separadas por divisórias de vidro e estrutura destinada à realização das atividades profissionais.

![Ambiente interno da organização, com divisórias de vidro](foto-ambiente-interno.jpeg)

### Foto 2 — Identificação visual da organização

A segunda fotografia apresenta a identificação visual **“Bradesco Empresas e Negócios”** presente nas instalações visitadas.

![Identificação visual Bradesco Empresas e Negócios](foto-identificacao.jpeg)

### Foto 3 — Fachada do local visitado

A terceira fotografia apresenta a fachada e a entrada do local visitado, com a identificação visual Bradesco.

![Fachada e entrada do local visitado](foto-fachada.jpeg)

### Dados da organização

| Informação | Dado |
| ---------------------------- | ------------------------- |
| Nome informado               | Bradesco                  |
| Segmento                     | Corretora de seguros      |
| Início das atividades        | 2016                      |
| Quantidade de funcionários   | 6                         |
| Endereço                     | Rua Rego Barros, 570      |
| E-mail informado             | alicelimna@gmail.com     |
| Responsável entrevistada     | Patrícia dos Santos Souza |
| Cargo                        | Sócia                     |
| Google Maps/Site/Rede social | Não informado             |

> **Observação:** o endereço, e-mail e identificação da organização acima foram utilizados conforme as informações fornecidas pelo grupo. Cidade, UF, CEP, razão social e vínculo com a unidade visitada ainda não foram informados. Um link de Google Maps/site/rede social pode complementar as fotos, se disponível.

---

# 2. Processos de Negócio

Com base na entrevista e na observação realizada durante a visita, foram identificados os seguintes processos.

## 2.1 Cadastro de clientes

O cadastro é realizado quando um cliente entra em contato com a corretora.

As principais informações levantadas são:

- CPF;
- Nome;
- Data de nascimento.

Essas informações são utilizadas para identificar o cliente e relacioná-lo aos demais processos da corretora.

---

## 2.2 Cotação

Após o levantamento das necessidades do cliente, a corretora realiza uma ou mais cotações.

A organização trabalha com diversos tipos de seguros e consulta diferentes seguradoras.

A **Bradesco Seguros é priorizada** nas cotações. Quando não é encontrada uma condição adequada, a corretora realiza cotações com outras companhias.

Atualmente, o acompanhamento dessas cotações é realizado por meio de Excel e Google Planilhas.

### Fluxo

**Cliente → Levantamento das necessidades → Cotação → Análise das opções → Escolha da opção**

---

## 2.3 Proposta

Após a realização da cotação, caso o cliente tenha interesse em prosseguir, é elaborada uma proposta.

A proposta representa a etapa entre a cotação e a efetiva contratação do seguro.

### Fluxo

**Cotação → Cliente analisa → Aceita prosseguir → Proposta**

Caso o cliente não prossiga, a cotação permanece registrada sem necessariamente resultar em uma apólice.

---

## 2.4 Contratação e apólice

Quando a contratação é efetivada, é gerada uma apólice.

As principais informações de apólice identificadas na pesquisa são:

- Número da apólice;
- Vigência.

A vigência representa o período durante o qual o seguro permanece válido.

### Fluxo

**Proposta → Contratação → Apólice → Controle da vigência**

---

## 2.5 Controle de parcelas e pagamentos

A corretora acompanha os pagamentos e parcelas por meio de Excel e Google Planilhas.

O sistema proposto deverá permitir relacionar cada parcela à sua respectiva apólice e registrar a situação do pagamento.

### Fluxo

**Apólice → Parcelas → Vencimento → Pagamento → Atualização do status**

---

## 2.6 Atendimento ao cliente

Os atendimentos são registrados nas planilhas de acompanhamento.

Durante visitas, os dados podem ser inicialmente registrados em papel e posteriormente transferidos para os controles digitais.

Além disso, um quadro de vidro é utilizado para organizar as visitas previstas para a semana.

### Fluxo

**Cliente → Atendimento/Visita → Levantamento de informações → Registro → Atualização do acompanhamento**

---

## 2.7 Sinistros

O processo de sinistros possui tratamento específico dentro da organização.

Uma funcionária é responsável pelo acompanhamento dos sinistros e pelas listagens relacionadas a eles.

O modelo proposto deverá permitir relacionar cada sinistro ao cliente e à apólice correspondente.

### Fluxo

**Cliente → Comunicação do sinistro → Registro → Acompanhamento → Atualização da situação**

---

## 2.8 Renovação

As renovações são acompanhadas por Excel e Google Planilhas.

A corretora também utiliza informações disponibilizadas pela sucursal para identificar seguros que estão próximos do vencimento.

Quando uma apólice se aproxima do vencimento, a corretora entra em contato com o cliente para tratar da renovação.

### Fluxo

**Apólice → Verificação do vencimento → Contato com cliente → Renovação ou encerramento**

---

# 3. Requisitos do Sistema

## 3.1 Requisitos Funcionais

| Código | Requisito funcional |
| ------------------------- | ------------------------------------------------------------------------------------------- |
| RF01                      | O sistema deve permitir cadastrar clientes.                                                 |
| RF02                      | O sistema deve permitir consultar clientes.                                                 |
| RF03                      | O sistema deve permitir atualizar dados dos clientes.                                       |
| RF04                      | O sistema deve permitir cadastrar tipos de seguros.                                         |
| RF05                      | O sistema deve permitir cadastrar seguradoras.                                              |
| RF06                      | O sistema deve permitir registrar cotações.                                                 |
| RF07                      | O sistema deve permitir relacionar uma cotação a um cliente.                                |
| RF08                      | O sistema deve permitir relacionar uma cotação a uma seguradora.                            |
| RF09                      | O sistema deve permitir registrar propostas.                                                |
| RF10                      | O sistema deve permitir acompanhar o status das propostas.                                  |
| RF11                      | O sistema deve permitir registrar apólices.                                                 |
| RF12                      | O sistema deve permitir registrar número e vigência da apólice.                             |
| RF13                      | O sistema deve permitir cadastrar parcelas.                                                 |
| RF14                      | O sistema deve permitir registrar pagamentos.                                               |
| RF15                      | O sistema deve permitir consultar parcelas pendentes e pagas.                               |
| RF16                      | O sistema deve permitir registrar atendimentos.                                             |
| RF17                      | O sistema deve permitir registrar sinistros.                                                |
| RF18                      | O sistema deve permitir acompanhar o status dos sinistros.                                  |
| RF19                      | O sistema deve identificar apólices próximas do vencimento.                                 |
| RF20                      | O sistema deve permitir registrar renovações.                                               |
| RF21                      | O sistema deve manter o histórico do cliente.                                               |
| RF22                      | O sistema deve permitir pesquisar informações por cliente, apólice, seguradora ou situação. |

---

## 3.2 Requisitos Não Funcionais

| Código | Requisito não funcional |
| ----------------------------- | ---------------------------------------------------------------------------- |
| RNF01                         | O sistema deve possuir interface simples e intuitiva.                        |
| RNF02                         | O acesso às informações deve ser protegido por autenticação.                 |
| RNF03                         | O sistema deve restringir o acesso aos dados conforme o perfil do usuário.   |
| RNF04                         | O sistema deve apresentar bom desempenho nas consultas.                      |
| RNF05                         | O banco deve preservar a integridade dos dados.                              |
| RNF06                         | O sistema deve permitir realização de backups periódicos.                    |
| RNF07                         | O sistema deve evitar duplicidade de clientes.                               |
| RNF08                         | O sistema deve permitir a inclusão de novos tipos de seguros.                |
| RNF09                         | O sistema deve permitir a inclusão de novas seguradoras.                     |
| RNF10                         | O sistema deve preservar a confidencialidade dos dados pessoais armazenados. |

---

# 4. Regras de Negócio

## 4.1 Regras operacionais e de integridade

As regras abaixo combinam informações do levantamento e restrições propostas para o sistema. Limites de cardinalidade não confirmados estão separados como hipóteses na seção 6.5.

| Código | Regra |
| ----------- | --------------------------------------------------------------------------------------------- |
| RN01        | Cada cliente deve possuir CPF, nome e data de nascimento cadastrados.                         |
| RN02        | O CPF deve identificar unicamente um cliente.                                                 |
| RN03        | A corretora trabalha com diferentes tipos de seguros.                                         |
| RN04        | Uma cotação deve estar associada a um cliente.                                                |
| RN05        | Uma cotação deve estar associada a uma seguradora.                                            |
| RN06        | A Bradesco Seguros é priorizada nas cotações, conforme informação fornecida pela organização. |
| RN07        | Outras seguradoras podem ser consultadas quando necessário.                                   |
| RN08        | Neste modelo, cada proposta tem uma cotação de origem; nem toda cotação gera proposta (hipótese H01).                                      |
| RN09        | Nem toda cotação necessariamente resulta em uma proposta.                                     |
| RN10        | Uma apólice deve possuir número e período de vigência.                                        |
| RN11        | A data inicial da vigência deve ser anterior à data final.                                    |
| RN12        | Uma apólice pode possuir várias parcelas.                                                     |
| RN13        | Uma parcela deve estar vinculada a uma apólice.                                               |
| RN14        | Um pagamento deve estar relacionado a uma parcela.                                            |
| RN15        | Um sinistro deve estar relacionado a uma apólice.                                             |
| RN16        | Os sinistros possuem acompanhamento específico dentro da organização.                         |
| RN17        | Os atendimentos devem estar relacionados aos clientes.                                        |
| RN18        | As apólices devem ser acompanhadas quanto ao vencimento.                                      |
| RN19        | Uma apólice pode entrar em processo de renovação.                                             |
| RN20        | As informações dos clientes devem ser protegidas contra acesso não autorizado.                |

---

## 4.2 Restrições organizacionais e impacto no modelo

| Código | Restrição / origem | Efeito no modelo e motivo |
|---|---|---|
| RO01 | Preferência pela Bradesco Seguros, informada na entrevista. | Seguradora possui o indicador prioridade; outras companhias continuam cadastráveis (RN06/RN07). |
| RO02 | Controles distribuídos entre planilhas, papel e quadro de visitas. | Cliente centraliza os vínculos; Atendimento registra data, tipo e descrição para conservar o histórico (RF16/RF21). O calendário completo de visitas não foi detalhado e não é prometido neste modelo. |
| RO03 | Vigência e renovação exigem acompanhamento. | Apólice possui início/fim de vigência; Renovação registra contato e resultado. O prazo de antecedência para alertas permanece a definir (RF19/RF20). |
| RO04 | Sinistros são acompanhados por uma funcionária específica. | Sinistro é uma entidade própria, vinculada à apólice, com data, descrição e status. Não se inventou cadastro de funcionários ou atribuição automática sem levantamento adicional. |
| RO05 | Confidencialidade e controle de acesso previstos nos requisitos do projeto. | CPF não deve ser repetido em entidades dependentes. Autenticação, perfis e backup são requisitos de implementação futura (RNF02/RNF03/RNF06/RNF10), ainda sem regras internas detalhadas. |
| RO06 | Cadastro informado contém CPF, nome e nascimento. | O escopo atual representa pessoa física. Apesar de existir Seguro Empresarial no catálogo, contratação por pessoa jurídica/CNPJ precisa de levantamento adicional. |

Não foram informadas outras políticas internas, prazos fixos ou exigências legais específicas. Elas não foram inventadas para preencher o roteiro.

---

# 5. Dicionário de Dados Conceitual (Preliminar)

O arquivo [dicionario_de_dados.html](dicionario_de_dados.html) contém as mesmas definições abaixo no formato HTML solicitado. Para visualizar a formatação, baixe-o e abra no navegador.

Versão preliminar revisada: entidades, atributos e referências estão padronizados entre README, HTML e DER. Os domínios e as hipóteses H01 a H06 são decisões de modelagem propostas, ainda não validadas pela entrevistada. ID indica identificador; REF indica referência de relacionamento, não um atributo descritivo adicional. Não se trata de um esquema físico ou de uma implementação SQL.

## Cliente

| Atributo / referência | Descrição | Regra de negócio associada |
|---|---|---|
| `id_cliente` (ID) | Identificador interno do cliente | Único e obrigatório; identificador interno proposto. |
| `cpf` | CPF do cliente | Obrigatório e único |
| `nome` | Nome do cliente | Obrigatório |
| `data_nascimento` | Data de nascimento | Obrigatória |

## Seguradora

| Atributo / referência | Descrição | Regra de negócio associada |
|---|---|---|
| `id_seguradora` (ID) | Identificador da seguradora | Único e obrigatório; identificador interno proposto. |
| `nome` | Nome da seguradora | Obrigatório |
| `prioridade` | Indica prioridade comercial | Indicador proposto (Sim/Não). Representa a preferência comercial informada em RN06; não impede consultar outras seguradoras. |

## TipoSeguro

| Atributo / referência | Descrição | Regra de negócio associada |
|---|---|---|
| `id_tipo_seguro` (ID) | Identificador do tipo | Único e obrigatório; identificador interno proposto. |
| `nome` | Nome do seguro | Obrigatório |
| `descricao` | Descrição do produto | Opcional |

## Cotação

| Atributo / referência | Descrição | Regra de negócio associada |
|---|---|---|
| `id_cotacao` (ID) | Identificador da cotação | Único e obrigatório; identificador interno proposto. |
| `data_cotacao` | Data da cotação | Obrigatória |
| `valor_cotado` | Valor apresentado | Valor não negativo |
| `status` | Situação da cotação | Obrigatório. Domínio técnico proposto, a validar: Em análise; apresentada; escolhida; não prosseguiu. |
| `id_cliente` (REF) | Cliente relacionado | Obrigatório; referencia exatamente uma ocorrência existente da entidade relacionada. |
| `id_seguradora` (REF) | Seguradora consultada | Obrigatório; referencia exatamente uma ocorrência existente da entidade relacionada. |
| `id_tipo_seguro` (REF) | Tipo de seguro | Obrigatório; referencia exatamente uma ocorrência existente da entidade relacionada. |

## Proposta

| Atributo / referência | Descrição | Regra de negócio associada |
|---|---|---|
| `id_proposta` (ID) | Identificador da proposta | Único e obrigatório; identificador interno proposto. |
| `data_proposta` | Data da proposta | Obrigatória |
| `status` | Situação da proposta | Obrigatório. Domínio técnico proposto, a validar: Em análise; aceita; recusada; cancelada. |
| `valor_proposta` | Valor da proposta | Não negativo |
| `id_cotacao` (REF) | Cotação de origem | Obrigatório; referencia exatamente uma ocorrência existente da entidade relacionada. Único nesta entidade, conforme hipótese H01. |

## Apólice

| Atributo / referência | Descrição | Regra de negócio associada |
|---|---|---|
| `id_apolice` (ID) | Identificador interno | Único e obrigatório; identificador interno proposto. |
| `numero_apolice` | Número da apólice | Obrigatório |
| `inicio_vigencia` | Início da vigência | Obrigatório |
| `fim_vigencia` | Fim da vigência | Obrigatório e posterior a inicio_vigencia (RN11). |
| `status` | Situação da apólice | Obrigatório. Domínio técnico proposto, a validar: Vigente; encerrada; cancelada. |
| `id_proposta` (REF) | Proposta de origem | Obrigatório; referencia exatamente uma ocorrência existente da entidade relacionada. Único nesta entidade, conforme hipótese H02. |

## Parcela

| Atributo / referência | Descrição | Regra de negócio associada |
|---|---|---|
| `id_parcela` (ID) | Identificador da parcela | Único e obrigatório; identificador interno proposto. |
| `numero_parcela` | Número da parcela | Inteiro positivo; combinação de apólice e número da parcela deve ser única (decisão técnica). |
| `valor` | Valor da parcela | Maior que zero |
| `data_vencimento` | Data de vencimento | Obrigatória |
| `status` | Situação da parcela | Obrigatório. Domínio técnico proposto, a validar: Pendente; paga. |
| `id_apolice` (REF) | Apólice relacionada | Obrigatório; referencia exatamente uma ocorrência existente da entidade relacionada. |

## Pagamento

| Atributo / referência | Descrição | Regra de negócio associada |
|---|---|---|
| `id_pagamento` (ID) | Identificador do pagamento | Único e obrigatório; identificador interno proposto. |
| `data_pagamento` | Data do pagamento | Obrigatória em todo registro de pagamento; parcela não paga não gera registro nesta entidade. |
| `valor_pago` | Valor pago | Maior que zero |
| `forma_pagamento` | Forma utilizada | Obrigatória. Domínio a confirmar com a organização; nenhuma modalidade foi informada no levantamento. |
| `id_parcela` (REF) | Parcela relacionada | Obrigatório; referencia exatamente uma ocorrência existente da entidade relacionada. Único nesta entidade, conforme hipótese H03. |

## Atendimento

| Atributo / referência | Descrição | Regra de negócio associada |
|---|---|---|
| `id_atendimento` (ID) | Identificador | Único e obrigatório; identificador interno proposto. |
| `data_atendimento` | Data do atendimento | Obrigatória |
| `tipo_atendimento` | Tipo do atendimento | Obrigatório. Valores propostos: Atendimento; Visita. Outros canais dependem de confirmação. |
| `descricao` | Informações do atendimento | Opcional |
| `id_cliente` (REF) | Cliente atendido | Obrigatório; referencia exatamente uma ocorrência existente da entidade relacionada. |

## Sinistro

| Atributo / referência | Descrição | Regra de negócio associada |
|---|---|---|
| `id_sinistro` (ID) | Identificador | Único e obrigatório; identificador interno proposto. |
| `numero_sinistro` | Número do sinistro | Quando fornecido, deve ser registrado |
| `data_sinistro` | Data da ocorrência | Obrigatória |
| `descricao` | Descrição da ocorrência | Obrigatória |
| `status` | Situação do sinistro | Obrigatório. Domínio técnico proposto, a validar: Registrado; em acompanhamento; encerrado. |
| `id_apolice` (REF) | Apólice relacionada | Obrigatório; referencia exatamente uma ocorrência existente da entidade relacionada. |

## Renovação

| Atributo / referência | Descrição | Regra de negócio associada |
|---|---|---|
| `id_renovacao` (ID) | Identificador | Único e obrigatório; identificador interno proposto. |
| `data_contato` | Data do contato com cliente | Registrada quando houver contato |
| `data_renovacao` | Data da renovação | Obrigatória quando concluída |
| `status` | Situação da renovação | Obrigatório. Domínio técnico proposto, a validar: Pendente; em contato; concluída; não renovada. |
| `id_apolice` (REF) | Apólice renovada | Obrigatório; referencia exatamente uma ocorrência existente da entidade relacionada. |

---

# 6. Modelagem Conceitual (Entidades, Atributos, Relacionamentos)

## 6.1 Entidades reconhecidas

| Entidade | Papel e justificativa |
|---|---|
| Cliente | Identifica a pessoa física que solicita cotações e recebe atendimentos; evita cadastros repetidos. |
| Seguradora | Identifica a companhia consultada, separando companhia de modalidade de seguro. |
| TipoSeguro | Mantém o catálogo de modalidades e permite cadastrar novos produtos sem criar novas entidades. |
| Cotação | Registra uma consulta para um cliente, em uma companhia e modalidade, mesmo sem contratação. |
| Proposta | Representa a etapa comercial que avança a partir de uma cotação. |
| Apólice | Registra o contrato efetivado e sua vigência. |
| Parcela | Separa cada obrigação de pagamento, com número, valor e vencimento. |
| Pagamento | Registra a ocorrência de pagamento; sua ausência permite representar uma parcela ainda não paga. |
| Atendimento | Conserva o histórico de contatos/visitas relacionado ao cliente. |
| Sinistro | Permite acompanhamento específico de ocorrências vinculadas a uma apólice. |
| Renovação | Registra o acompanhamento da renovação de uma apólice de origem, inclusive tentativas não concluídas. |

## 6.2 Atributos e classificações

Os atributos de cada entidade estão enumerados na seção 5 e no HTML. Todos são tratados como simples e monovalorados nesta abstração; nome e descrição são armazenados como uma unidade textual, sem decomposição adicional. Não há atributo multivalorado no escopo atual.

- **Identificadores:** `id_*` próprio de cada entidade, único e obrigatório. O CPF é um identificador de negócio alternativo para Cliente (RN02).
- **Descritivos:** nome, descrição, número de apólice/sinistro, tipo de atendimento e forma de pagamento.
- **Temporais:** nascimento, datas de cotação/proposta, vigência, vencimento, pagamento, atendimento, sinistro e renovação/contato.
- **Quantitativos:** valores cotado/proposto, valor da parcela, valor pago e número da parcela.
- **Categóricos:** status e prioridade. Os domínios sugeridos são decisões técnicas, não respostas atribuídas à entrevistada.
- **Referências (REF):** os 10 campos de ligação `id_*` em outras entidades expressam os 10 relacionamentos abaixo. Cotação contém três referências; as demais entidades dependentes contêm uma. Eles antecipam o mapeamento dos vínculos sem definir tipos SQL, índices ou armazenamento físico.
- **Informações derivadas:** cliente de uma apólice, de um sinistro ou de uma renovação é obtido pela cadeia Apólice → Proposta → Cotação → Cliente. Proximidade do vencimento e atraso são calculados pelas datas; não são atributos adicionais.

O número da apólice não foi declarado único globalmente: o levantamento não confirmou se diferentes seguradoras podem reutilizar a mesma numeração.

## 6.3 Relacionamentos e cardinalidades

Na tabela, **Destinos por origem** informa quantas ocorrências do destino uma ocorrência da origem pode possuir. **Origens por destino** informa o sentido inverso. `0..N` significa zero ou muitas; `0..1`, zero ou uma; `1`, exatamente uma.

| Origem | Relação | Destino | Destinos por origem | Origens por destino | Interpretação |
|---|---|---|---|---|---|
| Cliente | realiza | Cotação | 0..N | 1 | Cada cotação pertence a um cliente; um cliente pode ainda não ter cotações. |
| Seguradora | recebe | Cotação | 0..N | 1 | Cada cotação consulta uma seguradora; o cadastro pode existir antes de uma consulta. |
| TipoSeguro | classifica | Cotação | 0..N | 1 | Cada cotação corresponde a uma modalidade; um tipo pode ainda não ter cotações. |
| Cotação | origina | Proposta | 0..1 | 1 | H01: uma cotação origina no máximo uma proposta; cada proposta tem uma cotação. |
| Proposta | origina | Apólice | 0..1 | 1 | H02: uma proposta origina no máximo uma apólice; cada apólice tem uma proposta. |
| Apólice | possui | Parcela | 0..N | 1 | H04: uma apólice pode ser cadastrada antes das parcelas; cada parcela tem uma apólice. |
| Parcela | recebe | Pagamento | 0..1 | 1 | H03: uma parcela recebe no máximo um pagamento; cada pagamento pertence a uma parcela. |
| Cliente | possui | Atendimento | 0..N | 1 | Cada atendimento pertence a um cliente; o cliente pode ainda não ter atendimentos registrados. |
| Apólice | possui | Sinistro | 0..N | 1 | H05: uma apólice pode não ter sinistros ou ter vários; cada sinistro pertence a uma apólice. |
| Apólice | possui | Renovação | 0..N | 1 | H06: cada registro representa uma tentativa/processo de renovação de uma apólice de origem. |

## 6.4 Restrições e políticas aplicadas

RN02 impede duplicidade de CPF; RN11 exige início da vigência anterior ao fim; RN13/RN14/RN15/RN17 exigem vínculos válidos. A combinação apólice + número da parcela identifica a parcela dentro do contrato. As propostas de unicidade dos vínculos em Proposta, Apólice e Pagamento implementam H01, H02 e H03, respectivamente.

Uma cotação de outra companhia ou modalidade constitui outro registro. Seguradora e TipoSeguro se relacionam por intermédio de Cotação: o levantamento não sustenta limitar uma seguradora a um único tipo de seguro.

Sob H03, pagamento representa a liquidação da parcela: não há linha de pagamento vazia para representar pendência. A atualização da parcela para paga deve acompanhar o registro do pagamento; estornos, juros, descontos e pagamentos parciais exigem novas regras, ainda não levantadas. Nenhuma igualdade automática entre valor pago e valor da parcela foi afirmada.

Sob H06, Renovação documenta o processo referente à apólice de origem. Uma contratação renovada segue Cotação → Proposta → Apólice, preservando o contrato antigo. Um vínculo explícito entre a apólice antiga e a nova não está neste escopo e deve ser levantado se necessário.

## 6.5 Hipóteses para validação com a organização

Estas hipóteses tornam a proposta coerente, mas não constituem confirmação da entrevistada:

| Código | Decisão proposta | O que o grupo deve confirmar |
|---|---|---|
| H01 | Uma cotação gera zero ou uma proposta; cada proposta tem uma cotação. | Existem várias propostas/revisões para uma mesma cotação ou proposta sem cotação registrada? |
| H02 | Uma proposta gera zero ou uma apólice; cada apólice tem uma proposta. | Uma proposta pode gerar mais de uma apólice? |
| H03 | Uma parcela recebe zero ou um pagamento. | São aceitos pagamentos parciais, vários pagamentos, estornos ou ajustes? |
| H04 | A apólice pode existir antes do cadastro das parcelas (mínimo zero). | É obrigatório cadastrar pelo menos uma parcela já na inclusão da apólice? |
| H05 | Uma apólice pode ter zero ou vários sinistros. | Há limites ou restrições específicas que precisam ser modelados? |
| H06 | Uma apólice de origem pode possuir vários registros de processo/tentativa de renovação. | O controle registra tentativas, somente renovação concluída ou ciclos sucessivos? É necessário ligar a apólice antiga à nova? |

Também permanecem a confirmar: atendimento a pessoas jurídicas; formas de pagamento; valores de status; antecedência de alertas; dados necessários para uma agenda de visitas e atribuição de responsáveis.

---

# 7. Diagrama Entidade-Relacionamento (DER)

![DER revisado — Corretora de Seguros](DER-corretora.jpeg)

[Abrir imagem em tamanho original](DER-corretora.jpeg).

O diagrama usa entidades em caixas, atributos internos, relacionamentos nomeados e cardinalidades nas extremidades. ID identifica a entidade; REF identifica os vínculos descritos na seção 6. A quantidade junto a uma caixa indica quantas ocorrências **daquela entidade** podem se relacionar a uma ocorrência da entidade na outra ponta (convenção de multiplicidade UML). Não se usa aqui a posição das cardinalidades de participação da notação Chen.

O DER foi redesenhado a partir do dicionário fornecido pelo grupo: contém as mesmas 11 entidades, 45 atributos próprios e 10 referências. Foram retirados os campos adicionais sem sustentação no levantamento e corrigida a ligação de TipoSeguro para Cotação. O diagrama anterior permanece recuperável pelo histórico do GitHub. As hipóteses H01 a H06 estão explícitas; validação de campo não foi simulada.

---

# 8. Justificativa Técnica

## 8.1 Separação das etapas comerciais

Cotação, Proposta e Apólice possuem datas, situações e finalidades diferentes. Reuni-las em uma única entidade exigiria preencher dados contratuais mesmo quando o cliente não prossegue. O modelo preserva cotações sem proposta e propostas sem apólice. H01/H02 mantêm as associações máximas unitárias inicialmente propostas pelo grupo; se houver múltiplas revisões, os limites precisam ser alterados.

## 8.2 Identificação e escolha dos atributos

Cliente mantém CPF, nome e nascimento porque são os dados efetivamente informados. Identificadores internos dão identidade estável aos registros; CPF continua único por regra de negócio. Datas permitem acompanhar o ciclo operacional, valores descrevem as obrigações e status registram as etapas. Telefone, endereço, CNPJ e valores de indenização presentes na imagem anterior não foram mantidos como requisitos confirmados: precisam de levantamento adicional.

Seguradora e TipoSeguro são catálogos distintos: uma companhia não é uma modalidade. Cada cotação aponta para uma de cada. A prioridade comercial é representada em Seguradora, sem impedir o uso de outras companhias.

## 8.3 Relações, opcionalidade e integridade

Uma entidade de cadastro pode existir antes de uma operação, justificando `0..N` para cotações e atendimentos. Cada operação depende exatamente de um cadastro correspondente. A apólice pode existir sem sinistros ou renovações; exigir uma dessas ocorrências criaria registros artificiais. O mínimo zero de parcelas é uma decisão de cadastramento pendente de confirmação (H04), não uma afirmação de que um contrato não tem obrigação financeira.

O cliente da apólice é recuperado pela proposta e cotação de origem. Repetir esse vínculo na apólice permitiria indicar clientes conflitantes. Pelo mesmo motivo, Sinistro e Renovação chegam ao cliente pela apólice, atendendo ao histórico sem repetição de CPF.

## 8.4 Parcelas, pagamentos e renovação

Parcela representa a obrigação; Pagamento representa a ocorrência financeira. Separá-los permite manter vencimentos pendentes sem inventar pagamentos. O limite de um pagamento por parcela segue a proposta inicial e depende de H03. Se houver liquidações parciais, a relação passa a um-para-muitos e exigirá regras de saldo.

Renovação conserva contato, data de conclusão e status do processo da apólice de origem. Não se altera a vigência do contrato antigo para apagar o passado. O vínculo contratual entre apólices sucessivas será incluído somente após esclarecimento do processo (H06).

## 8.5 Escalabilidade e limites

Novas seguradoras, modalidades e ocorrências podem ser cadastradas sem criar uma entidade para cada produto. O modelo concentra o domínio da corretora; autenticação, perfis, backup, agenda completa de visitas e distribuição de tarefas exigem detalhamento posterior. Assim, os requisitos de segurança são registrados sem alegar que já estejam implementados neste DER.

---

# 9. Uso de Inteligência Artificial

## Ferramenta utilizada

**ChatGPT — OpenAI**

## Etapas em que foi utilizado

A ferramenta foi utilizada para:

- organização das informações da entrevista;
- estruturação do README;
- identificação preliminar de entidades;
- elaboração dos requisitos;
- organização das regras de negócio;
- elaboração do dicionário de dados;
- revisão da redação;
- organização da proposta de modelagem.

## Motivação

A IA foi utilizada como ferramenta de apoio para transformar as informações coletadas durante a pesquisa de campo em uma estrutura organizada de documentação e modelagem de banco de dados.

## Prompt utilizado

O grupo forneceu à ferramenta informações coletadas diretamente da corretora, incluindo:

> "CORRETORA DE SEGURO - QUE ATUA NO BRADESCO. Quais informações vocês cadastram de um cliente? CPF, Nome, Data de nascimento..."

Também foram fornecidas informações sobre os tipos de seguros, apólices, seguradoras, cotações, pagamentos, atendimentos, sinistros, renovações, quantidade de funcionários, clientes e faturamento.

Posteriormente, foi solicitado que essas informações fossem organizadas de acordo com os requisitos da atividade acadêmica.

## Resposta recebida

A IA organizou as informações em:

- caracterização da organização;
- processos de negócio;
- requisitos funcionais;
- requisitos não funcionais;
- regras de negócio;
- entidades;
- atributos;
- relacionamentos;
- cardinalidades;
- dicionário de dados;
- justificativa técnica.

## Fontes consultadas e verificadas

As informações específicas sobre a corretora foram obtidas por meio da **pesquisa de campo e entrevista realizada pelo grupo**.

As sugestões da IA foram comparadas com as informações fornecidas pela organização para evitar a inclusão de processos inexistentes.

## Trechos corrigidos ou rejeitados

Informações que não foram fornecidas pela organização não foram consideradas como fatos.

Alguns atributos sugeridos para o modelo, como identificadores internos e campos de status, representam decisões técnicas necessárias para estruturar o banco de dados e deverão ser validados durante as próximas etapas do projeto.

## Reflexão crítica

A IA foi utilizada apenas como ferramenta de apoio. O grupo reconhece que a ferramenta pode sugerir processos ou estruturas que não correspondam exatamente à realidade da organização.

Por esse motivo, a pesquisa de campo foi utilizada como principal referência para a definição dos processos, requisitos e regras de negócio.

---

## Justificativa da escolha final

A revisão utiliza o levantamento e o dicionário enviados pelo grupo como base comum. Essa escolha evita tratar os campos extras da primeira imagem como fatos confirmados. As cardinalidades máximas propostas originalmente foram preservadas, com mínimos e significados explicitados; a adoção definitiva depende da validação registrada na seção 6.5.

## Uso de IA na revisão e organização do repositório

| Item | Registro desta etapa |
|---|---|
| Ferramenta e etapa | ChatGPT/Codex — organização e publicação dos materiais fornecidos, comparação com o roteiro do professor, revisão de consistência, redesenho do DER e atualização do HTML/README. |
| Motivação | Adequar a documentação aos itens exigidos e resolver divergências entre a imagem, o dicionário e o texto. |
| Prompts utilizados | “este aqui e oq o professor pediu, ve se esta conforme”; “agora oque voce puder fazer com oq eu te dei, corrige e tente deixar conforme o q esta faltando”. |
| Resposta recebida | Auditoria das nove seções; apontamento de campos e vínculos divergentes; documentação revisada; DER padronizado; perguntas objetivas para validação de campo. |
| Fontes consultadas e verificadas | Roteiro 00-c_Esqueleto_Entrega_1.md.pdf, README e HTML enviados, imagem inicial do DER e três fotos. Os dois repositórios de referência foram consultados apenas para organização. A revisão comparou o texto dos requisitos com os artefatos; não houve nova entrevista nem confirmação externa dos dados da organização. |
| Trechos corrigidos | Cabeçalhos de tabelas e inclusão de Victor; substituição das fotos pendentes; remoção dos atributos extras do DER; TipoSeguro ligado a Cotação; padronização de nomes; explicitação das multiplicidades. A avaliação inicial tratou fluxogramas como pendência, mas o roteiro os declara opcionais, e isso foi corrigido. |
| Justificativa da escolha final | Usar as informações fornecidas como fonte comum, separar fatos e hipóteses e evitar acrescentar processos não levantados. O grupo ainda precisa avaliar a revisão e confirmar as hipóteses. |
| Reflexão crítica | Coerência entre arquivos não prova aderência à operação real. Os domínios sugeridos e as hipóteses de cardinalidade podem precisar mudar. A IA não confirma a razão social, as regras de pagamento nem a participação dos integrantes. |

Não foi informada a ferramenta utilizada para produzir a primeira imagem do DER. Se houve IA nessa etapa, o grupo deverá registrar ferramenta, prompt, resultado e revisão realizada.

## Pendências de validação pelo grupo

- Confirmar razão social/vínculo com a unidade visitada e completar cidade, UF e CEP; link público é complementar às fotos.
- Responder às hipóteses H01 a H06 e confirmar os domínios e limites do escopo.
- Comparar o HTML com 02-03g_Exemplo_Dicionario_Dados.pdf, citado no roteiro e ainda não fornecido.
- Registrar o uso de IA na imagem original, se aplicável, e a decisão do grupo sobre esta revisão.
- Realizar contribuições reais dos integrantes e a avaliação 360° conforme orientação da disciplina. O histórico de commits não foi alterado para simular autoria ou participação.
