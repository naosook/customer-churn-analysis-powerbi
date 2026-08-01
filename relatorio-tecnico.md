# Relatório Técnico: Dashboard de Churn e Comportamento do Cliente

## Introdução

Este relatório técnico documenta o desenvolvimento e a estrutura do **Dashboard de Churn e Comportamento do Cliente**, um painel analítico desenvolvido em Power BI utilizando o dataset público **Telco Customer Churn**, disponibilizado originalmente pela IBM e distribuído através do Kaggle.

O objetivo deste documento é registrar o contexto de negócio, a origem dos dados, o processo de preparação, a modelagem utilizada, os indicadores desenvolvidos e os principais insights obtidos durante a análise, servindo como documentação técnica do projeto para fins de portfólio.

## Objetivo do Projeto

Desenvolver um dashboard interativo em Power BI para análise de churn (cancelamento) de clientes de uma empresa de telecomunicações, permitindo identificar padrões relacionados ao comportamento dos clientes, características contratuais, aspectos financeiros e fatores associados ao cancelamento de serviços.

## Contexto de Negócio

O setor de telecomunicações apresenta alta competitividade e custos significativos relacionados à aquisição de novos clientes. Nesse cenário, a retenção da base existente representa uma estratégia importante para manutenção da receita recorrente.

A análise de churn permite compreender quais características estão relacionadas ao cancelamento de clientes, possibilitando a criação de estratégias de retenção mais direcionadas e baseadas em dados.

## Problema de Negócio

A empresa fictícia representada pelo dataset apresenta uma taxa de churn de **26,54%** da base de clientes.

O problema de negócio analisado neste projeto é:

**Como identificar os principais fatores associados ao cancelamento de clientes e transformar esses dados em informações visuais que auxiliem na tomada de decisão para ações de retenção?**

# Dataset

- **Origem:** Kaggle, Telco Customer Churn. Dados originalmente disponibilizados pela IBM.
- **Quantidade de registros:** 7.043 clientes.
- **Quantidade de atributos:** 21 colunas.
- **Variável alvo:** `Churn` (Yes/No), indicando se o cliente cancelou o serviço.

Principais atributos utilizados:

- **Identificação:** `customerID`
- **Dados demográficos:** `gender`, `SeniorCitizen`, `Partner`, `Dependents`
- **Relacionamento com a empresa:** `tenure`
- **Serviços contratados:** `PhoneService`, `MultipleLines`, `InternetService`, `OnlineSecurity`, `OnlineBackup`, `DeviceProtection`, `TechSupport`, `StreamingTV`, `StreamingMovies`
- **Contrato e pagamento:** `Contract`, `PaperlessBilling`, `PaymentMethod`
- **Dados financeiros:** `MonthlyCharges`, `TotalCharges`

Cada linha representa um cliente individual contendo informações sobre perfil, serviços utilizados, contrato, valores financeiros e status de cancelamento.

# Processo de ETL

O processo de ETL foi realizado utilizando o **Power Query dentro do Power BI**, envolvendo a importação, preparação e transformação dos dados antes da criação das visualizações.

## Extração

Os dados foram importados a partir do arquivo CSV disponibilizado pelo Kaggle, contendo informações históricas dos clientes da empresa de telecomunicações.

## Transformação

Durante a preparação dos dados foram realizadas etapas de organização e padronização para adequação da análise:

- Verificação da estrutura das colunas.
- Ajuste dos tipos de dados.
- Organização dos campos utilizados nas análises.
- Padronização de categorias para facilitar a interpretação dos gráficos.
- Tradução de valores categóricos do inglês para português.

Entre as padronizações realizadas estão:

- Tipo de contrato.
- Forma de pagamento.
- Gênero.
- Status de cancelamento.

Também foi criada uma classificação baseada no tempo de relacionamento do cliente (`tenure`), agrupando os clientes nas seguintes faixas:

