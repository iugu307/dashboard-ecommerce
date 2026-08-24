# Dashboard Ecommerce

## Acesso
- **URL:** arquivo `dashboard_ecommerce.html` hospedado no Cloudflare Pages
- **Sem autenticação** — abre direto no dashboard

---

## Estrutura das Abas

### Aba 1 — Acompanhamento de Resultado
- Seletor de ano + meses (multi-seleção, não fecha ao selecionar)
- Cabeçalho de meses fixo (sticky) ao rolar horizontalmente
- Coluna Acumulado fixa à direita
- Canais colapsáveis verticalmente (clique no cabeçalho do canal)
- Meses expansíveis horizontalmente (clique no mês → abre colunas de dias)

**Grupos de métricas (linhas) × Meses (colunas):**

#### GERAL
| Métrica | Definição |
|---|---|
| Investimento total | Soma Meta + Google + TikTok (só canais com dados no período) |
| Receita captada | SUM(purchase_revenue) — GA4 |
| ROAS captado | Receita captada ÷ Investimento total |
| Taxa de conversão | Transações ÷ Sessões totais |
| Transações | COUNT(purchase events) — GA4 |
| Ticket médio | Receita captada ÷ Transações |
| Sessões (geral) | Todas as sessões — GA4 |
| CPS (geral) | Investimento total ÷ Sessões totais |
| Sessões mídia | Sessões com utm_source IN ('facebook','google','tiktok') |
| CPS (mídia) | Investimento total ÷ Sessões mídia |
| % sessões mídia | Sessões mídia ÷ Sessões totais |

#### FACEBOOK
| Métrica | Definição |
|---|---|
| Investimento Meta Ads | API Meta Ads |
| Receita | GA4 filtrado: utm_source = 'facebook' |
| % receita geral | Receita Facebook ÷ Receita total GA4 |
| ROAS | Receita Facebook ÷ Investimento Meta |
| Taxa de conversão (M) | Transações Facebook ÷ Sessões Facebook |
| Transações (M) | COUNT purchase — GA4 filtrado utm_source = 'facebook' |
| Ticket médio | Receita Facebook ÷ Transações Facebook |
| Sessões mídia | Sessões GA4 com utm_source = 'facebook' |
| CPS | Investimento Meta ÷ Sessões Facebook |
| % sessões mídia | Sessões Facebook ÷ Sessões totais |

#### GOOGLE
| Métrica | Definição |
|---|---|
| Investimento Google Ads | API Google Ads |
| Receita | GA4 filtrado: utm_source = 'google' |
| % receita geral | Receita Google ÷ Receita total GA4 |
| ROAS | Receita Google ÷ Investimento Google |
| Taxa de conversão (G) | Transações Google ÷ Sessões Google |
| Transações (G) | COUNT purchase — GA4 filtrado utm_source = 'google' |
| Ticket médio | Receita Google ÷ Transações Google |
| Sessões mídia | Sessões GA4 com utm_source = 'google' |
| CPS | Investimento Google ÷ Sessões Google |
| % sessões mídia | Sessões Google ÷ Sessões totais |

#### TIKTOK
| Métrica | Definição |
|---|---|
| Investimento | API TikTok Ads (quando ativo) |
| Receita | GA4 filtrado: utm_source = 'tiktok' |
| % receita geral | Receita TikTok ÷ Receita total GA4 |
| ROAS | Receita TikTok ÷ Investimento TikTok |
| Taxa de conversão (T) | Transações TikTok ÷ Sessões TikTok |
| Transações (T) | COUNT purchase — GA4 filtrado utm_source = 'tiktok' |
| Ticket médio | Receita TikTok ÷ Transações TikTok |
| Sessões mídia | Sessões GA4 com utm_source = 'tiktok' |
| CPS | Investimento TikTok ÷ Sessões TikTok |
| % sessões mídia | Sessões TikTok ÷ Sessões totais |

> **Regra:** quando canal sem investimento no período → exibe `—` em ROAS, CPS e métricas dependentes. Investimento total só soma canais com dados.

#### E-MAIL MARKETING
| Métrica | Filtro GA4 |
|---|---|
| Receita | utm_medium = 'email' OR utm_source = 'email' |
| % receita geral | Receita canal ÷ Receita total |
| Taxa de conversão | Transações canal ÷ Sessões canal |
| Transações (E) | COUNT purchase filtrado |
| Ticket médio | Receita ÷ Transações |
| Sessões orgânica | Sessões do canal |
| % sessões geral | Sessões canal ÷ Sessões totais |

#### DIRECT
| Métrica | Filtro GA4 |
|---|---|
| Receita | utm_medium = '(none)' AND utm_source = '(direct)' |
| (demais métricas) | idem padrão orgânico |

#### ORGANIC SEO
| Métrica | Filtro GA4 |
|---|---|
| Receita | utm_medium = 'organic' |
| (demais métricas) | idem padrão orgânico |

#### SACOLINHA IG
| Métrica | Filtro GA4 |
|---|---|
| Receita | utm_medium = 'IGShopping' OR utm_source = 'IGShopping' |
| (demais métricas) | idem padrão orgânico |

#### INSTAGRAM / REFERRAL
| Métrica | Filtro GA4 |
|---|---|
| Receita | utm_source IN ('ig', 'l.instagram.com', 'instagram') |
| (demais métricas) | idem padrão orgânico |

#### WHATSAPP
| Métrica | Filtro GA4 |
|---|---|
| Receita | utm_source = 'whatsapp' OR utm_medium = 'whatsapp' |
| (demais métricas) | idem padrão orgânico |

---

