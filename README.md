# PROJETO DE MODELAGEM DE BANCO DE DADOS

## Corretora de Seguros — Bradesco

> **Entrega 1 — Modelo Conceitual (DER)** · Versão inicial em atualização.

[Dicionário de dados em HTML](dicionario_de_dados.html) · [Diagrama Entidade-Relacionamento](DER-corretora.jpeg)

### Metadados

| Integrante | RGM |
| --------------------------- | -------- |
| Mateus Martins Gonçalves    | 47812222 |
| Raul Borges Sim             | 48247634 |
| João Gustavo Bento de Souza | 42283671 |
| Victor Alves Rodrigues Braulino | 48216305 |

---

# 1. Caracterização da Organização

## 1.1 Nome e natureza da organização

A organização escolhida para o desenvolvimento deste projeto é uma **corretora de seguros que atua junto ao Bradesco**, identificada durante a visita como **Bradesco**.

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

# 1.5 Evidências da organização e da pesquisa de campo

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

> **Observação:** o endereço, e-mail e identificação da organização acima foram utilizados conforme as informações fornecidas pelo grupo. O link do Google Maps/site/rede social deverá ser acrescentado caso o grupo possua esse material.

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

| Código | Regra |
| ----------- | --------------------------------------------------------------------------------------------- |
| RN01        | Cada cliente deve possuir CPF, nome e data de nascimento cadastrados.                         |
| RN02        | O CPF deve identificar unicamente um cliente.                                                 |
| RN03        | A corretora trabalha com diferentes tipos de seguros.                                         |
| RN04        | Uma cotação deve estar associada a um cliente.                                                |
| RN05        | Uma cotação deve estar associada a uma seguradora.                                            |
| RN06        | A Bradesco Seguros é priorizada nas cotações, conforme informação fornecida pela organização. |
| RN07        | Outras seguradoras podem ser consultadas quando necessário.                                   |
| RN08        | Uma proposta pode ser originada a partir de uma cotação.                                      |
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

# 5. Dicionário de Dados Conceitual

O dicionário também está disponível no arquivo [dicionario_de_dados.html](dicionario_de_dados.html), no formato solicitado pelo professor. Para visualizar a página formatada, baixe o arquivo HTML e abra-o no navegador.

## Cliente

| Atributo | Descrição | Regra de negócio |
| --------------------------------- | -------------------------------- | ------------------- |
| id\_cliente                       | Identificador interno do cliente | Único e obrigatório |
| cpf                               | CPF do cliente                   | Obrigatório e único |
| nome                              | Nome do cliente                  | Obrigatório         |
| data\_nascimento                  | Data de nascimento               | Obrigatória         |

## Seguradora

| Atributo | Descrição | Regra de negócio |
| --------------------------------- | --------------------------- | ---------------------------------- |
| id\_seguradora                    | Identificador da seguradora | Único                              |
| nome                              | Nome da seguradora          | Obrigatório                        |
| prioridade                        | Indica prioridade comercial | Pode indicar seguradora priorizada |

## TipoSeguro

| Atributo | Descrição | Regra de negócio |
| --------------------------------- | --------------------- | ----------- |
| id\_tipo\_seguro                  | Identificador do tipo | Único       |
| nome                              | Nome do seguro        | Obrigatório |
| descricao                         | Descrição do produto  | Opcional    |

## Cotação

| Atributo | Descrição | Regra de negócio |
| --------------------------------- | ------------------------ | ------------------------------ |
| id\_cotacao                       | Identificador da cotação | Único                          |
| data\_cotacao                     | Data da cotação          | Obrigatória                    |
| valor\_cotado                     | Valor apresentado        | Valor não negativo             |
| status                            | Situação da cotação      | Deve possuir valores definidos |
| id\_cliente                       | Cliente relacionado      | Obrigatório                    |
| id\_seguradora                    | Seguradora consultada    | Obrigatório                    |
| id\_tipo\_seguro                  | Tipo de seguro           | Obrigatório                    |

## Proposta