- 0 a 6 meses.
- 7 a 12 meses.
- 13 a 24 meses.
- 25 meses ou mais.

Essa transformação permitiu analisar o comportamento do churn ao longo do ciclo de vida do cliente.

## Carga

Após o tratamento dos dados, a base foi utilizada dentro do Power BI para criação das medidas, indicadores e visualizações do dashboard.

# Modelagem dos Dados

A modelagem desenvolvida no Power BI utiliza uma abordagem de **tabela única**, baseada diretamente no dataset original.

Essa estrutura foi adequada para o objetivo do projeto, pois a base já apresenta todas as informações necessárias para análise exploratória e construção dos indicadores de churn.

A tabela utilizada contém:

- **Identificação do cliente:** `customerID`
- **Características demográficas:** `gender`, `SeniorCitizen`, `Partner`, `Dependents`
- **Tempo de relacionamento:** `tenure`
- **Serviços contratados:** `PhoneService`, `InternetService`, `OnlineSecurity`, `OnlineBackup`, `DeviceProtection`, `TechSupport`, `StreamingTV`, `StreamingMovies`
- **Informações contratuais:** `Contract`, `PaperlessBilling`, `PaymentMethod`
- **Indicadores financeiros:** `MonthlyCharges`, `TotalCharges`
- **Variável analisada:** `Churn`

Durante o desenvolvimento do dashboard, foi utilizada uma classificação derivada da coluna `tenure`, agrupando os clientes em faixas de tempo de relacionamento:

- 0 a 6 meses.
- 7 a 12 meses.
- 13 a 24 meses.
- 25 meses ou mais.

Essa categorização permitiu uma análise mais clara do comportamento de cancelamento ao longo do ciclo de vida do cliente.

Para este projeto, a utilização de uma tabela única atende ao objetivo analítico proposto, considerando que a base possui uma estrutura consolidada e o foco principal é a análise exploratória e visualização de indicadores de negócio.

Em ambientes corporativos com múltiplas fontes de dados, maior volume e necessidade de análises históricas, uma evolução possível seria a implementação de um modelo dimensional (**Star Schema**), utilizando tabelas fato e dimensões para melhorar escalabilidade, organização e manutenção do modelo.

# KPIs

Os principais indicadores desenvolvidos no dashboard são exibidos no cabeçalho das páginas para fornecer uma visão geral da base analisada.

## Clientes Totais (7.043)

**Definição:** quantidade total de clientes analisados na base de dados.

**Objetivo:** apresentar o tamanho da carteira de clientes avaliada.

**Interpretação:** representa todos os registros disponíveis no dataset utilizado no projeto.

**Importância para o negócio:** fornece o contexto necessário para interpretação dos demais indicadores, como churn e retenção.

## Taxa de Churn (26,54%)

**Definição:** percentual de clientes que cancelaram o serviço em relação ao total da base.

**Objetivo:** medir o nível de cancelamento existente na carteira de clientes.

**Interpretação:** aproximadamente um quarto dos clientes analisados deixou de utilizar os serviços da empresa.

**Importância para o negócio:** representa o principal indicador do problema analisado, auxiliando na identificação de oportunidades de retenção.

## Taxa de Retenção (73,46%)

**Definição:** percentual de clientes que permaneceram ativos na base.

**Objetivo:** apresentar a parcela de clientes mantidos pela empresa.

**Interpretação:** representa os clientes que continuam utilizando os serviços em comparação ao total analisado.

**Importância para o negócio:** permite acompanhar o equilíbrio entre retenção e perda de clientes.

## Ticket Médio (R$ 3,52 Mil)

**Definição:** valor médio financeiro associado aos clientes analisados.

**Objetivo:** relacionar a análise de churn ao impacto financeiro da perda de clientes.

**Interpretação:** permite compreender o valor médio associado à carteira de clientes analisada.

**Importância para o negócio:** conecta a análise comportamental dos clientes com uma perspectiva financeira, auxiliando na avaliação do impacto causado pelo cancelamento.