### Aba 2 — Meta Ads (em desenvolvimento)
- Quadros em cascata: Campanhas → Conjuntos → Criativos
- Clique filtra os quadros abaixo
- Colunas: Investimento · Alcance · Impressões · Freq. · CPM · CPC · CTR · Receita GA4 · ROAS · Transações · Ticket médio

### Aba 3 — Google Ads (em desenvolvimento)
- Quadros em cascata: Campanhas → Grupos → Termos de pesquisa
- Colunas: Investimento · Impressões · CPM · CPC · CTR · Receita GA4 · ROAS · Transações · Ticket médio

### Aba 4 — TikTok Ads (em desenvolvimento)
- Ativada quando houver investimento cadastrado

---

## Padrão de UTMs

| Canal | utm_source | utm_medium |
|---|---|---|
| Meta Ads | facebook | cpc |
| Google Ads | google | cpc |
| TikTok Ads | tiktok | cpc |
| E-mail | email | email |
| Instagram orgânico | ig / instagram / l.instagram.com | (referral) |
| Sacolinha IG | IGShopping | IGShopping |
| WhatsApp | whatsapp | whatsapp |
| Direct | (direct) | (none) |
| SEO | (various) | organic |

**CRÍTICO:** Instagram orgânico NÃO é mídia paga — utm_source instagram sem utm_medium = cpc não entra no bloco Facebook nem em Sessões Mídia.

---

## Definições do Funil

| Métrica | Definição |
|---|---|
| Sessão | session_start event — GA4 |
| Transação | purchase event — GA4 |
| Receita | purchase_revenue — GA4 (fonte única de verdade) |
| Sessão mídia | utm_source IN ('facebook','google','tiktok') |
| Sessão orgânica | tudo que não é mídia paga |
| ROAS | Receita GA4 ÷ Investimento API (não usa receita da plataforma) |
| CPS | Investimento ÷ Sessões do canal |
| Taxa de conversão | Transações ÷ Sessões (do mesmo canal ou total) |
| Ticket médio | Receita ÷ Transações |

---

## Regras de Negócio

- Receita vem **sempre do GA4** — nunca da API do Meta/Google/TikTok (evita discrepância de atribuição)
- Investimento vem **sempre da API de mídia** de cada canal
- ROAS, CPS e métricas de custo calculados apenas sobre canais **com investimento no período**
- Canal sem investimento exibe `—` nas métricas de custo, não zero
- Pipeline D-1: roda às 06h, busca dados até ontem
- Mês atual sempre parcial — sem indicador visual

---

## Arquitetura de Infraestrutura

| Serviço | Uso | Custo |
|---|---|---|
| BigQuery (Google) | GA4 (exportação nativa) + dados de mídia Meta/Google/TikTok | Gratuito (10GB storage + 1TB queries/mês) |
| Cloudflare Pages | Frontend (dashboard_ecommerce.html) | Gratuito |
| Cloudflare Workers | Pipeline diário às 06h + API para o dashboard | Gratuito |

### Volume estimado em 3 anos
- **GA4 eventos:** ~50k eventos/mês → ~1,8M registros → ~2GB (BigQuery)
- **Mídia diária:** ~2.000 combinações/dia Meta + ~3.000 Google + ~1.000 TikTok → ~6M linhas/ano → ~3GB (BigQuery, dentro do free tier)

---

## Tabelas do Banco de Dados (BigQuery)

```sql
-- Exportação nativa GA4 → BigQuery
-- Tabela gerada automaticamente pelo Google:
-- `projeto.analytics_XXXXXXX.events_YYYYMMDD`
-- Campos relevantes:
--   event_name              → 'purchase', 'session_start'
--   event_date              → data do evento
--   ecommerce.purchase_revenue → receita
--   ecommerce.transaction_id   → id da transação
--   traffic_source.source   → utm_source
--   traffic_source.medium   → utm_medium
--   traffic_source.campaign → utm_campaign

-- Tabela de mídia paga (pipeline Cloudflare Worker)
CREATE TABLE IF NOT EXISTS `projeto.ecommerce.midia_diaria` (
  data DATE,
  canal STRING,           -- 'meta', 'google', 'tiktok'
  campanha_id STRING,
  campanha_nome STRING,
  conjunto_id STRING,
  conjunto_nome STRING,
  criativo_id STRING,
  criativo_nome STRING,
  spend NUMERIC,
  impressoes INT64,
  alcance INT64,
  cliques INT64,
  cpm NUMERIC,
  cpc NUMERIC,
  ctr NUMERIC,
  termo_pesquisa STRING   -- Google Ads only
);
```

---

## Queries Principais

### Receita e sessões por canal (GA4)
```sql
SELECT
  CASE
    WHEN traffic_source.source = 'facebook'  THEN 'facebook'
    WHEN traffic_source.source = 'google'    THEN 'google'
    WHEN traffic_source.source = 'tiktok'    THEN 'tiktok'
    WHEN traffic_source.medium = 'email'
      OR traffic_source.source = 'email'     THEN 'email'
    WHEN traffic_source.medium = 'organic'   THEN 'seo'
    WHEN traffic_source.medium = 'IGShopping'
      OR traffic_source.source = 'IGShopping' THEN 'sacolinha'
    WHEN traffic_source.source IN ('ig','instagram','l.instagram.com') THEN 'instagram'
    WHEN traffic_source.source = 'whatsapp'
      OR traffic_source.medium = 'whatsapp'  THEN 'whatsapp'
    WHEN traffic_source.source = '(direct)'  THEN 'direct'
    ELSE 'outros'
  END AS canal,
  DATE(PARSE_TIMESTAMP('%Y%m%d', event_date)) AS data,
  SUM(IF(event_name = 'purchase', ecommerce.purchase_revenue, 0)) AS receita,
  COUNT(IF(event_name = 'purchase', ecommerce.transaction_id, NULL)) AS transacoes,
  COUNT(DISTINCT IF(event_name = 'session_start', user_pseudo_id, NULL)) AS sessoes
FROM `projeto.analytics_XXXXXXX.events_*`
WHERE _TABLE_SUFFIX BETWEEN '20250101' AND '20250131'
GROUP BY canal, data
ORDER BY data, canal;
```

