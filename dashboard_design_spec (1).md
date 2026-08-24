# Dashboard Ecommerce — Design Specification

> Documento para replicação visual e funcional exata do dashboard. Qualquer IA ou desenvolvedor deve conseguir reproduzir o projeto a partir deste spec.

---

## 1. Identidade Visual

### Paleta de Cores

#### Cores principais
| Nome | Hex | Uso |
|---|---|---|
| Fundo escuro principal | `#1a1a2e` | Cabeçalho da navbar, cabeçalho de tabelas, headers de seção |
| Azul escuro | `#0c447c` | Coluna Acumulado, destaques |
| Azul médio | `#185fa5` | Links, métricas em destaque, hover |
| Azul claro | `#378add` | Valores de sessões, links secundários |
| Azul muito claro | `#85b7eb` | Escala de cores do mapa |
| Azul pastel | `#b5d4f4` | Escala de cores do mapa |
| Azul fundo | `#e6f1fb` | Escala de cores do mapa, fundo cards |

#### Cores de texto
| Nome | Hex | Uso |
|---|---|---|
| Texto principal | `#2a2e45` | Texto geral da tabela |
| Texto secundário | `#6b7591` | Labels, categorias, textos de apoio |
| Texto muito claro | `#9aa3bf` | Numeração, textos desabilitados |
| Branco | `#e8eaf0` | Texto sobre fundo escuro |

#### Cores de status
| Nome | Hex | Uso |
|---|---|---|
| Verde positivo | `#0ca30c` | Variação positiva ▲ |
| Vermelho negativo | `#d03b3b` | Variação negativa ▼ |
| Verde destaque | `#7ed348` | Nome de produto na tabela, destaques verdes |
| Verde suave | `#eaf3de` | Fundo de Faturamento/ROAS na simulação |
| Verde texto | `#3b6d11` | Texto sobre fundo verde suave |

#### Cores de borda e fundo
| Nome | Hex | Uso |
|---|---|---|
| Borda principal | `#d0d5e0` | Bordas de cards e tabelas |
| Borda interna | `#eceef3` | Divisórias internas de linhas |
| Fundo da página | `#f0f2f5` | Background geral |
| Fundo card | `#fff` | Background de cards e tabelas |
| Fundo zebra claro | `#fafbff` | Linhas alternadas, labels |
| Fundo zebra azul | `#e6f1fb` | Labels editáveis na simulação |

#### Cores de badges (Curva ABC)
| Nome | Hex | Uso |
|---|---|---|
| Badge A fundo | `#e8f5e9` | Badge Curva A e Q-A |
| Badge A texto | `#155724` | Texto badge A |
| Badge B fundo | `#fff3cd` | Badge Curva B |
| Badge B texto | `#856404` | Texto badge B |
| Badge C fundo | `#fce4ec` | Badge Curva C e Q-D |
| Badge C texto | `#880e4f` | Texto badge C |
| Badge Q-B fundo | `#e3f2fd` | Badge quadrante B |
| Badge Q-B texto | `#0d47a1` | Texto badge Q-B |
| Badge Q-C fundo | `#fff8e1` | Badge quadrante C |
| Badge Q-C texto | `#856404` | Texto badge Q-C |

#### Cores especiais Meta x Realizado
| Nome | Hex | Uso |
|---|---|---|
| Projeção header | `#5f5e5a` | Cabeçalho coluna projeção |
| Realizado header | `#1e5631` | Cabeçalho coluna realizado |
| Plataforma header | `#0c447c` | Cabeçalho coluna plataforma |
| Realizado fundo | `#e8f5e9` | Células coluna realizado |
| Plataforma fundo | `#e3f2fd` | Células coluna plataforma |

---