| Atributo | Descrição | Regra de negócio |
| --------------------------------- | ------------------------- | ------------------------------ |
| id\_proposta                      | Identificador da proposta | Único                          |
| data\_proposta                    | Data da proposta          | Obrigatória                    |
| status                            | Situação da proposta      | Deve possuir valores definidos |
| valor\_proposta                   | Valor da proposta         | Não negativo                   |
| id\_cotacao                       | Cotação de origem         | Deve existir                   |

## Apólice

| Atributo | Descrição | Regra de negócio |
| --------------------------------- | --------------------- | ------------------------------ |
| id\_apolice                       | Identificador interno | Único                          |
| numero\_apolice                   | Número da apólice     | Obrigatório                    |
| inicio\_vigencia                  | Início da vigência    | Obrigatório                    |
| fim\_vigencia                     | Fim da vigência       | Obrigatório                    |
| status                            | Situação da apólice   | Deve possuir valores definidos |
| id\_proposta                      | Proposta de origem    | Deve existir                   |

## Parcela

| Atributo | Descrição | Regra de negócio |
| --------------------------------- | ------------------------ | -------------- |
| id\_parcela                       | Identificador da parcela | Único          |
| numero\_parcela                   | Número da parcela        | Obrigatório    |
| valor                             | Valor da parcela         | Maior que zero |
| data\_vencimento                  | Data de vencimento       | Obrigatória    |
| status                            | Situação da parcela      | Obrigatório    |
| id\_apolice                       | Apólice relacionada      | Obrigatório    |

## Pagamento

| Atributo | Descrição | Regra de negócio |
| --------------------------------- | -------------------------- | ------------------------------ |
| id\_pagamento                     | Identificador do pagamento | Único                          |
| data\_pagamento                   | Data do pagamento          | Obrigatória quando pago        |
| valor\_pago                       | Valor pago                 | Maior que zero                 |
| forma\_pagamento                  | Forma utilizada            | Deve possuir valores definidos |
| id\_parcela                       | Parcela relacionada        | Obrigatório                    |

## Atendimento

| Atributo | Descrição | Regra de negócio |
| --------------------------------- | -------------------------- | ----------- |
| id\_atendimento                   | Identificador              | Único       |
| data\_atendimento                 | Data do atendimento        | Obrigatória |
| tipo\_atendimento                 | Tipo do atendimento        | Obrigatório |
| descricao                         | Informações do atendimento | Opcional    |
| id\_cliente                       | Cliente atendido           | Obrigatório |

## Sinistro

| Atributo | Descrição | Regra de negócio |
| --------------------------------- | ----------------------- | ------------------------------------- |
| id\_sinistro                      | Identificador           | Único                                 |
| numero\_sinistro                  | Número do sinistro      | Quando fornecido, deve ser registrado |
| data\_sinistro                    | Data da ocorrência      | Obrigatória                           |
| descricao                         | Descrição da ocorrência | Obrigatória                           |
| status                            | Situação do sinistro    | Deve possuir valores definidos        |
| id\_apolice                       | Apólice relacionada     | Obrigatório                           |

## Renovação

| Atributo | Descrição | Regra de negócio |
| --------------------------------- | --------------------------- | -------------------------------- |
| id\_renovacao                     | Identificador               | Único                            |
| data\_contato                     | Data do contato com cliente | Registrada quando houver contato |
| data\_renovacao                   | Data da renovação           | Obrigatória quando concluída     |
| status                            | Situação da renovação       | Deve possuir valores definidos   |
| id\_apolice                       | Apólice renovada            | Obrigatório                      |

---

# 6. Modelagem Conceitual

## 6.1 Entidades

Foram identificadas as seguintes entidades:

**Cliente** — representa os clientes da corretora.

**Seguradora** — representa as companhias utilizadas nas cotações.

**TipoSeguro** — representa as modalidades de seguros comercializadas.

**Cotação** — representa uma cotação realizada para determinado cliente.

**Proposta** — representa uma cotação que avançou para uma etapa de contratação.

**Apólice** — representa o seguro contratado.

**Parcela** — representa os valores que devem ser pagos relacionados à apólice.

**Pagamento** — representa o pagamento de uma parcela.

**Atendimento** — representa o contato ou atendimento realizado pela corretora ao cliente.

**Sinistro** — representa uma ocorrência relacionada a uma apólice.