### Investimento por canal e dia (mídia)
```sql
SELECT
  data,
  canal,
  SUM(spend) AS investimento,
  SUM(impressoes) AS impressoes,
  SUM(cliques) AS cliques
FROM `projeto.ecommerce.midia_diaria`
WHERE data BETWEEN '2025-01-01' AND '2025-01-31'
GROUP BY data, canal
ORDER BY data, canal;
```

### View consolidada (GA4 + mídia)
```sql
CREATE OR REPLACE VIEW `projeto.ecommerce.v_consolidado_diario` AS
WITH ga4 AS (
  SELECT
    CASE
      WHEN traffic_source.source = 'facebook'   THEN 'facebook'
      WHEN traffic_source.source = 'google'     THEN 'google'
      WHEN traffic_source.source = 'tiktok'     THEN 'tiktok'
      WHEN traffic_source.medium = 'email'
        OR traffic_source.source = 'email'      THEN 'email'
      WHEN traffic_source.medium = 'organic'    THEN 'seo'
      WHEN traffic_source.medium = 'IGShopping'
        OR traffic_source.source = 'IGShopping' THEN 'sacolinha'
      WHEN traffic_source.source IN ('ig','instagram','l.instagram.com') THEN 'instagram'
      WHEN traffic_source.source = 'whatsapp'
        OR traffic_source.medium = 'whatsapp'   THEN 'whatsapp'
      WHEN traffic_source.source = '(direct)'   THEN 'direct'
      ELSE 'outros'
    END AS canal,
    DATE(PARSE_TIMESTAMP('%Y%m%d', event_date)) AS data,
    SUM(IF(event_name = 'purchase', ecommerce.purchase_revenue, 0)) AS receita,
    COUNT(IF(event_name = 'purchase', ecommerce.transaction_id, NULL)) AS transacoes,
    COUNT(DISTINCT IF(event_name = 'session_start', user_pseudo_id, NULL)) AS sessoes
  FROM `projeto.analytics_XXXXXXX.events_*`
  WHERE _TABLE_SUFFIX >= '20250101'
  GROUP BY canal, data
),
midia AS (
  SELECT data, canal, SUM(spend) AS investimento
  FROM `projeto.ecommerce.midia_diaria`
  GROUP BY data, canal
)
SELECT
  g.data,
  g.canal,
  g.receita,
  g.transacoes,
  g.sessoes,
  COALESCE(m.investimento, 0) AS investimento,
  SAFE_DIVIDE(g.receita, m.investimento) AS roas,
  SAFE_DIVIDE(g.transacoes, g.sessoes) AS taxa_conversao,
  SAFE_DIVIDE(g.receita, g.transacoes) AS ticket_medio,
  SAFE_DIVIDE(m.investimento, g.sessoes) AS cps
FROM ga4 g
LEFT JOIN midia m ON g.data = m.data AND g.canal = m.canal;
```

---

## Pipeline Diário

```
06:00 todo dia (Cloudflare Worker):
1. Consulta Meta Ads API   → upsert em midia_diaria (data = ontem, canal = 'meta')
2. Consulta Google Ads API → upsert em midia_diaria (data = ontem, canal = 'google')
3. Consulta TikTok Ads API → upsert em midia_diaria (data = ontem, canal = 'tiktok')
4. Consulta BigQuery (v_consolidado_diario) → agrega por mês/canal
5. Gera JSON para o frontend → salva no Cloudflare KV ou R2
```

### Formato do JSON de saída
```json
[
  {
    "data": "2025-01-01",
    "canal": "facebook",
    "receita": 1820.00,
    "transacoes": 27,
    "sessoes": 1100,
    "investimento": 302.00,
    "roas": 6.02,
    "taxa_conversao": 0.0245,
    "ticket_medio": 67.41,
    "cps": 0.27
  }
]
```

---

## Integrações de API

### GA4 → BigQuery
- Integração nativa: ativar em GA4 → Admin → Exportação para BigQuery
- Dados chegam diariamente sem pipeline customizado
- Tabelas no formato `events_YYYYMMDD` (uma por dia)

### Meta Ads
- Marketing API endpoint: `/{ad-account-id}/insights`
- System User Token (não expira)
- Campos: `spend, reach, impressions, clicks, cpm, cpc, ctr`
- Breakdown: `campaign_id, adset_id, ad_id, date_start`
- Filtro de atribuição: mesmo período do GA4 (evitar discrepância)

### Google Ads
- Google Ads API (não GA4)
- GAQL nos recursos `campaign`, `ad_group` e `search_term_view`
- Developer token + customer ID necessários

### TikTok Ads
- TikTok Marketing API endpoint: `/open_api/v1.3/report/integrated/get/`
- Campos: `spend, impressions, clicks, cpm, cpc, ctr`
- Breakdown: `campaign_id, adgroup_id, ad_id`
- Ativar quando canal for ao ar

---

## Pendências para Produção