### Tipografia
| Tamanho | Uso |
|---|---|
| 7px | Labels de siglas no mapa SVG |
| 8px | Textos mínimos |
| 9px | Labels de fórmula na simulação, variações pequenas |
| 10px | Labels de seção em uppercase, badges, variações ▲▼ |
| 11px | Células de tabela secundárias, tooltips |
| 12px | Células de tabela padrão, texto de cards |
| 13px | Células principais, inputs, labels de formulário |
| 20px | Valores em destaque nos cards de KPI |
| 22px | KPIs principais na Visão Geral |

**Fonte:** sistema (sem fonte externa importada — usa a fonte padrão do navegador)

**Pesos usados:** 400 (normal), 500 (medium), 600 (semibold), 700 (bold)

**Letras maiúsculas:** labels de seção usam `text-transform: uppercase` + `letter-spacing: 0.06em` a 0.08em`

---

## 2. Layout Geral

### Estrutura da página
```
┌─────────────────────────────────────────┐
│  NAVBAR (fundo #1a1a2e, altura ~44px)   │
│  "Dashboard · Ecommerce"                │
├─────────────────────────────────────────┤
│  ABAS (fundo #fff, borda inferior)      │
│  [Aba1] [Aba2] [Aba3] ... [Aba8]       │
│  Aba ativa: sublinhado amarelo #f5a623  │
├─────────────────────────────────────────┤
│  CONTEÚDO DA ABA ATIVA                  │
│  padding: 16px                          │
│  background: #f0f2f5                    │
└─────────────────────────────────────────┘
```

### Navbar
- Background: `#1a1a2e`
- Texto: `"Dashboard · Ecommerce"` em branco, fonte 13px, bold
- Altura: ~44px
- Padding: 0 16px

### Barra de abas
- Background: `#fff`
- Borda inferior: `1px solid #eceef3`
- Aba normal: texto `#6b7591`, sem sublinhado
- Aba ativa: texto `#1a1a2e`, bold, sublinhado amarelo `#f5a623` de 2px na base
- Hover: texto escurece
- Padding por aba: 12px 16px
- As abas que não cabem ficam em scroll horizontal

### Cards brancos (padrão de todos os blocos)
```css
background: #fff;
border: 1px solid #d0d5e0;
border-radius: 8px;
padding: 14px 18px;
margin-bottom: 14px;
```

---

## 3. Componentes Reutilizáveis

### Botões de período (7 dias / 14 dias / 30 dias)
```css
/* Normal */
background: #fff;
border: 1px solid #d0d5e0;
color: #6b7591;
padding: 5px 12px;
border-radius: 6px;
font-size: 12px;

/* Ativo */
background: #1a1a2e;
color: #fff;
border-color: #1a1a2e;
```

### Dropdown de seleção (Meses, Comparar)
```css
appearance: none;
background: #fff;
border: 1px solid #d0d5e0;
color: #1a1a2e;
padding: 6px 32px 6px 12px;
border-radius: 6px;
font-size: 13px;
min-width: 180px;
```
- Ícone ▾ posicionado absolutamente à direita

### Variação ▲▼
```
▲ X.X%  →  color: #0ca30c (verde)
▼ X.X%  →  color: #d03b3b (vermelho)
font-size: 10px
margin-left: 3px
```

### Paginação (padrão usado em Taxa Conversão, ABC, Regiões)
```
[Mostrando 1–15 de 43 produtos]    [← Anterior]  [Página 1 de 3]  [Próxima →]
```
- Rodapé da tabela
- Background: `#fafbff`
- Borda topo: `1px solid #eceef3`
- Padding: 10px 16px
- Texto info: `font-size: 12px; color: #6b7591`
- Botões: estilo padrão de período
- Botão desabilitado: `opacity: 0.4`

### Badges Curva ABC
```css
/* Badge A */
background: #e8f5e9; color: #155724;
padding: 2px 8px; border-radius: 4px; font-size: 11px; font-weight: 600;

/* Badge B */
background: #fff3cd; color: #856404;

/* Badge C */
background: #fce4ec; color: #880e4f;
```

### Badges Matriz BCG
```
Q-A ⭐ Estrela    → fundo #e8f5e9, texto #155724
Q-B 🚀 Potencial  → fundo #e3f2fd, texto #0d47a1
Q-C 🔍 Revisar    → fundo #fff8e1, texto #856404
Q-D ⚠️ Atenção    → fundo #fce4ec, texto #880e4f
```

---

## 4. Tabelas — Padrão Visual

### Cabeçalho de tabela
```css
background: #1a1a2e;
color: #e8eaf0;
font-size: 11px;
font-weight: 500;
padding: 7px 12px;
text-align: right; /* exceto primeira coluna que é left */
border-bottom: 1px solid #2d3352;
white-space: nowrap;
```

### Células padrão
```css
padding: 6px 12px;
border-bottom: 1px solid #eceef3;
text-align: right;
color: #2a2e45;
font-size: 12px;
white-space: nowrap;
```

### Célula de métrica (primeira coluna, sticky)
```css
text-align: left;
position: sticky;
left: 0;
z-index: 2;
background: #fff;
color: #185fa5; /* azul */
font-weight: 500;
min-width: 160–190px;
border-right: 1px solid #eceef3;
```

### Hover nas linhas
```css
.row:hover td { background: #f7f8fc; }
```

### Coluna Acumulado (sticky direita)
```css
background: #f0f6ff;
color: #185fa5;
font-weight: 500;
position: sticky;
right: 0;
border-left: 2px solid #d0dff5;
```

### Cabeçalho Acumulado
```css
background: #0c447c;
position: sticky;
right: 0;
border-left: 2px solid #2d3352;
```

---

## 5. Aba 1 — Acompanhamento de Resultado

### Layout
```
[Filtros: ANO | MESES]
[Container fixo com scroll interno]
  ├── Cabeçalho sticky (Métrica | datas... | Acumulado)
  ├── Bloco GERAL (colapsável)
  │   └── 11 métricas
  ├── Bloco FACEBOOK (colapsável)
  │   └── 8 métricas
  ├── Bloco GOOGLE (colapsável)
  └── ... demais canais
```

### Container de scroll interno
- `overflow-x: auto` + `overflow-y: auto`
- `max-height: calc(100vh - 200px)`
- Scroll acontece DENTRO do container, a página não rola

### Cabeçalho das colunas
- Quando colapsado: mostra só o mês (`Jan`, `Fev`...)
- Quando expandido: mostra os dias do mês (`01/01`, `02/01`...)
- Clique no mês expande/colapsa os dias
- Ícone ▶ rotaciona 90° quando expandido

### Separadores de canal
```css
background: #1a1a2e;
color: #7ed348; /* verde */
font-size: 11px;
font-weight: 700;
letter-spacing: 0.06em;
text-transform: uppercase;
cursor: pointer; /* clicável para colapsar */
```

### Métricas com cor azul na coluna Acumulado
- Investimento total
- Receita captada
- Sessões (geral)
- CPS (geral)
- Sessões mídia
- CPS (mídia)
- % sessões mídia

### Canais sem investimento
- Exibem `—` (não zero) nas colunas de Investimento, ROAS, CPS

---

## 6. Aba 2 — Visão Geral

### Layout
```
[Filtros: período + comparação]
[8 KPI cards em linha horizontal]
[2 colunas:]
  Coluna esquerda (60%):
    - Categorias mais vendidas
    - Produtos mais vendidos
  Coluna direita (40%):
    - Vendas por dispositivo
    - Vendas por estado
    - Pesquisa interna
```

### KPI cards
```css
background: #fff;
border: 1px solid #d0d5e0;
border-radius: 8px;
padding: 14px 16px;
flex: 1;
min-width: 120px;
```
- Label: 10px, uppercase, `#6b7591`
- Valor: 22px, bold, `#1a1a2e`
- Variação: 10px, verde/vermelho

### Tabelas de produtos/categorias
- Primeira coluna (nome): `text-align: left`
- Demais colunas: `text-align: right`
- 5 itens por tabela

---

## 7. Aba 3 — UTM

### Layout cascata
```
[Filtros: período + comparação]
[Q1: Origem da Sessão]      utm_source
[Q2: Campanhas]             utm_campaign
[Q3: Medium]                utm_medium
[Q4: Conteúdo]              utm_content
[Q5: Termo de pesquisa]     utm_term
```

### Breadcrumb
```
Filtrando por: Source: facebook > Campaign: camp_verao_2025   [Limpar filtros]
```
- Background: `#f0f6ff`
- Borda: `1px solid #d0dff5`
- Border-radius: 8px
- Texto: `#185fa5`

### Comportamento cascata
- Clique em uma linha → filtra todos os quadros abaixo
- Clique na mesma linha → deseleciona
- Selecionado: fundo `#f0f6ff`, borda esquerda `3px solid #185fa5`
- Cursor: pointer em todas as linhas

### Quadros (Q1 a Q5)
- Cabeçalho do quadro em fundo escuro com label em verde `#7ed348` e tag UTM em `#9aa3bf` à direita
- Q1 tem colunas: Usuários ativos, Sessões, TX conversão, Pedidos, Ticket médio, Receita (com Δ)
- Q2 a Q5 têm colunas: Sessões, CPS, TX conversão, Pedidos, Ticket médio, Receita, ROAS (com Δ)

---

## 8. Aba 4 — Taxa de Conversão por Produto

### Layout
```
[Filtros: ANO | MESES | Busca por nome]
[Tabela com scroll horizontal]
[Paginação: 15 produtos por página]
```

### Estrutura da tabela
```
Métrica (sticky left) | Jan | Fev | Mar | ... | Acumulado (sticky right)
────────────────────────────────────────────────── (linha escura = nome do produto)
Bojo Jani Índia        |     |     |     |     |
────────────────────────────────────────────────── 
Sessões                | 1.100 | 980 | ... | 7.230
Itens vendidos         | 89  | 76  | ... | 592
Receita                | R$6.005 | ...  | R$39.958
Taxa de conversão      | 8,09% | ...  | 8,19%
Preço médio            | R$67,47 | ... | R$67,50
```

### Linha de nome do produto
```css
background: #1a1a2e;
color: #7ed348;
font-size: 11px;
font-weight: 700;
letter-spacing: 0.04em;
text-align: left;
position: sticky;
left: 0;
border-top: 2px solid #d0d5e0;
```

### Regra de agrupamento
- Nomes com tamanho entre parênteses no final são agrupados: `(M)`, `(G)`, `(GG)`, `(35)`, etc.
- Regex: `TRIM(REGEXP_REPLACE(item_name, r'\s*\([^)]*\)\s*$', ''))`
- Sessões, itens e receita são SOMADOS
- Taxa de conversão e preço médio são RECALCULADOS sobre os totais

---

## 9. Aba 5 — Curva ABC / Matriz BCG

### Layout
```
[Card de filtros e legendas]
  ├── Seletor de meses
  ├── TX conversão média (calculada automaticamente)
  ├── Sessões totais (calculadas automaticamente)
  ├── Corte de conversão (calculado automaticamente)
  ├── Legenda — Curva ABC (lado a lado)
  └── Legenda — Quadrantes Matriz BCG
[Tabela com paginação: 30 produtos por página]
```

### Colunas da tabela
`# | Produto | Categoria | Receita total | % receita | % acumulada | Taxa de conversão | Sessões | Itens vendidos | Curva ABC | Matriz BCG`

### Colunas Curva ABC e Matriz BCG
```css
/* Cabeçalho */
background: #2d1f4e; /* roxo escuro */

/* Células */
background: #f3f0fb; /* roxo claro */
```

### Lógica Curva ABC
- A = até 80% receita acumulada
- B = 80% a 95%
- C = acima 95%

### Lógica Matriz BCG
- Corte sessões: percentil 60 dinâmico
- Corte conversão: 90% da média do e-commerce calculada automaticamente
- Q-A: muitas sessões + alta conversão → Estrela
- Q-B: poucas sessões + alta conversão → Potencial
- Q-C: muitas sessões + baixa conversão → Revisar
- Q-D: poucas sessões + baixa conversão → Atenção

---

## 10. Aba 6 — Regiões

### Layout
```
[Filtros: período + comparação]
[Card com 3 colunas:]
  [Cards Sul & Sudeste] | [Mapa SVG Brasil] | [Cards Norte/Nordeste/Centro-Oeste]
[Tabela: Top estados por receita + paginação]
[Tabela: Cidades por receita + paginação]
```

### Mapa SVG
- Paths reais do GeoJSON oficial do Brasil (27 estados)
- Coloração por receita: escala de azul
  - > 80% do máximo: `#0c447c`
  - > 50%: `#185fa5`
  - > 30%: `#378add`
  - > 15%: `#85b7eb`
  - > 5%: `#b5d4f4`
  - resto: `#e6f1fb`
- Tooltip ao hover: Receita, Sessões, TX conversão, ROAS (com Δ)
- `viewBox="50 30 720 640"`

### Cards de região
```css
border-radius: 8px;
padding: 10px 14px;
border-left: 4px solid [cor da região];
```
- Sul: `#185fa5`
- Sudeste: `#0c447c`
- Norte: `#854f0b`
- Nordeste: `#a32d2d`
- Centro-Oeste: `#3b6d11`

Métricas por card (3 colunas em grid):
- Receita | TX conversão | Transações
- Cada uma com variação ▲▼

### Cascata estados → cidades
- Clique no estado: linha fica com fundo `#e6f1fb` + borda esquerda `3px solid #185fa5`
- Breadcrumb aparece: "Filtrando cidades por: São Paulo"
- Tabela de cidades filtra para mostrar só aquele estado
- Clique novamente: deseleciona

### Colunas tabela estados
`Estado | Sessões | CPS | TX conversão | Receita total | ROAS | Invest. Meta (fundo #f0f4ff) | Invest. Google (fundo #fffaf0)`

### Colunas tabela cidades
`Cidade | Estado | Sessões | TX conversão | Pedidos | Receita total | ROAS`

---

## 11. Aba 7 — Simulação

### Layout
```
[Container centralizado, max-width: 760px, margin: 0 auto]
[Card: Planejamento de orçamento × faturamento]
  └── Verba mensal (editável)
[Card: inputs]
  ├── CPS - editável
  ├── Ticket médio - editável
  └── Taxa de conversão - editável
[Card: calculados]
  ├── Visitas mensais  | valor | fórmula: Verba ÷ CPS
  ├── CPA              | valor | fórmula: Verba ÷ Pedidos/mês
  └── Pedidos/mês      | valor | fórmula: Visitas × Taxa conversão
[Card: resultados - fundo verde]
  ├── Faturamento bruto | valor | fórmula: Pedidos × Ticket médio
  └── ROAS bruto        | valor | fórmula: Faturamento ÷ Verba
[Card: Diário]
  ├── Investimento diário  | valor | fórmula: Verba ÷ 30
  ├── Visitas diárias      | valor | fórmula: Visitas ÷ 30
  ├── Pedidos diários      | valor | fórmula: Pedidos ÷ 30
  └── Faturamento diário   | valor | fórmula: Faturamento ÷ 30
```

### Linhas de 3 colunas (calculadas)
```css
display: grid;
grid-template-columns: 1fr 140px 220px;
```
- Coluna 1: nome da métrica (fundo `#fafbff`)
- Coluna 2: valor calculado (alinhado à direita)
- Coluna 3: fórmula em itálico, `color: #9aa3bf`, fundo `#f7f8fc`, `font-size: 11px`

### Linhas editáveis (2 colunas)
```css
display: grid;
grid-template-columns: 1fr 140px;
```
- Label fundo: `#e6f1fb`, cor: `#0c447c`
- Input:
  ```css
  type="text" inputmode="decimal"
  width: 90px; text-align: right;
  border: 1px solid #b5d4f4;
  border-radius: 6px; padding: 5px 8px;
  font-size: 13px; color: #0c447c; font-weight: 600;
  ```

### Linhas com fundo verde (Faturamento e ROAS)
```css
background: #eaf3de;
color: #3b6d11;
font-weight: 500;
```

---

## 12. Aba 8 — Meta x Realizado

### Layout
```
[Seletor de ano: 2026 | 2027]
[Legenda: Projeção | Realizado GA4 | Plataforma]
[Tabela horizontal com 12 meses]
```

### Seletor de ano
```css
/* Botão ativo */
background: #1a1a2e; color: #fff; border-color: #1a1a2e;
/* Botão inativo */
background: #fff; color: #6b7591; border-color: #d0d5e0;
padding: 5px 14px; border-radius: 6px; font-size: 12px;
```

### Estrutura das colunas por mês
- **Colapsado:** mostra só 1 coluna (Projeção) com o nome do mês no cabeçalho
- **Expandido:** mostra 5 colunas: Projeção | Realizado | %Δ | Plataforma | %Δ
- Clique no nome do mês: expande/colapsa
- Ícone ▶ no cabeçalho, rotaciona quando expandido

### Cores das sub-colunas (cabeçalho)
| Sub-coluna | Cor fundo |
|---|---|
| Projeção | `#5f5e5a` |
| Realizado | `#1e5631` |
| %Δ Realizado | `#1e5631` com `opacity: 0.85` |
| Plataforma | `#0c447c` |
| %Δ Plataforma | `#0c447c` com `opacity: 0.85` |

### Cores das células
| Sub-coluna | Cor fundo |
|---|---|
| Projeção | `#fff` (branco) |
| Realizado | `#e8f5e9` (verde claro) |
| %Δ | mesmo fundo da coluna ao lado |
| Plataforma | `#e3f2fd` (azul claro) |

### %Δ (diferença)
```
▼ X.X%  →  color: #d03b3b (falta atingir a projeção)
▲ X.X%  →  color: #0ca30c (superou a projeção)
font-size: 10px; font-weight: 500;
```

### Campos editáveis — Projeção (6 campos)
- Receita, Investimento Meta Ads, Investimento Google Ads, Sessões, CPS Mídia, Transações
- Input: `type="text" inputmode="decimal"`, borda `#d0d5e0`, fundo `#fff`

### Campos calculados — Projeção
- Investimento total = Meta + Google
- % Meta = Meta ÷ Total
- % Google = Google ÷ Total
- CPS Geral = Total ÷ Sessões
- Taxa de Conversão = Transações ÷ Sessões
- Ticket Médio = Receita ÷ Transações
- ROAS = Receita ÷ Investimento total

### Campos editáveis — Plataforma (2 campos)
- Receita, Transações

### Campos derivados — Plataforma (usando GA4 como base)
- Sessões → copia do GA4
- Investimento Meta/Google/Total → copia do GA4
- % Meta/Google → copia do GA4
- CPS Geral → copia do GA4
- Taxa de Conversão → Transações(Plat) ÷ Sessões(GA4)
- Ticket Médio → Receita(Plat) ÷ Transações(Plat)
- ROAS → Receita(Plat) ÷ Investimento(GA4)

### Coluna de métricas (sticky left)
```css
position: sticky; left: 0; z-index: 2;
background: #fff; color: #185fa5; font-weight: 500;
min-width: 190px; border-right: 1px solid #eceef3;
```

---

## 13. Comportamentos Globais

### Sticky em tabelas com scroll interno
```css
/* Coluna esquerda */
position: sticky; left: 0; z-index: 2; background: #fff;

/* Cabeçalho */
position: sticky; top: 0; z-index: 3; background: #1a1a2e;

/* Coluna direita (Acumulado) */
position: sticky; right: 0; z-index: 2;
```

### Scroll interno (container fixo)
```css
overflow-x: auto;
overflow-y: auto;
max-height: calc(100vh - 240px); /* ajusta por aba */
```
A página NÃO rola — só o conteúdo dentro do container rola.

### Dropdowns com panel flutuante
```css
position: absolute;
top: calc(100% + 4px);
left: 0;
background: #fff;
border: 1px solid #d0d5e0;
border-radius: 6px;
padding: 8px;
z-index: 100;
box-shadow: 0 4px 16px rgba(0,0,0,0.12);
min-width: 200px;
```

### Inputs de número (sem type="number")
- Usar `type="text" inputmode="decimal"` para controle de cursor
- Parser: aceita vírgula como separador decimal
- Formatar com vírgula na exibição: `toFixed(2).replace('.', ',')`

---

## 14. Dados e Fontes

### Fontes de dados por aba
| Aba | Fonte principal |
|---|---|
| Acompanhamento de Resultado | GA4 (receita) + Meta/Google/TikTok APIs (investimento) |
| Visão Geral | GA4 |
| UTM | GA4 (traffic_source.*) |
| Taxa de Conversão | GA4 (view_item + purchase por item_name) |
| Curva ABC / Matriz BCG | GA4 (derivado da Taxa de Conversão) |
| Regiões | GA4 (geo.region + geo.city) + Meta API (breakdowns=region) + Google Ads (geographic_view) |
| Simulação | Matemática pura, sem API |
| Meta x Realizado | Projeção manual + GA4 (Realizado) + Plataforma de ecommerce (manual) |

### Identificação de canais por UTM
| Canal | utm_source | utm_medium |
|---|---|---|
| Facebook | facebook | cpc |
| Google | google | cpc |
| TikTok | tiktok | cpc |
| Email | email | email |
| Direct | (direct) | (none) |
| SEO | qualquer | organic |
| Sacolinha IG | IGShopping | IGShopping |
| Instagram | ig, instagram, l.instagram.com | qualquer |
| WhatsApp | whatsapp | whatsapp |

### Pipeline de dados (Worker Cloudflare)
- Roda às 06h todo dia (D-1)
- Busca Meta Ads API → upsert BigQuery `midia_diaria` + `midia_regiao_diaria`
- Busca Google Ads API → upsert BigQuery `midia_diaria` + `midia_regiao_diaria`
- Busca TikTok Ads API → upsert BigQuery `midia_diaria`
- Consulta views do BigQuery → gera JSONs
- Serve via endpoints REST para o dashboard

### Variáveis de ambiente (nunca no código)
```
META_TOKEN
GOOGLE_ADS_DEVELOPER_TOKEN
GOOGLE_CLIENT_ID
GOOGLE_REFRESH_TOKEN
BIGQUERY_PROJECT_ID
```

---

## 15. Prompt Padrão para Nova Sessão

Use este prompt ao iniciar uma nova sessão com este projeto:

```
Tenho um dashboard de ecommerce em HTML com 8 abas já construídas.
Vou anexar dois arquivos:
1. dashboard_ecommerce.html — o projeto completo com dados de demonstração
2. dashboard_design_spec.md — especificação visual e funcional completa

Leia os dois arquivos antes de fazer qualquer coisa.
NÃO altere nada que já existe no projeto.
NÃO refaça nenhuma aba do zero.
Mantenha exatamente as mesmas cores, fontes, comportamentos e estrutura.

O que quero fazer: [DESCREVA AQUI]
```
