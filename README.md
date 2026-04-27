# 📊 Sales Report – Desafio Power BI

## Relatório Financeiro com Foco na Experiência do Usuário

---

## 🎯 Objetivo do Desafio

Modificar um relatório financeiro criativo no Power BI, aplicando princípios de **experiência do usuário (UX)** para torná-lo mais intuitivo, visualmente organizado e navegável. O desafio envolve 3 páginas completas com menus de navegação e estilização avançada.

---

## 📐 Princípios de UX Aplicados

### 1. Segmentação dos Dados
Separar informações em grupos lógicos por página:
- **Página 1 (Apresentação)**
- **Página 2 (Principal):** Visão geral — KPIs, período, segmentos e países
- **Página 3:** Análise de vendas — detalhamento mensal e por produto

---


## 🖥️ Página Principal — Elementos e Como Recriar

### Cabeçalho (Header)
| Elemento | Como criar no Power BI |
|----------|------------------------|
| Retângulo branco de fundo | Inserir → Formas → Retângulo |
| Título "Sales Report" | Caixa de texto com fonte grande e negrito |
| Imagem do boneco | Inserir → Imagem → selecionar PNG |
| Seletor de data | Inserir → Segmentação de dados → campo Date |
| Ícone de borracha (limpar) | Inserir → Botão → Em branco + ação "Limpar todos os filtros" |

### KPIs
| Métrica | Campo do dataset |
|---------|-----------------|
| Total de Vendas | `SUM(Sales)` |
| Unidades Vendidas | `SUM(Units Sold)` |
| Soma de Descontos | `SUM(Discounts)` |
| Soma de COGS | `SUM(COGS)` |

> Usar visual **Cartão** para cada métrica. Formatar número em Mi (÷ 1.000.000).

### Gráfico de Área — "Vendas por Período"
- Visual: **Gráfico de área**
- Eixo X: `Month Name` (ordenado por `Month Number`)
- Valores: `SUM(Sales)`
- Cor da linha: azul claro
- Fundo: roxo médio
- Ativar **Rótulos de dados** desligado para visual limpo

### Vendas x Segmento
- Visual: **Gráfico de barras horizontais** (Barra clusterizada)
- Eixo Y: `Segment`
- Valores: `SUM(Sales)`
- Adicionar botões para alternar entre **Bar Chart** e **Pie Chart**:
  - Usar **Indicadores** + **Botões** para trocar o visual ativo

### Vendas por Produto
- Visual: **Gráfico de barras horizontais**
- Eixo Y: `Product`
- Valores: `SUM(Sales)`
- Adicionar linha de **Somatório** via medida DAX:
```dax
Somatório = SUMX(TOPN(2, VALUES(financials[Product]), [Total Sales], DESC), [Total Sales])
```

### Treemap / Map Chart — Países
- Visual: **Treemap**
  - Categoria: `Country`
  - Valores: `SUM(Sales)`
- Visual: **Mapa preenchido (Filled Map)**
  - Localização: `Country`
  - Saturação de cor: `SUM(Sales)`
- Criar botões **Tremap** e **Map Chart** para alternar entre os dois visuais

---

## 🎨 Paleta de Cores Usada

| Uso | Cor Hex |
|-----|---------|
| Fundo principal | `#4B0082` / `#6A0DAD` |
| KPI background | `#FFFFFF` |
| Gráfico de área | `#1E90FF` |
| Barras – Government | `#FFD700` |
| Barras – Small Business | `#F5DEB3` |
| Treemap – USA | `#1E90FF` |
| Treemap – France | `#FF8C00` |
| Treemap – Germany | `#FF69B4` |
| Treemap – Canada | `#228B22` |
| Treemap – Mexico | `#FF1493` |
| Botões ativos | `#FFFFFF` com borda escura |

---

## 📋 Medidas DAX Essenciais

```dax
-- Total de Vendas em Milhões
Total Sales Mi = DIVIDE(SUM(financials[Sales]), 1000000)

-- Unidades Vendidas em Milhões
Units Mi = DIVIDE(SUM(financials[Units Sold]), 1000000)

-- Soma de Descontos em Milhões
Discounts Mi = DIVIDE(SUM(financials[Discounts]), 1000000)

-- COGS em Milhões
COGS Mi = DIVIDE(SUM(financials[COGS]), 1000000)

-- Lucro Bruto
Gross Profit = SUM(financials[Sales]) - SUM(financials[COGS])
```


## 🛠️ Ferramentas e Recursos

- **Power BI Desktop** — versão gratuita disponível em [powerbi.microsoft.com](https://powerbi.microsoft.com)
- **Dataset:** `financials` (Financial Sample — disponível nativamente no Power BI)
  - Acessar via: Obter dados → Exemplos → Financial Sample
- **Ícones gratuitos:** [flaticon.com](https://flaticon.com) · [icons8.com](https://icons8.com)
- **Paletas de cor:** [coolors.co](https://coolors.co) · [colorhunt.co](https://colorhunt.co)

---


