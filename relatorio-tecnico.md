# Relatório Técnico: Dashboard de Churn e Comportamento do Cliente

## Introdução

Este relatório técnico documenta o desenvolvimento e a estrutura do **Dashboard de Churn e Comportamento do Cliente**, um painel analítico construído em Power BI a partir do dataset público **Telco Customer Churn**, disponibilizado pela IBM através do Kaggle. O documento tem como objetivo registrar, de forma completa e tecnicamente rigorosa, o contexto de negócio, os dados utilizados, a estrutura do dashboard e os insights obtidos, servindo como referência técnica para o repositório de portfólio.

## Objetivo do Projeto

Consolidar, em um único painel visual publicado no Power BI, a análise de churn (cancelamento) de clientes de uma empresa de telecomunicações, permitindo a identificação de padrões temporais, contratuais, financeiros e demográficos associados ao cancelamento de serviços.

## Contexto de Negócio

O setor de telecomunicações é caracterizado por alta concorrência e por custos elevados de aquisição de clientes. Nesse cenário, a retenção de clientes existentes é, tipicamente, mais eficiente do ponto de vista financeiro do que a aquisição de novos clientes. Monitorar a taxa de churn e entender seus fatores associados é, portanto, uma prática essencial de gestão para empresas desse setor, com impacto direto sobre receita recorrente e rentabilidade.

## Problema de Negócio

A empresa fictícia representada pelo dataset enfrenta uma taxa de churn de 26,54% de sua base de clientes. O problema de negócio endereçado por este dashboard é: **como identificar, de forma visual e acessível, os principais fatores associados ao cancelamento de clientes, de modo a orientar ações de retenção mais direcionadas?**

## Dataset

