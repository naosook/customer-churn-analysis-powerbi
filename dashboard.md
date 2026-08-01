# Documentação do Dashboard

> Todas as informações abaixo foram extraídas diretamente do dashboard publicado no Power BI e das imagens de cada página. Interpretações de negócio estão sinalizadas como tal.

O relatório é composto por **4 páginas**, acessíveis por um menu de navegação superior fixo: **Churn**, **Impacto**, **Financeiro** e **Perfil**. Todas as páginas compartilham o mesmo cabeçalho com título ("Dashboard de Churn e Comportamento do Cliente") e os mesmos quatro cartões de KPI:

| KPI | Valor |
|---|---|
| Clientes Totais | 7.043 |
| Taxa de Churn (%) | 26,54% |
| Taxa de Retenção (%) | 73,46% |
| Ticket Médio | R$ 3,52 Mil |

Esses indicadores permanecem fixos (não filtrados por página), funcionando como uma visão-resumo constante do negócio em todas as telas.

### Painel de Filtros

No canto superior direito do cabeçalho, um ícone de configurações abre um **painel de filtros** flutuante, aplicável ao relatório. Nas imagens fornecidas, esse painel foi capturado sobreposto à página **Financeiro** (visível ao fundo o rótulo "DSL" e o valor "3,1 Mil"), contendo as seguintes segmentações:

| Filtro | Opções |
|---|---|
| Tipo de Internet | Selecionar tudo, DSL, Fibra óptica |
| Backup Online | Não, Sim |
| Status do Contrato | Ativo, Cancelado |

O painel conta ainda com um botão **"Limpar filtros"**, que reseta as segmentações aplicadas.

O mesmo ícone de filtros aparece no cabeçalho das quatro páginas do relatório (Churn, Impacto, Financeiro e Perfil), o que indica que esse painel está disponível em todas elas. A confirmação visual do conteúdo do painel, entretanto, foi obtida apenas a partir da captura feita sobre a página Financeiro.

---

## Página 1: Churn

**Subtítulo observado:** "Análise de Risco de Churn: Segmentos Críticos e Ações Prioritárias"

![Página 1 - Churn](imagens/pagina-1.jpeg)

### Objetivo
Apresentar como o risco de cancelamento se comporta ao longo do tempo de relacionamento do cliente com a empresa.

### Indicadores apresentados
Os 4 KPIs fixos do cabeçalho (Clientes Totais, Taxa de Churn, Taxa de Retenção, Ticket Médio).

### Gráficos utilizados

**1. "Churn por Tempo de Contrato: Clientes com 0-6 meses têm risco 36% (2x acima da média)"**
- Tipo: gráfico de área/linha
- Eixo X: faixas de tempo de contrato: 0-6 meses, 7-12 meses, 13-24 meses, 25+ meses
- Eixo Y: percentual de churn
- Valores observados: 52,94% (0-6 meses), 35,89% (7-12 meses), 28,71% (13-24 meses), 14,04% (25+ meses)
- **Observação:** o título do gráfico menciona "risco 36%" para a faixa de 0-6 meses, enquanto o valor plotado nessa faixa é 52,94%. Essa diferença é reportada aqui exatamente como aparece no dashboard, sem tentativa de correção ou suposição sobre sua causa.

**2. "Evolução do Churn: 70% dos cancelamentos ocorrem nos primeiros 12 meses"**
- Tipo: gráfico de linha
- Eixo X: tempo de contrato (0 a 80, provavelmente em meses)
- Eixo Y: percentual de churn (0% a 70%)
- Valores observados ao longo da linha: 61,99% (início), 36,36%, 29,11%, 27,54%, 15,29%, 9,84%, 14,61%, 1,66% (final)
- Uma linha de referência horizontal (próxima a 22-23%) aparenta representar a taxa média de churn da base

### Filtros
Disponível via ícone de filtros no canto superior direito do cabeçalho com segmentações por Tipo de Internet, Backup Online e Status do Contrato.

### Pergunta de negócio respondida
"Em que momento do ciclo de vida do cliente o risco de cancelamento é maior?"

---

## Página 2: Impacto

**Subtítulo observado:** "Fatores de Retenção: Como Serviços e Tempo de Contrato Impactam a Fidelização"

![Página 2 - Impacto](imagens/pagina-2.jpeg)

### Objetivo
Explorar quais serviços contratados e faixas de tempo de contrato estão associados a maior ou menor retenção de clientes.

### Gráficos utilizados