| Item | Status |
|---|---|
| Ativar exportação GA4 → BigQuery | ⏳ Pendente |
| Criar tabela `midia_diaria` no BigQuery | ⏳ Pendente |
| Criar view `v_consolidado_diario` no BigQuery | ⏳ Pendente |
| Auditoria UTMs nas campanhas ativas (Meta + Google) | ⏳ Pendente |
| System User Token Meta Ads | ⏳ Criar |
| Developer token + customer ID Google Ads | ⏳ Criar |
| Implementar pipeline Cloudflare Worker | ⏳ Pendente |
| Hospedar dashboard no Cloudflare Pages | ⏳ Pendente |
| Definir abas Meta Ads e Google Ads (drill-down) | ⏳ Em discussão |
| Implementar TikTok Ads API | ⏳ Quando canal ativo |

---

## Aba 2 — Visão Geral

### Fonte de dados
Tudo vem do GA4 via BigQuery. Endpoint separado do Worker:
- **Aba 1:** `/ecommerce/acompanhamento` → dados diários por canal
- **Aba 2:** `/ecommerce/visao-geral` → KPIs, produtos, estados, dispositivos, pesquisa

### Filtro de período
- Atalhos rápidos: 7 dias, 14 dias, 30 dias
- Personalizado: seletor de data início → fim
- Comparação: período anterior (automático) ou personalizado

### Blocos e métricas

#### KPIs principais (8 cards com ▲▼ vs período anterior)
| Métrica | Campo GA4 | Evento/Dimensão |
|---|---|---|
| Receita total | `ecommerce.purchase_revenue` | event_name = 'purchase' |
| Pedidos | `ecommerce.transaction_id` | COUNT DISTINCT |
| Ticket médio | Receita ÷ Pedidos | calculado |
| Taxa de conversão | Transações ÷ Sessões | calculado |
| Sessões | `session_start` | COUNT |
| Usuários | `user_pseudo_id` | COUNT DISTINCT |
| Sessões engajadas | `session_engaged = '1'` | COUNT |
| Taxa de engajamento | Sessões engajadas ÷ Sessões | calculado |

#### Categorias mais vendidas
| Coluna | Campo GA4 |
|---|---|
| Categoria | `items.item_category` |
| Itens comprados | `items.quantity` SUM |
| Receita | `items.price * items.quantity` SUM |

#### Produtos mais vendidos
| Coluna | Campo GA4 |
|---|---|
| Produto | `items.item_name` |
| Itens comprados | `items.quantity` SUM |
| Receita | `items.price * items.quantity` SUM |

#### Vendas por dispositivo
| Coluna | Campo GA4 |
|---|---|
| Dispositivo | `device.category` (mobile/desktop/tablet) |
| Sessões | COUNT session_start |
| Receita total | SUM purchase_revenue |

#### Vendas por estado
| Coluna | Campo GA4 |
|---|---|
| Estado | `geo.region` |
| Taxa de conversão | Transações ÷ Sessões por região |
| Receita total | SUM purchase_revenue por região |

#### Pesquisa interna
| Coluna | Campo GA4 |
|---|---|
| Termo de pesquisa | `event_params.value` onde `event_params.key = 'search_term'` |
| Sessões | COUNT sessões com o termo |
| % variação | vs período anterior |

> **Pré-requisito:** evento `search` configurado no GA4 com parâmetro `search_term`

---

### Queries BigQuery — Aba 2

#### KPIs do período
```sql
WITH periodo AS (
  SELECT
    SUM(ecommerce.purchase_revenue)                              AS receita,
    COUNT(DISTINCT ecommerce.transaction_id)                     AS pedidos,
    COUNT(DISTINCT IF(event_name='session_start', user_pseudo_id||CAST(event_timestamp AS STRING), NULL)) AS sessoes,
    COUNT(DISTINCT user_pseudo_id)                               AS usuarios,
    COUNT(DISTINCT IF(
      event_name='session_start' AND
      (SELECT value.string_value FROM UNNEST(event_params) WHERE key='session_engaged') = '1',
      user_pseudo_id||CAST(event_timestamp AS STRING), NULL))    AS sessoes_engajadas
  FROM `projeto.analytics_XXXXXXX.events_*`
  WHERE _TABLE_SUFFIX BETWEEN '20250601' AND '20250630'
)
SELECT
  receita,
  pedidos,
  SAFE_DIVIDE(receita, pedidos)           AS ticket_medio,
  SAFE_DIVIDE(pedidos, sessoes)           AS taxa_conversao,
  sessoes,
  usuarios,
  sessoes_engajadas,
  SAFE_DIVIDE(sessoes_engajadas, sessoes) AS taxa_engajamento
FROM periodo;
```

#### Produtos mais vendidos
```sql
SELECT
  item.item_name                    AS produto,
  item.item_category                AS categoria,
  SUM(item.quantity)                AS itens_comprados,
  SUM(item.item_revenue)            AS receita
FROM `projeto.analytics_XXXXXXX.events_*`,
  UNNEST(items) AS item
WHERE _TABLE_SUFFIX BETWEEN '20250601' AND '20250630'
  AND event_name = 'purchase'
GROUP BY produto, categoria
ORDER BY receita DESC
LIMIT 20;
```

#### Vendas por dispositivo
```sql
SELECT
  device.category                                               AS dispositivo,
  COUNT(DISTINCT IF(event_name='session_start',
    user_pseudo_id||CAST(event_timestamp AS STRING), NULL))     AS sessoes,
  SUM(IF(event_name='purchase', ecommerce.purchase_revenue, 0)) AS receita
FROM `projeto.analytics_XXXXXXX.events_*`
WHERE _TABLE_SUFFIX BETWEEN '20250601' AND '20250630'
GROUP BY dispositivo
ORDER BY receita DESC;
```

