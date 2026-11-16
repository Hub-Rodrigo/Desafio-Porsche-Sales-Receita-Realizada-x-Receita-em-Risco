# 🏎️ Porsche Sales: Receita Realizada x Receita em Risco

Dashboard web interativo desenvolvido para análise comercial de **100 vendas da Porsche nos Estados Unidos**, com foco na visibilidade entre **receita efetivamente entregue**, **receita em risco operacional** (em trânsito ou aguardando aprovação) e **perdas por cancelamento**.

![Preview do Dashboard](assets/dashboard_preview.png)

---

## 🎯 Objetivo do Projeto

Transformar dados transacionais sanitizados de vendas de veículos em um painel executivo leve, responsivo e interativo, respondendo a quatro perguntas estratégicas de negócio:

1. **Quanto da receita líquida já está efetivamente entregue?**
2. **Qual família de modelos sustenta o faturamento e o ticket médio?**
3. **Quais métodos de pagamento concentram o maior volume financeiro?**
4. **Onde estão concentradas as maiores transações do recorte selecionado?**

---

## 📊 Principais Indicadores e Insights (Visão Geral)

Considerando a base completa de **100 transações** (Receita Bruta Total de **$12.827.800,50**):

| Indicador | Valor | Detalhamento |
| :--- | :---: | :--- |
| **Receita Líquida (Não Cancelada)** | **$12.202.550,50** | 93 vendas válidas (exclui 7 cancelamentos) |
| **Ticket Médio Líquido** | **$131.210,22** | Média por veículo vendido (não cancelado) |
| **Receita Já Entregue (Realizada)** | **$5.078.800,50** | **41,62%** da receita líquida (41 veículos) |
| **Receita em Risco / Pipeline** | **$7.123.750,00** | **58,38%** da receita líquida (52 veículos) |
| **Receita Cancelada** | **$625.250,00** | 4,87% do volume bruto (7 veículos) |

### Destaques Analíticos
* **Liderança por Família:** A linha **911** lidera com folga o faturamento líquido (**$4.168.100,00** — **34,16%** do total e ticket médio de **$189.459,09**), seguida por **Taycan** ($2,33M) e **Cayenne** ($2,08M).
* **Atenção à Receita em Risco:** Mais da metade da receita líquida (**58,38%**) ainda depende de conclusão logística (*Em andamento*: $3,92M) ou liberação cadastral/financeira (*Aguardando aprovação*: $3,21M), incluindo o maior pedido da base (**911 GT3 RS** de **$286.500,00** no Texas, ainda *Pending*).
* **Meios de Pagamento:** **Wire Transfer** concentra **32,61%** da receita líquida (**$3.979.450,00** em 26 vendas), seguido por **Credit Card** (14,75%) e **Financing** (11,69%). Pagamentos via **Crypto Payment** apresentam o maior ticket médio da operação (**$180.500,00**).
* **Concentração Geográfica:** **Texas (TX)** ($2,02M) e **Califórnia (CA)** ($1,97M) lideram o faturamento líquido entre os estados norte-americanos.

---

## ⚙️ Regras de Negócio e Agrupamento de Status

Para facilitar a leitura executiva de risco, os **10 status originais** da base foram consolidados em **4 macroetapas**:

| Macroetapa (`grupo`) | Status Originais Agrupados (`status`) | Qtd. Vendas | Receita Total |
| :--- | :--- | :---: | :---: |
| **Entregue** | `Delivered` | 41 | $5.078.800,50 |
| **Em andamento** | `In Transit`, `Awaiting Delivery`, `Awaiting Pickup`, `Shipped` | 28 | $3.917.600,00 |
| **Aguardando aprovação** | `Pending`, `Pending Approval`, `Pending Review`, `Awaiting Review` | 24 | $3.206.150,00 |
| **Cancelado** | `Cancelled` | 7 | $625.250,00 |

* **Tratamento e Privacidade (LGPD/Sanitização):** Colunas sensíveis (nome do cliente e vendedor) foram removidas na etapa de sanitização, mantendo apenas atributos analíticos (`id`, `data`, `modelo`, `familia`, `ano`, `preco`, `pagamento`, `cidade`, `estado` e `status`). Registros sem data preenchida foram padronizados como `"Sem data"` (24 ocorrências).

---

## 🛠️ Tecnologias e Recursos Implementados

* **HTML5 Semântico & Acessibilidade:** Uso de landmarks (`<header>`, `<main>`, `<section>`, `<footer>`), atributos ARIA (`role="group"`, `role="img"`, `aria-label`) e suporte a `prefers-reduced-motion`.
* **CSS3 Moderno (Design System):** Layout responsivo com CSS Grid e Flexbox, tipografia *Barlow Condensed* & *Barlow*, e paleta inspirada na identidade visual Porsche (`#15171c` Asphalt Dark, `#c8102e` Guards Red e `#eceef1` Neutral Surface).
* **JavaScript Vanilla (ES6+):** Motor de filtragem combinada em tempo real por **Família**, **Ano do Modelo**, **Estado (UF)** e **Método de Pagamento**, com cálculo dinâmico de KPIs, barra empilhada proporcional, rankings horizontais, narrativa executiva automática e tabela Top 10 maiores vendas.

---

## 🚀 Como Executar Localmente

Por ser uma aplicação *single-file* sem dependências externas de build:

1. Clone este repositório:
   ```bash
   git clone [https://github.com/seu-usuario/porsche-sales-dashboard.git](https://github.com/seu-usuario/porsche-sales-dashboard.git)