**1. "Backup Online Reduz Churn em 20%: Oportunidade para Promoção" / "Clientes com Backup Online tendem a cancelar menos?"**
- Tipo: gráfico de barras horizontais empilhadas
- Categoria: "Cancelou o Contrato?" (Não / Sim)
- Valores observados: Não = 5,2 Mil; Sim = 1,9 Mil; total = 7,04 Mil

**2. "Tempo de Contrato vs. Churn: 60% dos cancelamentos em clientes com 1 ano"**
- Tipo: gráfico de barras agrupadas
- Eixo X: faixas de tempo de contrato (0-6 meses, 7-12 meses, 13-24 meses, 25+ meses)
- Categoria: "Cancelou o Contrato?" (Não / Sim)
- Valores observados:

| Faixa de tempo | Não cancelou | Cancelou |
|---|---|---|
| 0-6 meses | 697 | 784 |
| 7-12 meses | 452 | 253 |
| 13-24 meses | 730 | 294 |
| 25+ meses | 3.295 | 538 |

### Filtros
Disponível via ícone de filtros no canto superior direito do cabeçalho, com segmentações por Tipo de Internet, Backup Online e Status do Contrato.

### Pergunta de negócio respondida
"Quais serviços contratados e faixas de tempo de contrato estão associados a maior retenção de clientes?"

---

## Página 3: Financeiro

**Subtítulo observado:** "Estratégias Financeiras: Como Pagamentos e Serviços Impactam Receita"

![Página 3 - Financeiro](imagens/pagina-3.jpeg)

### Objetivo
Analisar o impacto de diferentes formas de pagamento e tipos de serviço de internet sobre a receita e o comportamento de cancelamento.

### Gráficos utilizados

**1. "Pagamento por Cartão Tem 15% Menos Churn: Incentivo a Migração"**
- Tipo: gráfico de barras horizontais
- Categoria: forma de pagamento
- Valores observados: Cheque eletrônico = 2.365; Cheque enviado pelo correio = 1.612; Transferência bancária = 1.544; Cartão de crédito = 1.522

**2. "Fibra Óptica Gera 2x Mais Receita que DSL (R$ 4K vs. R$ 2K)"**
- Tipo: gráfico de barras verticais
- Categoria: tipo de serviço de internet
- Valores observados no gráfico: Fibra óptica = 3,7 Mil; DSL = 3,1 Mil
- **Observação:** o título indica "R$ 4K vs. R$ 2K", enquanto os valores plotados nas barras são 3,7 Mil e 3,1 Mil. Essa diferença é reportada exatamente como aparece no dashboard, sem suposição sobre sua causa (pode estar relacionada a arredondamento do título, período de referência distinto, ou unidade de medida diferente da exibida no eixo).

### Filtros
Confirmado nas imagens fornecidas: painel de filtros acessível pelo ícone no canto superior direito do cabeçalho, com segmentações por Tipo de Internet (Selecionar tudo, DSL, Fibra óptica), Backup Online (Não, Sim) e Status do Contrato (Ativo, Cancelado), além do botão "Limpar filtros". Ver detalhamento no início deste documento.

### Pergunta de negócio respondida
"Quais estratégias de pagamento e de tipo de serviço têm maior impacto na receita e no churn?"

---

## Página 4: Perfil

**Subtítulo observado:** "Segmentação de Clientes: Demografia e Tipos de Contrato com Maior Retenção"

![Página 4 - Perfil](imagens/pagina-4.jpeg)

### Objetivo
Segmentar a base de clientes por tipo de contrato e por gênero, relacionando essas dimensões à retenção.

### Gráficos utilizados

**1. "Contratos Mensais Têm 55% de Adesão, mas Churn 30% Maior que Anuais" / "Contagem de ID do Cliente por tipo de Contrato"**
- Tipo: gráfico de pizza
- Categorias e valores observados: Sem fidelidade (mensal) = 55,02%; Fidelidade de 2 anos = 24,07%; Fidelidade de 1 ano = 20,91%

**2. "Mulheres em Contratos Anuais Têm 5% Mais Retenção" / "Distribuição de Clientes por Gênero"**
- Tipo: gráfico de rosca (donut)
- Categorias e valores observados: Homem = 50,48%; Mulher = 49,52%

### Filtros
Disponível via ícone de filtros no canto superior direito do cabeçalho, com segmentações por Tipo de Internet, Backup Online e Status do Contrato.

### Pergunta de negócio respondida
"Qual o perfil contratual e demográfico da base de clientes, e como ele se relaciona com a retenção?"