#### Vendas por estado
```sql
SELECT
  geo.region                                                    AS estado,
  COUNT(DISTINCT IF(event_name='session_start',
    user_pseudo_id||CAST(event_timestamp AS STRING), NULL))     AS sessoes,
  COUNT(DISTINCT IF(event_name='purchase',
    ecommerce.transaction_id, NULL))                            AS pedidos,
  SUM(IF(event_name='purchase', ecommerce.purchase_revenue, 0)) AS receita,
  SAFE_DIVIDE(
    COUNT(DISTINCT IF(event_name='purchase', ecommerce.transaction_id, NULL)),
    COUNT(DISTINCT IF(event_name='session_start',
      user_pseudo_id||CAST(event_timestamp AS STRING), NULL))
  )                                                             AS taxa_conversao
FROM `projeto.analytics_XXXXXXX.events_*`
WHERE _TABLE_SUFFIX BETWEEN '20250601' AND '20250630'
  AND geo.country = 'Brazil'
GROUP BY estado
ORDER BY receita DESC
LIMIT 20;
```

#### Pesquisa interna
```sql
SELECT
  (SELECT value.string_value FROM UNNEST(event_params)
   WHERE key = 'search_term')          AS termo,
  COUNT(DISTINCT user_pseudo_id||
    CAST(event_timestamp AS STRING))   AS sessoes
FROM `projeto.analytics_XXXXXXX.events_*`
WHERE _TABLE_SUFFIX BETWEEN '20250601' AND '20250630'
  AND event_name = 'search'
GROUP BY termo
ORDER BY sessoes DESC
LIMIT 20;
```

---

### Formato JSON — Worker Aba 2

```json
{
  "periodo": { "ini": "2025-06-01", "fim": "2025-06-30" },
  "comparacao": { "ini": "2025-05-01", "fim": "2025-05-31" },
  "kpis": {
    "receita":            { "atual": 84320.00, "anterior": 75020.00 },
    "pedidos":            { "atual": 1248,      "anterior": 1148 },
    "ticket_medio":       { "atual": 67.56,     "anterior": 65.35 },
    "taxa_conversao":     { "atual": 0.032,     "anterior": 0.033 },
    "sessoes":            { "atual": 39125,     "anterior": 36875 },
    "usuarios":           { "atual": 31240,     "anterior": 29520 },
    "sessoes_engajadas":  { "atual": 18320,     "anterior": 16760 },
    "taxa_engajamento":   { "atual": 0.468,     "anterior": 0.454 }
  },
  "produtos": [
    { "nome": "Bojo Jani Índia (M)", "categoria": "Sale", "itens": 89, "receita": 11476.00 }
  ],
  "categorias": [
    { "categoria": "Sale", "itens": 312, "receita": 21084.00 }
  ],
  "dispositivos": [
    { "dispositivo": "mobile",  "sessoes": 33256, "receita": 46376.00 },
    { "dispositivo": "desktop", "sessoes": 5619,  "receita": 37100.00 },
    { "dispositivo": "tablet",  "sessoes": 250,   "receita": 844.00 }
  ],
  "estados": [
    { "estado": "São Paulo", "sessoes": 12480, "pedidos": 512, "receita": 29512.00, "taxa_conversao": 0.041 }
  ],
  "pesquisa": [
    { "termo": "crochê", "sessoes": 312, "sessoes_anterior": 285 }
  ]
}
```

---

### Pendências Aba 2

| Item | Status |
|---|---|
| Confirmar evento `search` configurado no GA4 com parâmetro `search_term` | ⏳ Confirmar |
| Confirmar `item_category` preenchido nos eventos de purchase | ⏳ Confirmar |
| Implementar endpoint `/ecommerce/visao-geral` no Worker | ⏳ Pendente |
| Conectar `API_URL_VISAO_GERAL` no dashboard HTML | ⏳ Pendente |
| Validar `geo.region` retorna estados em português ou inglês | ⏳ Confirmar |

---

## Aba Taxa de Conversão por Produto

### Regra de agrupamento (remoção de variação/tamanho)

O GA4 registra `item_name` com o tamanho/variação geralmente entre parênteses no final (`(M)`, `(G)`, `(35)`, `(GG)`). Para agrupar todas as variações do mesmo produto base, a query remove esse padrão antes de agregar:

```sql
TRIM(REGEXP_REPLACE(item.item_name, r'\s*\([^)]*\)\s*$', '')) AS produto_base
```

**Exemplo de agrupamento:**
```
"Bojo Jani Índia Vermelho (M)"  ┐
"Bojo Jani Índia Vermelho (G)"  ├─→ "Bojo Jani Índia Vermelho"
"Bojo Jani Índia Vermelho (GG)" ┘
```

> Se o catálogo tiver variações fora do padrão de parênteses (ex: `- 35`, `Tam M` sem parênteses), a regex precisa ser expandida quando a auditoria de nomes reais for feita — por ora cobre o padrão mais comum.

### Cálculo da Taxa de Conversão por Produto

A taxa de conversão usa duas bases de sessão diferentes — sessões que **viram** o produto vs sessões que **compraram** o produto:

```sql
WITH views AS (
  SELECT
    TRIM(REGEXP_REPLACE(item.item_name, r'\s*\([^)]*\)\s*$', '')) AS produto,
    COUNT(DISTINCT CONCAT(user_pseudo_id, '-', 
      (SELECT value.int_value FROM UNNEST(event_params) WHERE key='ga_session_id')
    )) AS sessoes_com_view
  FROM `projeto.analytics_XXXXXXX.events_*`, UNNEST(items) AS item
  WHERE event_name = 'view_item'
    AND _TABLE_SUFFIX BETWEEN '20250101' AND '20250131'
  GROUP BY produto
),
compras AS (
  SELECT
    TRIM(REGEXP_REPLACE(item.item_name, r'\s*\([^)]*\)\s*$', '')) AS produto,
    SUM(item.quantity)     AS itens_vendidos,
    SUM(item.item_revenue) AS receita,
    COUNT(DISTINCT CONCAT(user_pseudo_id, '-',
      (SELECT value.int_value FROM UNNEST(event_params) WHERE key='ga_session_id')
    )) AS sessoes_com_compra
  FROM `projeto.analytics_XXXXXXX.events_*`, UNNEST(items) AS item
  WHERE event_name = 'purchase'
    AND _TABLE_SUFFIX BETWEEN '20250101' AND '20250131'
  GROUP BY produto
)
SELECT
  v.produto,
  v.sessoes_com_view                                     AS sessoes,
  COALESCE(c.itens_vendidos, 0)                          AS itens_vendidos,
  COALESCE(c.receita, 0)                                 AS receita,
  SAFE_DIVIDE(c.sessoes_com_compra, v.sessoes_com_view)  AS taxa_conversao,
  SAFE_DIVIDE(c.receita, c.itens_vendidos)               AS preco_medio
FROM views v
LEFT JOIN compras c ON v.produto = c.produto
ORDER BY receita DESC;
```

### Definição da Taxa de Conversão por Produto

| Conceito | Definição |
|---|---|
| Sessão com view | Sessão onde ocorreu `view_item` daquele produto base |
| Sessão com compra | Sessão onde ocorreu `purchase` contendo aquele produto base |
| Taxa de conversão | Sessões com compra ÷ Sessões com view |

Essa é a métrica mais precisa para produto: mede quantas sessões que **viram** o produto efetivamente **compraram** — diferente da taxa de conversão geral do e-commerce (que usa sessões totais da loja).

### Pendências
| Item | Status |
|---|---|
| Evento `view_item` configurado no GA4 com `items` populado | ✅ Confirmado |
| Auditoria de nomes de produto fora do padrão `(TAMANHO)` | ⏳ Validar quando o catálogo real estiver disponível |

---

## Aba Regiões — Investimento por Estado

### Fonte confirmada: investimento real via API (não estimativa)

Diferente do que foi inicialmente cogitado (estimativa proporcional por % de sessões), **tanto Meta Ads quanto Google Ads entregam investimento segmentado geograficamente de forma nativa**:

| Canal | Recurso da API | Granularidade |
|---|---|---|
| Meta Ads | Marketing API com `breakdowns=region` | Estado/região |
| Google Ads | `geographic_view` (Google Ads API) | Estado e cidade |

### Meta Ads — exemplo de chamada
```
GET /{ad-account-id}/insights
  ?breakdowns=region
  &fields=spend,impressions,clicks,date_start
  &time_range={"since":"2025-06-01","until":"2025-06-30"}
```

### Google Ads — exemplo GAQL
```sql
SELECT
  geographic_view.country_criterion_id,
  geographic_view.location_type,
  segments.date,
  metrics.cost_micros,
  metrics.impressions,
  metrics.clicks
FROM geographic_view
WHERE segments.date BETWEEN '2025-06-01' AND '2025-06-30'
```

> **Nota:** o `geographic_view` do Google Ads é baseado por padrão na localização **física do usuário** durante a sessão (`location_type = LOCATION_OF_PRESENCE`), o que é o comportamento correto para medir investimento por região de quem realmente está no estado.

### Nova tabela no BigQuery

```sql
CREATE TABLE IF NOT EXISTS `projeto.ecommerce.midia_regiao_diaria` (
  data DATE,
  canal STRING,        -- 'meta' ou 'google'
  estado STRING,        -- sigla UF
  spend NUMERIC,
  impressoes INT64,
  cliques INT64
);
```

### View consolidada por região (GA4 + mídia geo)

```sql
CREATE OR REPLACE VIEW `projeto.ecommerce.v_consolidado_regiao` AS
WITH ga4_regiao AS (
  SELECT
    geo.region                                                     AS estado,
    DATE(PARSE_TIMESTAMP('%Y%m%d', event_date))                    AS data,
    SUM(IF(event_name = 'purchase', ecommerce.purchase_revenue, 0)) AS receita,
    COUNT(IF(event_name = 'purchase', ecommerce.transaction_id, NULL)) AS transacoes,
    COUNT(DISTINCT IF(event_name = 'session_start',
      CONCAT(user_pseudo_id, '-', CAST(event_timestamp AS STRING)), NULL)) AS sessoes
  FROM `projeto.analytics_XXXXXXX.events_*`
  WHERE _TABLE_SUFFIX >= '20250101'
    AND geo.country = 'Brazil'
  GROUP BY estado, data
),
midia_regiao AS (
  SELECT data, estado, canal, SUM(spend) AS investimento
  FROM `projeto.ecommerce.midia_regiao_diaria`
  GROUP BY data, estado, canal
),
midia_regiao_pivot AS (
  SELECT
    data, estado,
    SUM(IF(canal='meta', investimento, 0))   AS invest_meta,
    SUM(IF(canal='google', investimento, 0)) AS invest_google
  FROM midia_regiao
  GROUP BY data, estado
)
SELECT
  g.data,
  g.estado,
  g.receita,
  g.transacoes,
  g.sessoes,
  COALESCE(m.invest_meta, 0)   AS invest_meta,
  COALESCE(m.invest_google, 0) AS invest_google,
  COALESCE(m.invest_meta,0) + COALESCE(m.invest_google,0) AS investimento_total,
  SAFE_DIVIDE(g.receita, COALESCE(m.invest_meta,0)+COALESCE(m.invest_google,0)) AS roas,
  SAFE_DIVIDE(g.transacoes, g.sessoes) AS taxa_conversao,
  SAFE_DIVIDE(COALESCE(m.invest_meta,0)+COALESCE(m.invest_google,0), g.sessoes) AS cps
FROM ga4_regiao g
LEFT JOIN midia_regiao_pivot m ON g.data = m.data AND g.estado = m.estado;
```