**Renovação** — representa o processo de renovação de uma apólice.

---

# 7. Diagrama Entidade-Relacionamento

![DER — Corretora de Seguros (Bradesco)](DER-corretora.jpeg)

[Baixar ou visualizar a imagem do DER](DER-corretora.jpeg).

> **Revisão pendente:** a imagem recebida possui atributos adicionais e nomes diferentes dos registrados no dicionário, além de representar Seguradora — TipoSeguro onde o texto propõe TipoSeguro — Cotação. Os materiais foram mantidos nesta versão inicial e deverão ser conciliados pelo grupo antes da entrega definitiva.

Resumo das relações propostas no levantamento:

```
CLIENTE
   │
   │ 1:N
   ▼
COTAÇÃO ───── N:1 ───── SEGURADORA
   │
   │ N:1
   ▼
TIPO_SEGURO

COTAÇÃO
   │
   │ 1:0..1
   ▼
PROPOSTA
   │
   │ 1:0..1
   ▼
APÓLICE
   │
   ├────────────── 1:N ──────────────► PARCELA
   │                                      │
   │                                      │ 1:0..1
   │                                      ▼
   │                                  PAGAMENTO
   │
   ├────────────── 1:N ──────────────► SINISTRO
   │
   └────────────── 1:N ──────────────► RENOVAÇÃO

CLIENTE
   │
   │ 1:N
   ▼
ATENDIMENTO

```

### Cardinalidades propostas

| Relacionamento | Cardinalidade |
| --------------------------- | ------ |
| Cliente — Cotação           | 1:N   |
| Seguradora — Cotação        | 1:N   |
| TipoSeguro — Cotação        | 1:N   |
| Cotação — Proposta          | 1:0..1 |
| Proposta — Apólice          | 1:0..1 |
| Apólice — Parcela           | 1:N   |
| Parcela — Pagamento         | 1:0..1 |
| Cliente — Atendimento       | 1:N   |
| Apólice — Sinistro          | 1:N   |
| Apólice — Renovação         | 1:N   |

### Observação importante sobre as cardinalidades

As cardinalidades acima são uma **proposta de modelagem baseada nas informações fornecidas pela organização**. Antes da entrega definitiva, o grupo deve confirmar com a responsável entrevistada, Patrícia dos Santos Souza, se essas relações representam corretamente o funcionamento real da corretora.

Essa validação é especialmente importante para:

- quantidade de propostas originadas de uma cotação;
- quantidade de apólices vinculadas a uma proposta;
- quantidade de pagamentos por parcela;
- possibilidade de uma apólice possuir mais de um sinistro;
- quantidade de renovações que podem ser registradas para uma mesma apólice.

---

# 8. Justificativa Técnica

A modelagem foi elaborada considerando os processos efetivamente identificados durante a pesquisa de campo.

A entidade **Cliente** foi definida como uma das entidades centrais porque todas as atividades de atendimento e contratação estão relacionadas aos clientes da corretora.

**Cotação**, **Proposta** e **Apólice** foram separadas para representar diferentes etapas do processo comercial. Essa separação evita considerar que toda cotação necessariamente resulta em contratação.

A entidade **Seguradora** foi separada de **TipoSeguro** porque uma seguradora representa a companhia responsável pelo produto, enquanto o tipo de seguro representa a modalidade contratada.

A entidade **Parcela** foi separada de **Apólice** porque uma única apólice pode possuir diversas parcelas. Da mesma maneira, **Pagamento** foi separado para permitir registrar a situação financeira de cada parcela.

A entidade **Atendimento** representa o histórico de contatos realizados com o cliente, substituindo conceitualmente o controle atualmente realizado por planilhas e registros manuais.

A entidade **Sinistro** foi incluída porque o processo de acompanhamento de sinistros é uma atividade existente na organização e possui uma funcionária especializada.

A entidade **Renovação** foi incluída devido à importância do acompanhamento dos vencimentos das apólices. Sua existência permite registrar o processo de renovação sem apagar o histórico anterior.

A estrutura também foi pensada para permitir crescimento futuro. Novas seguradoras e modalidades de seguros podem ser adicionadas sem modificar as entidades principais.

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