# Dashboard

O relatório é composto por quatro páginas analíticas, desenvolvidas com objetivos específicos para facilitar a interpretação dos padrões de churn e do comportamento dos clientes.

A descrição detalhada de cada página, incluindo objetivos, indicadores, gráficos, filtros e interpretações, está documentada em [`DASHBOARD.md`](DASHBOARD.md).

## Página 1: Churn

![Página 1: Churn](imagens/pagina-1.jpeg)

Esta página apresenta uma visão geral do comportamento de cancelamento dos clientes, analisando principalmente a relação entre tempo de relacionamento e taxa de churn.

Principais análises:

- Churn por faixa de permanência (`tenure`).
- Identificação dos períodos com maior concentração de cancelamentos.
- Análise do comportamento do cliente ao longo do ciclo de relacionamento.

## Página 2: Impacto

![Página 2: Impacto](imagens/pagina-2.jpeg)

Esta página analisa fatores relacionados aos serviços contratados e sua relação com o cancelamento dos clientes.

Principais análises:

- Relação entre serviços adicionais e taxa de churn.
- Comparação do comportamento dos clientes conforme características dos serviços utilizados.
- Identificação de fatores associados à retenção ou perda de clientes.

## Página 3: Financeiro

![Página 3: Financeiro](imagens/pagina-3.jpeg)

Esta página apresenta uma análise dos aspectos financeiros e contratuais relacionados ao comportamento dos clientes, buscando compreender como características de pagamento e serviços influenciam o cancelamento.

Principais análises:

- Distribuição dos clientes por forma de pagamento.
- Relação entre tipo de contrato e taxa de churn.
- Comparação dos indicadores financeiros da base analisada.
- Avaliação do impacto financeiro relacionado ao comportamento dos clientes.

## Página 4: Perfil

![Página 4: Perfil](imagens/pagina-4.jpeg)

Esta página apresenta uma segmentação do perfil dos clientes, permitindo analisar diferenças entre grupos da base.

Principais análises:

- Distribuição dos clientes por características demográficas.
- Comparação entre tipos de contrato.
- Análise do comportamento de churn entre diferentes segmentos de clientes.

# Principais Insights

A análise realizada através do dashboard identificou os seguintes padrões relacionados ao comportamento dos clientes:

- Clientes nos primeiros meses de relacionamento apresentam maior concentração de cancelamentos, indicando maior risco durante o início do ciclo de vida.

- Contratos mensais apresentam maior taxa de churn quando comparados a contratos de maior duração, indicando uma relação entre fidelização contratual e retenção.

- Clientes com contratos de maior duração apresentam maior permanência na base, demonstrando maior estabilidade no relacionamento com a empresa.

- Características relacionadas aos serviços contratados apresentam diferenças no comportamento de cancelamento, permitindo identificar grupos com maior ou menor risco de churn.

- A análise financeira permite relacionar o comportamento dos clientes ao impacto econômico causado pela perda de receita associada aos cancelamentos.

# Conclusão

O Dashboard de Churn e Comportamento do Cliente apresenta uma análise completa dos principais fatores associados ao cancelamento de clientes em uma empresa de telecomunicações.

O projeto demonstra a aplicação prática de conceitos de análise de dados utilizando Power BI, incluindo preparação de dados, transformação de informações, criação de indicadores, modelagem, construção de visualizações e interpretação de resultados de negócio.

A organização do dashboard em quatro perspectivas, Churn, Impacto, Financeiro e Perfil, permite uma análise progressiva do problema, começando pela identificação dos padrões de cancelamento, passando pela análise dos fatores associados ao comportamento dos clientes e chegando à compreensão do impacto financeiro envolvido.

Este projeto evidencia a capacidade de transformar dados brutos em informações estratégicas para apoio à tomada de decisão, utilizando ferramentas de Business Intelligence e boas práticas de comunicação visual de dados.