### Pipeline atualizado

```
06:00 todo dia:
1. Consulta Meta Ads API (breakdown=region) → upsert em midia_regiao_diaria
2. Consulta Google Ads API (geographic_view) → upsert em midia_regiao_diaria
3. Consulta BigQuery (v_consolidado_regiao) → agrega por estado/mês
4. Gera JSON para a aba Regiões
```

### Pendências atualizadas
| Item | Status |
|---|---|
| Confirmar mapeamento de `region` do Meta Ads para sigla UF | ⏳ Confirmar (Meta retorna nome completo do estado, ex: "São Paulo", precisa mapear para "SP") |
| Confirmar `location_type` do Google Ads (presence vs interest) | ⏳ Confirmar — usar presence para medir região real do comprador |
| Criar tabela `midia_regiao_diaria` no BigQuery | ⏳ Pendente |
| Criar view `v_consolidado_regiao` no BigQuery | ⏳ Pendente |
| Implementar segunda consulta geo no pipeline do Worker | ⏳ Pendente |

---

## Aba Meta x Realizado — Coluna Plataforma

### Regra final de cálculo

A coluna Plataforma representa os dados reais vindos da plataforma de ecommerce (Shopify, VTEX, etc), que podem divergir do GA4 por questões de atribuição, bloqueio de cookies ou delay de tracking.

**Campos editáveis (2):** Receita, Transações

**Campos copiados do GA4 (não recalculados, mesma fonte):** Sessões, Investimento Meta Ads, Investimento Google Ads, Investimento total, % Investimento Meta, % Investimento Google, CPS (Geral)

**Campos calculados com mistura Plataforma + GA4:**
| Métrica | Fórmula |
|---|---|
| Taxa de conversão | Transações (Plataforma) ÷ Sessões (GA4) |
| Ticket médio | Receita (Plataforma) ÷ Transações (Plataforma) |
| ROAS captado | Receita (Plataforma) ÷ Investimento total (GA4) |

### Por que essa regra

A Plataforma é a fonte mais confiável de **receita e número real de pedidos** (sem perda por bloqueio de cookies ou problemas de atribuição), mas não tem dado de sessão — sessão é conceito exclusivo de analytics. Por isso o investimento e as sessões usam sempre o GA4 como base, e só os dois campos onde a plataforma é mais confiável (receita e transações) ficam editáveis.

### Pendência
| Item | Status |
|---|---|
| Definir se Plataforma será preenchida manualmente todo mês ou conectada via API (Shopify, VTEX, etc) | ⏳ Em aberto |

---

## Aba Meta x Realizado — Seletor de Ano

### Estrutura

A aba suporta múltiplos anos com dados completamente independentes — Projeção, Realizado (GA4) e Plataforma são isolados por ano. Adicionar um novo ano é uma alteração de uma linha no array `MR_ANOS`:

```javascript
var MR_ANOS = ['2026', '2027']; // adicionar '2028' aqui quando necessário
```

O restante da lógica (geração de botões, estrutura de dados por mês, cálculos) é genérico e funciona automaticamente para qualquer ano adicionado à lista — não há valores fixos de ano hardcoded no resto do código.

### Em produção

Quando conectado ao Worker, o ideal é que a lista de anos disponíveis venha dinamicamente do backend, baseada nos anos que têm dados no GA4/BigQuery, em vez de fixa no front-end:

```json
{
  "anos_disponiveis": ["2025", "2026", "2027"],
  "dados": { ... }
}
```

Isso evita necessidade de editar o HTML toda vez que um novo ano começar — o Worker simplesmente passa a incluir o novo ano na resposta assim que houver dados.

---

## Guia de Obtenção de Credenciais — APIs

### 1. GA4 → BigQuery (vinculação nativa, não é API tradicional)

**Onde:** Google Cloud Console + GA4 Admin