- **Origem:** [Kaggle: blastchar/telco-customer-churn](https://www.kaggle.com/datasets/blastchar/telco-customer-churn), com dados originalmente disponibilizados pela IBM (IBM Sample Data Sets).
- **Quantidade de registros:** 7.043 clientes.
- **Quantidade de atributos:** 21 colunas, incluindo a variável alvo.
- **Principais colunas:** `customerID`, `gender`, `SeniorCitizen`, `Partner`, `Dependents`, `tenure`, `PhoneService`, `MultipleLines`, `InternetService`, `OnlineSecurity`, `OnlineBackup`, `DeviceProtection`, `TechSupport`, `StreamingTV`, `StreamingMovies`, `Contract`, `PaperlessBilling`, `PaymentMethod`, `MonthlyCharges`, `TotalCharges`, `Churn`.
- **Variável alvo:** `Churn` (Yes/No): indica se o cliente cancelou o contrato.
- **Significado das informações:** cada linha representa um cliente único da empresa de telecomunicações, com atributos demográficos (gênero, se é idoso, se possui parceiro/dependentes), atributos contratuais (tipo de contrato, tempo de permanência, forma de pagamento), atributos de serviços contratados (internet, linhas telefônicas, segurança online, backup, streaming) e atributos financeiros (cobrança mensal e total).
- **Qualidade dos dados:** conforme amplamente documentado na literatura pública sobre este dataset, a coluna `TotalCharges` é originalmente armazenada como texto e contém um pequeno número de valores em branco, associados a clientes com `tenure = 0`. Não há relatos, na documentação oficial, de duplicidade de identificadores de cliente. O tratamento específico de qualidade de dados realizado neste projeto (se houve remoção de valores nulos, conversões de tipo, etc.) **não é visível a partir do dashboard publicado** e é discutido de forma mais detalhada na seção de ETL, abaixo.

## Processo de ETL

> **Limitação identificada:** o processo de ETL (Extração, Transformação e Carga) não pode ser totalmente reconstruído apenas a partir do dashboard publicado e das imagens das páginas, pois essas etapas ocorrem no Power Query, cuja visualização exige acesso ao arquivo `.pbix` original. As observações abaixo combinam evidências indiretas (nomenclaturas e categorias visíveis no relatório) com boas práticas usuais do mercado para dados dessa natureza.

- **Importação:** os dados foram, muito provavelmente, importados diretamente do arquivo CSV oficial do Kaggle (`WA_Fn-UseC_-Telco-Customer-Churn.csv`) para o Power BI via Power Query.
- **Limpeza:** não é possível confirmar, a partir do dashboard, se houve tratamento de valores nulos na coluna `TotalCharges` (documentadamente presente no dataset original). Trata-se de uma etapa esperada, mas não verificável externamente.
- **Transformação/Padronização:** há evidência clara, nas categorias exibidas no dashboard, de que os valores de diversas colunas categóricas foram **traduzidos do inglês para o português**, incluindo: tipo de contrato ("Sem fidelidade (mensal)", "Fidelidade de 1 ano", "Fidelidade de 2 anos"), forma de pagamento ("Cheque eletrônico", "Cheque enviado pelo correio", "Transferência bancária", "Cartão de crédito"), gênero ("Homem"/"Mulher") e a variável alvo ("Sim"/"Não" para "Cancelou o Contrato?"). Essa tradução pode ter sido implementada via Power Query (substituição de valores) ou via tabela de mapeamento/DAX.
- **Criação de colunas:** há evidência de uma coluna calculada de agrupamento de tempo de contrato ("0-6 meses", "7-12 meses", "13-24 meses", "25+ meses"), derivada da coluna numérica `tenure` do dataset original. Essa é a única coluna derivada identificável com segurança a partir das visualizações do dashboard.
- **Conversões:** não é possível confirmar conversões de tipo específicas (ex.: texto para número em `TotalCharges`) apenas pelo dashboard publicado.
- **Modelagem:** discutida a seguir, na seção "Modelagem dos Dados".

## Modelagem dos Dados

A modelagem de dados exata não pôde ser confirmada a partir das fontes disponíveis para este projeto de documentação, já que essa informação só é visível na visão de "Modelo" do arquivo `.pbix` original. Uma estrutura hipotética, composta provavelmente por uma tabela fato única (refletindo a estrutura de arquivo único do dataset de origem) com uma coluna calculada de faixas de tempo de contrato, é a hipótese mais consistente com o que é observável nas visualizações do dashboard.

## KPIs

Os quatro indicadores a seguir são exibidos de forma fixa no cabeçalho de todas as páginas do dashboard:

### Clientes Totais (7.043)
- **Definição:** contagem total de clientes únicos na base de dados.
- **Objetivo:** fornecer o tamanho absoluto da base analisada, dando contexto de escala aos demais indicadores.
- **Interpretação:** corresponde exatamente ao total de registros do dataset oficial (7.043 linhas), o que indica que o dashboard trabalha com a base completa, sem filtragem de amostra.
- **Importância para o negócio:** dimensiona o universo de clientes sobre o qual as demais métricas (churn, retenção, ticket médio) são calculadas.

### Taxa de Churn (26,54%)
- **Definição:** percentual de clientes que cancelaram o contrato em relação ao total da base.
- **Objetivo:** medir a intensidade do problema de cancelamento na base de clientes.
- **Interpretação:** aproximadamente 1 em cada 4 clientes da base analisada cancelou o serviço.
- **Importância para o negócio:** é o indicador central do problema de negócio abordado pelo dashboard: orienta diretamente a priorização de ações de retenção.

### Taxa de Retenção (73,46%)
- **Definição:** percentual de clientes que permanecem ativos (complemento da taxa de churn).
- **Objetivo:** oferecer a visão inversa e complementar à taxa de churn, facilitando a leitura em termos de "sucesso" de retenção.
- **Interpretação:** cerca de 73,46% da base permanece ativa, valor que somado à taxa de churn totaliza 100% da base.
- **Importância para o negócio:** serve como métrica de acompanhamento de metas de retenção ao longo do tempo.

### Ticket Médio (R$ 3,52 Mil)
- **Definição:** valor médio de cobrança por cliente (a base de cálculo específica, cobrança mensal ou total, não pôde ser confirmada apenas pelo dashboard).
- **Objetivo:** dimensionar o valor financeiro médio associado a cada cliente da base.
- **Interpretação:** fornece uma referência de valor médio por cliente, útil para estimar o impacto financeiro do churn (ex.: perda de receita associada aos clientes cancelados).
- **Importância para o negócio:** conecta a análise de churn a uma perspectiva financeira, permitindo estimar o impacto em receita de cada ponto percentual de churn reduzido ou aumentado.

## Dashboard

O relatório é composto por 4 páginas. A descrição completa de cada uma (objetivo, indicadores, gráficos, filtros e interpretação) está documentada em detalhe em [`DASHBOARD.md`](DASHBOARD.md). Em síntese:

![Página 1 - Churn](imagens/pagina-1.jpeg)

- **Página Churn:** analisa o risco de cancelamento ao longo do tempo de contrato, com dois gráficos (churn por faixa de tenure; evolução do churn ao longo do tempo).

![Página 2 - Impacto](imagens/pagina-2.jpeg)

- **Página Impacto:** relaciona serviços contratados (backup online) e tempo de contrato ao comportamento de cancelamento.

![Página 3 - Financeiro](imagens/pagina-3.jpeg)

- **Página Financeiro:** analisa o impacto de formas de pagamento e tipo de internet na receita e no churn.

![Página 4 - Perfil](imagens/pagina-4.jpeg)

- **Página Perfil:** segmenta a base por tipo de contrato e por gênero.

## Principais Insights

A partir do que foi observado nos títulos e valores das visualizações do dashboard, destacam-se os seguintes insights:

- O risco de churn é significativamente maior nos primeiros meses de contrato, concentrando a maior parte dos cancelamentos no primeiro ano de relacionamento.
- Serviços adicionais (como backup online) e determinadas formas de pagamento (como cartão de crédito) estão associados a menor churn, segundo os títulos dos gráficos do dashboard.
- Contratos mensais concentram a maioria da base de clientes e apresentam maior churn relativo em comparação a contratos anuais/bianuais.
- A base de clientes de fibra óptica representa uma parcela maior de receita em comparação à base de clientes DSL.
- Observa-se uma diferença de retenção entre gêneros especificamente no segmento de contratos anuais, segundo o título de um dos gráficos, ainda que a distribuição geral de gênero na base seja praticamente equilibrada.

## Conclusão

O Dashboard de Churn e Comportamento do Cliente consolida, de forma visual e direta, os principais fatores associados ao cancelamento de clientes em uma base de telecomunicações, utilizando como fonte o dataset público Telco Customer Churn (IBM/Kaggle). A estrutura em quatro páginas (Churn, Impacto, Financeiro e Perfil) permite uma leitura progressiva do problema de negócio: primeiro identificando *quando* o churn ocorre, depois *quais fatores* estão associados a ele, em seguida *qual o impacto financeiro* envolvido, e por fim *qual o perfil* dos clientes mais suscetíveis ao cancelamento.

Do ponto de vista técnico, este projeto evidencia boas práticas de comunicação de dados, como o uso de títulos de gráficos como conclusões diretas de negócio e a manutenção de KPIs fixos e consistentes em todas as páginas do relatório. As limitações identificadas, relacionadas à ausência de acesso ao arquivo `.pbix` original para validação de ETL, modelagem e medidas DAX, foram registradas de forma explícita ao longo deste relatório e dos demais documentos do repositório, em conformidade com o princípio de não inferir informações que não possam ser diretamente observadas ou razoavelmente hipotetizadas a partir das fontes disponíveis.
