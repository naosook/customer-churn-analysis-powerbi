# Dashboard de Churn e Comportamento do Cliente

Análise de risco de cancelamento (churn) de clientes de uma empresa de telecomunicações, desenvolvida em Power BI utilizando o dataset público **Telco Customer Churn**, originalmente disponibilizado pela IBM através do Kaggle.

**Dashboard publicado no Power BI:**  
[Acessar dashboard](https://app.powerbi.com/view?r=eyJrIjoiNDI1NWEwNTUtYjUxZC00MDVjLWJmMTktMDkwNWQ5MGI1YmYzIiwidCI6IjdlMjU2YWE5LTRhMjAtNGY1MS05YTQxLWRjNTM4ZTlmMzQ3OCJ9&pageName=ReportSection&autoAuth=true&ctid=7e256aa9-4a20-4f51-9a41-dc538e9f3478&filterPaneEnabled=false&navContentPaneEnabled=false)

![Dashboard](imagens/pagina-1.jpeg)

---

## Descrição

Este projeto apresenta um dashboard interativo desenvolvido em Power BI para análise de **churn (cancelamento de clientes)** em uma empresa de telecomunicações.

O painel foi estruturado em quatro páginas analíticas:

* **Churn:** análise dos padrões de cancelamento considerando o tempo de relacionamento dos clientes.
* **Impacto:** análise dos fatores relacionados aos serviços contratados e comportamento de retenção.
* **Financeiro:** análise da relação entre características contratuais, pagamentos e impacto financeiro.
* **Perfil:** segmentação dos clientes por características demográficas e contratuais.

O objetivo do projeto é transformar dados brutos em informações estratégicas, permitindo identificar padrões associados ao cancelamento e apoiar decisões relacionadas à retenção de clientes.

---

## Objetivo

Desenvolver um dashboard analítico em Power BI capaz de identificar padrões relacionados ao cancelamento de clientes e responder perguntas de negócio como:

* Em qual momento do ciclo de vida do cliente o risco de churn é maior?
* Quais características contratuais apresentam relação com maior retenção?
* Quais serviços contratados apresentam diferenças no comportamento dos clientes?
* Qual o impacto financeiro associado ao cancelamento?
* Quais perfis de clientes apresentam maior concentração de churn?

---

## Contexto de Negócio

Empresas de telecomunicações atuam em um mercado altamente competitivo, no qual a retenção de clientes possui grande importância estratégica.

A perda de clientes impacta diretamente a receita recorrente e aumenta os custos relacionados à aquisição de novos consumidores.

A análise de churn permite identificar padrões de comportamento e oportunidades de melhoria, auxiliando empresas no desenvolvimento de estratégias de retenção mais eficientes.

---

## Problema de Negócio

A empresa fictícia representada pelo dataset apresenta uma taxa de churn de **26,54%** da base analisada.

O problema de negócio analisado neste projeto é:

**Como identificar os principais fatores associados ao cancelamento de clientes e transformar esses dados em informações visuais que auxiliem na tomada de decisão para estratégias de retenção?**

---

## Dataset Utilizado

* **Nome:** Telco Customer Churn
* **Fonte:** Kaggle
* **Origem dos dados:** IBM Sample Data Sets
* **Quantidade de registros:** 7.043 clientes
* **Quantidade de atributos:** 21 colunas
* **Variável alvo:** `Churn`

Principais atributos utilizados:

* **Identificação do cliente:** `customerID`
* **Dados demográficos:** `gender`, `SeniorCitizen`, `Partner`, `Dependents`
* **Tempo de relacionamento:** `tenure`
* **Serviços contratados:** `PhoneService`, `MultipleLines`, `InternetService`, `OnlineSecurity`, `OnlineBackup`, `DeviceProtection`, `TechSupport`, `StreamingTV`, `StreamingMovies`
* **Informações contratuais:** `Contract`, `PaperlessBilling`, `PaymentMethod`
* **Indicadores financeiros:** `MonthlyCharges`, `TotalCharges`

Cada registro representa um cliente individual contendo informações sobre perfil, serviços utilizados, contrato, valores financeiros e status de cancelamento.

---

## Tecnologias Utilizadas

* **Power BI:** desenvolvimento do dashboard, criação das visualizações e análise dos indicadores.
* **Power Query (M):** preparação e transformação dos dados dentro do ambiente Power BI.
* **DAX:** criação de medidas, cálculos analíticos e indicadores.
* **Markdown:** documentação técnica do projeto.
* **GitHub:** versionamento e publicação do projeto.

---

## Ferramentas Utilizadas

* Power BI Desktop
* Power BI Service
* Power Query
* Kaggle
* GitHub

## Processo de Preparação dos Dados

A preparação dos dados foi realizada dentro do ambiente Power BI, utilizando etapas de organização e transformação da base antes da construção das visualizações.

Foram realizadas etapas como:

* Importação do dataset original em formato CSV.
* Verificação da estrutura dos dados.
* Ajuste dos tipos de dados.
* Padronização das categorias utilizadas nas análises.
* Tradução de valores categóricos originalmente em inglês para português.
* Criação de uma classificação de tempo de relacionamento baseada na coluna `tenure`.

Entre as transformações realizadas estão:

* Padronização do tipo de contrato.
* Padronização das formas de pagamento.
* Padronização do status de cancelamento.
* Organização dos campos utilizados nos gráficos e indicadores.

Também foi criada uma categorização do tempo de relacionamento dos clientes:

* 0 a 6 meses.
* 7 a 12 meses.
* 13 a 24 meses.
* 25 meses ou mais.

Essa transformação permitiu analisar o comportamento do churn considerando diferentes fases do ciclo de relacionamento do cliente.

---

## Modelagem dos Dados

A estrutura de dados utilizada no projeto segue uma abordagem baseada em **tabela única**, utilizando o dataset original como fonte principal das análises.

Essa estrutura foi adequada ao objetivo do projeto, que consiste na análise exploratória do comportamento dos clientes e identificação de padrões relacionados ao churn.

A base contém informações:

* Demográficas.
* Contratuais.
* Financeiras.
* Serviços utilizados.
* Status de cancelamento.

A tabela principal utilizada contém os seguintes grupos de informações:

* **Identificação do cliente:** `customerID`
* **Características demográficas:** `gender`, `SeniorCitizen`, `Partner`, `Dependents`
* **Tempo de relacionamento:** `tenure`
* **Serviços contratados:** `PhoneService`, `InternetService`, `OnlineSecurity`, `OnlineBackup`, `DeviceProtection`, `TechSupport`, `StreamingTV`, `StreamingMovies`
* **Informações contratuais:** `Contract`, `PaperlessBilling`, `PaymentMethod`
* **Indicadores financeiros:** `MonthlyCharges`, `TotalCharges`
* **Variável analisada:** `Churn`

Também foi utilizada uma classificação derivada da coluna `tenure` para agrupar clientes por tempo de relacionamento, facilitando a análise dos padrões de cancelamento.

A validação completa da estrutura interna do modelo, como possíveis tabelas auxiliares, relacionamentos ou medidas específicas, depende do arquivo original do Power BI (`.pbix`).

Para este projeto, a estrutura baseada em tabela única atende ao objetivo analítico proposto. Em ambientes corporativos com múltiplas fontes de dados e maior necessidade de escalabilidade, uma evolução possível seria a implementação de um modelo dimensional utilizando **Star Schema**.

---

## Estrutura do Dashboard

O relatório é composto por quatro páginas analíticas, desenvolvidas para apresentar diferentes perspectivas sobre o comportamento dos clientes.

| Página | Foco |
|---|---|
| **Churn** | Padrões de cancelamento considerando tempo de contrato e comportamento ao longo da jornada do cliente |
| **Impacto** | Relação entre serviços contratados e comportamento de retenção |
| **Financeiro** | Relação entre contrato, pagamento, receita e churn |
| **Perfil** | Segmentação dos clientes por características demográficas e contratuais |

---

## Prévia das páginas

| Página 1: Churn | Página 2: Impacto |
|---|---|
| ![Página 1 - Churn](imagens/pagina-1.jpeg) | ![Página 2 - Impacto](imagens/pagina-2.jpeg) |

| Página 3: Financeiro | Página 4: Perfil |
|---|---|
| ![Página 3 - Financeiro](imagens/pagina-3.jpeg) | ![Página 4 - Perfil](imagens/pagina-4.jpeg) |

Detalhamento completo das páginas disponível em [`dashboard.md`](dashboard.md).

---

## Principais KPIs

Os principais indicadores desenvolvidos no dashboard são apresentados no cabeçalho de todas as páginas:

| KPI | Valor |
|---|---|
| Clientes Totais | 7.043 |
| Taxa de Churn | 26,54% |
| Taxa de Retenção | 73,46% |
| Ticket Médio | R$ 3,52 Mil |

Esses indicadores permitem uma visão inicial da dimensão da base analisada e do impacto do cancelamento de clientes.

---

## Principais Visualizações

O dashboard apresenta diferentes tipos de visualizações para facilitar a interpretação dos dados:

* Gráfico de área/linha: análise do churn por faixa de tempo de contrato.
* Gráfico de linha: evolução do churn ao longo do tempo de relacionamento.
* Gráfico de barras horizontais: comparação entre cancelamento e contratação de serviços adicionais.
* Gráfico de barras agrupadas: relação entre tempo de contrato e cancelamento.
* Gráfico de barras horizontais: distribuição por formas de pagamento.
* Gráfico de barras: comparação de receita por tipo de internet.
* Gráfico de pizza: distribuição dos clientes por tipo de contrato.
* Gráfico de rosca: distribuição dos clientes por gênero.

## Principais Insights

A análise realizada através do dashboard identificou os seguintes padrões relacionados ao comportamento dos clientes:

* Clientes nos primeiros meses de contrato apresentam maior concentração de churn, indicando maior risco durante o início do relacionamento.

* Aproximadamente 70% dos cancelamentos estão concentrados nos primeiros 12 meses de relacionamento, conforme observado nas análises do dashboard.

* Clientes com serviço de backup online apresentam diferença no comportamento de cancelamento quando comparados aos clientes sem esse serviço.

* Contratos mensais apresentam maior concentração de churn em comparação aos contratos de maior duração, indicando uma relação entre fidelização contratual e retenção.

* Clientes com contratos de maior duração apresentam maior estabilidade no relacionamento com a empresa.

* A análise financeira permite compreender a relação entre comportamento dos clientes e o impacto causado pelos cancelamentos na receita.

---

## Como Visualizar o Dashboard

O dashboard está publicado no Power BI Service e pode ser acessado diretamente pelo navegador:

[Abrir Dashboard de Churn e Comportamento do Cliente](https://app.powerbi.com/view?r=eyJrIjoiNDI1NWEwNTUtYjUxZC00MDVjLWJmMTktMDkwNWQ5MGI1YmYzIiwidCI6IjdlMjU2YWE5LTRhMjAtNGY1MS05YTQxLWRjNTM4ZTlmMzQ3OCJ9&pageName=ReportSection&autoAuth=true&ctid=7e256aa9-4a20-4f51-9a41-dc538e9f3478&filterPaneEnabled=false&navContentPaneEnabled=false)

As imagens estáticas das páginas também estão disponíveis na pasta [`imagens/`](imagens/).

---

## Aprendizados Obtidos

Durante o desenvolvimento deste projeto, foram aplicados conceitos de análise de dados e Business Intelligence, incluindo:

* Desenvolvimento de dashboards analíticos utilizando Power BI.
* Preparação e transformação de dados utilizando Power Query.
* Criação de medidas e indicadores utilizando DAX.
* Estruturação de uma narrativa de dados através de visualizações.
* Análise de comportamento de clientes utilizando indicadores de churn.
* Comunicação de insights de negócio através de dashboards interativos.

---

## Conclusão

O Dashboard de Churn e Comportamento do Cliente apresenta uma análise dos principais fatores relacionados ao cancelamento de clientes em uma empresa de telecomunicações.

A construção do projeto envolveu desde a preparação dos dados até a criação de indicadores, visualizações e análises de negócio utilizando Power BI.

A organização do dashboard em quatro perspectivas, Churn, Impacto, Financeiro e Perfil, permite uma leitura progressiva do problema analisado, iniciando pela identificação dos padrões de cancelamento, passando pelos fatores associados ao comportamento dos clientes e chegando aos impactos financeiros envolvidos.

O projeto demonstra a aplicação prática de ferramentas de Business Intelligence para transformar dados brutos em informações estratégicas que podem apoiar processos de tomada de decisão.

---

## Autor

**Amanda Brandão Sousa**

Analista de Dados Júnior | Power BI | SQL | Python | Business Intelligence

---

## Contato

* LinkedIn: https://www.linkedin.com/in/amanda-brand%C3%A3o-sousa/
* E-mail: amandabrandaoday@gmail.com
* GitHub: https://github.com/naosook