1. Acesse [console.cloud.google.com](https://console.cloud.google.com) e crie um novo projeto (ou use um existente)
2. Vá em **APIs e Serviços → Biblioteca** → ative a **BigQuery API**
3. No GA4: **Admin → Vinculações do BigQuery (BigQuery Links)** → clique em Vincular
4. Selecione o projeto do Google Cloud criado no passo 1
5. Escolha a região de armazenamento dos dados (não pode ser alterada depois — escolha a mais próxima da sua operação, ex: `southamerica-east1` para Brasil)
6. Confirme — a vinculação cria automaticamente um service account com permissão `BigQuery User`

> **Atenção:** os dados podem levar até 48h para começar a aparecer no BigQuery após a vinculação. Ative isso o quanto antes, mesmo antes do resto da infraestrutura estar pronta — não há backfill de dados históricos, só a partir da data de ativação.

---

### 2. Meta Marketing API (Facebook/Instagram Ads)

**Onde:** developers.facebook.com + Business Manager

1. Acesse [developers.facebook.com](https://developers.facebook.com) → **Criar App** → tipo **Business**
2. Preencha nome do app, e-mail de contato, vincule ao Business Manager
3. Salve o **App ID** e **App Secret** gerados
4. No painel do app: **Adicionar Produtos → Marketing API**
5. No **Business Manager → Configurações de Negócios → Usuários → Usuários do Sistema (System Users)**:
   - Clique em **Adicionar**
   - Nomeie claramente (ex: "Dashboard-Ecommerce-Connector")
   - Atribua papel **Admin**
6. Com o System User selecionado, gere um **token de acesso**:
   - Marque os scopes `ads_read` e `read_insights` (suficiente para leitura de relatórios — não precisa de `ads_management` já que o dashboard não cria/edita campanhas)
   - Defina como **sem expiração** (System User tokens não expiram, diferente de tokens de usuário comum que duram 1-2h)
7. Conceda ao System User acesso à conta de anúncios (ad account) que você quer consultar

> **Importante:** tokens de usuário comum expiram em 1-2h (curta duração) ou 60 dias (longa duração). Para automação via Worker, **sempre use System User Token**, que não expira e é o padrão recomendado para produção.

**Endpoint principal para o pipeline:**
```
GET /{ad-account-id}/insights
  ?fields=spend,impressions,clicks,cpm,cpc,ctr,date_start
  &breakdowns=region
  &time_range={"since":"2025-06-01","until":"2025-06-30"}
```

---

### 3. Google Ads API

**Onde:** Google Cloud Console (OAuth) + Google Ads MCC (Developer Token) — duas peças separadas que se combinam

#### Peça 1 — Google Cloud Console (OAuth)
1. Acesse [console.cloud.google.com](https://console.cloud.google.com) → crie um projeto **dedicado** (não reaproveitar projeto vinculado a outro developer token)
2. **APIs e Serviços → Biblioteca** → ative a **Google Ads API**
3. **APIs e Serviços → Tela de consentimento OAuth**:
   - Tipo de usuário: **Externo**
   - Preencha nome do app, e-mail de suporte, domínios autorizados
   - Em escopos, adicione: `https://www.googleapis.com/auth/adwords`
4. **APIs e Serviços → Credenciais → Criar Credenciais → ID do cliente OAuth**:
   - Tipo de aplicativo: **Aplicativo para computador (Desktop)**
   - Baixe o JSON gerado — contém `client_id` e `client_secret`

#### Peça 2 — Google Ads (Developer Token)
1. Você precisa de uma **conta de gerente (MCC)** no Google Ads — crie uma gratuitamente se ainda não tiver
2. Na conta MCC: **Ferramentas e Configurações → Configuração → Centro de API (API Center)**
3. Clique em **Solicitar Token de Desenvolvedor**, preencha:
   - Uso pretendido: "Relatórios automatizados e análise de marketing interna"
4. O token aparece como **Pendente de Aprovação** com acesso nível **Teste** — funciona imediatamente só com contas de teste
5. Para acessar contas reais, solicite **Acesso Standard ou Básico** no mesmo painel

> **Atenção a prazos:** em 2026 a fila de aprovação está mais lenta que o padrão — Acesso Básico levando 14+ dias úteis (SLA oficial é 2 dias), Acesso Standard levando 4+ semanas (SLA oficial é 10 dias), por causa do volume de solicitações vindas de ferramentas de IA. **Solicite o quanto antes**, mesmo antes de terminar o resto da implementação — esse é o item que mais trava o cronograma.

#### Gerar o Refresh Token
Depois de ter `client_id` e `client_secret`, gere o refresh token uma única vez (vincula sua conta Google):
```bash
curl -s https://raw.githubusercontent.com/googleads/google-ads-python/main/examples/authentication/generate_user_credentials.py | python3 - -c=client_secret.json
```

#### Configuração final reunida
```yaml
developer_token: SEU_TOKEN_22_CARACTERES
client_id: SEU_CLIENT_ID
client_secret: SEU_CLIENT_SECRET
refresh_token: GERADO_NO_PASSO_ANTERIOR
login_customer_id: ID_DA_CONTA_MCC  # sem hífens, formato 1111111111
```

**Endpoint principal para o pipeline (GAQL):**
```sql
SELECT
  campaign.id, campaign.name, segments.date,
  metrics.cost_micros, metrics.impressions, metrics.clicks
FROM campaign
WHERE segments.date BETWEEN '2025-06-01' AND '2025-06-30'
```

```sql
-- Para investimento por região (aba Regiões)
SELECT
  geographic_view.country_criterion_id, geographic_view.location_type,
  segments.date, metrics.cost_micros, metrics.impressions, metrics.clicks
FROM geographic_view
WHERE segments.date BETWEEN '2025-06-01' AND '2025-06-30'
```

---

### Sobre o MCP (Model Context Protocol) — opcional, separado do pipeline

O MCP é uma forma de **conversar com seus dados via Claude** (perguntar "como estão minhas campanhas essa semana?" em linguagem natural) — **não substitui o Worker** do pipeline automatizado, que precisa rodar sozinho sem intervenção humana.

| Servidor | Tipo | Credenciais necessárias |
|---|---|---|
| Google Ads MCP oficial (`googleads/google-ads-mcp`) | Somente leitura, self-hosted | Mesmas 3 credenciais acima (developer token, project ID, OAuth) |
| Servidores de terceiros (Composio, Markifact, Adspirer) | Leitura e escrita, hospedados | OAuth simplificado, sem gerenciar developer token diretamente |

Se quiser usar o MCP para consultas rápidas e exploratórias dentro do Claude (além do dashboard), as mesmas credenciais do Worker servem — é só reaproveitar.

---

### Checklist de obtenção de credenciais

| Item | Onde obter | Prazo esperado |
|---|---|---|
| Vinculação GA4 → BigQuery | GA4 Admin + Google Cloud Console | Imediato (dados em até 48h) |
| Meta System User Token | Business Manager → System Users | Imediato |
| Google Ads: projeto + OAuth Client ID/Secret | Google Cloud Console | Imediato |
| Google Ads: Developer Token | MCC → API Center | 2-14+ dias úteis (Básico) ou 10 dias-4+ semanas (Standard) — **solicitar primeiro, é o gargalo** |
| Google Ads: Refresh Token | Gerado localmente com client_id/secret | Imediato após ter as credenciais OAuth |
