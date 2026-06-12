---
name: ifood-mcp
description: Skill da REST API do iFood na MCP.AI: 16 endpoints em /api/ifood. Insights da sua loja no iFood direto no chat do seu assistente de IA. Gere gráficos de vendas e repasses no tempo, ticket médio, taxas, mix de cardápio e satisfação (avaliações), tudo pela API oficial do iFood. A conexão usa o app oficial homologado, você não informa credenciais. Autentique com workspace API key (sk_live) gerada em app.mcp.ai/settings/api-keys. Use quando o usuário pedir algo coberto pelos endpoints.
---

# iFood — REST API skill

Você tem acesso à **iFood** REST API na MCP.AI.

> Insights da sua loja no iFood direto no chat do seu assistente de IA. Gere gráficos de vendas e repasses no tempo, ticket médio, taxas, mix de cardápio e satisfação (avaliações), tudo pela API oficial do iFood. A conexão usa o app oficial homologado, você não informa credenciais.

## Base URL

```
https://api.mcp.ai/api/ifood
```

Todo endpoint é um **POST** na Base URL + o path abaixo. Os parâmetros vão no corpo JSON.

## Autenticação

Inclua em toda request:

```
Authorization: Bearer sk_live_...
Content-Type: application/json
```

> Gere sua chave em **https://app.mcp.ai/settings/api-keys** (workspace API key `sk_live_…`, não expira, revogável). Uma única chave serve pra todos os seus MCPs.

## Formato de resposta

```json
{ "ok": true, "tool": "<tool_id>", "result": <payload> }
```

## Exemplo cURL

```bash
curl -X POST https://api.mcp.ai/api/ifood/catalog/summary \
  -H "Authorization: Bearer sk_live_..." \
  -H "Content-Type: application/json" \
  -d '{}'
```

## Reportar problemas

Se um endpoint retornar erro, vazio ou dado inesperado, reporte (não desista calado): **POST /api/ifood/report** com `{ "message": "...", "context"?: "...", "conversation"?: [...] }`. Isso notifica o time da MCP.AI.

## Endpoints (16)

#### `ifood_catalog_summary`

Resumo do cardápio (chart-ready): totais (catálogos, categorias, itens, disponíveis/indisponíveis), faixa de preço (min/médio/máx) e mix por categoria (by_category). _(POST /api/ifood/catalog/summary)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `merchant_id` | string | Não | ID da loja (merchant). Opcional, por padrão usa a loja da conexão (`account`). |
| `account` | string | Não | Quando o install tem mais de uma loja iFood: merchant_id, label, ou parcial. Ver ifood_list_accounts. Omita se só houver uma. |
| `merchant_ids` | string[] | Não | Bulk mode: multiple values for merchant_id |

#### `ifood_financial_summary`

Resumo financeiro agregado do período (chart-ready): total de pedidos, faturamento bruto, ticket médio, série diária (by_day), por forma de pagamento (by_payment_method) e repasses. _(POST /api/ifood/financial/summary)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `start_date` | string | Não | Início YYYY-MM-DD (inclusive). Default: 30 dias atrás. |
| `end_date` | string | Não | Fim YYYY-MM-DD (inclusive, <= hoje). Default: hoje. |
| `account` | string | Não | Quando o install tem mais de uma loja iFood: merchant_id, label, ou parcial. Ver ifood_list_accounts. Omita se só houver uma. |

#### `ifood_get_merchant`

Detalhe da loja: nome, razão social, endereço, ticket médio, tipo, status, canais. _(POST /api/ifood/get/merchant)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `merchant_id` | string | Não | ID da loja (merchant). Opcional, por padrão usa a loja da conexão (`account`). |
| `account` | string | Não | Quando o install tem mais de uma loja iFood: merchant_id, label, ou parcial. Ver ifood_list_accounts. Omita se só houver uma. |
| `merchant_ids` | string[] | Não | Bulk mode: multiple values for merchant_id |

#### `ifood_get_opening_hours`

Horários de funcionamento da loja (shifts por dia: dayOfWeek, start, duration em minutos). _(POST /api/ifood/get/opening/hours)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `merchant_id` | string | Não | ID da loja (merchant). Opcional, por padrão usa a loja da conexão (`account`). |
| `account` | string | Não | Quando o install tem mais de uma loja iFood: merchant_id, label, ou parcial. Ver ifood_list_accounts. Omita se só houver uma. |
| `merchant_ids` | string[] | Não | Bulk mode: multiple values for merchant_id |

#### `ifood_get_reconciliation`

Conciliação financeira de uma competência (YYYY-MM): links dos arquivos detalhados (CSV) com o financeiro completo por pedido. _(POST /api/ifood/get/reconciliation)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `competence` | string | Sim | Competência no formato YYYY-MM (ex.: 2026-05) |
| `account` | string | Não | Quando o install tem mais de uma loja iFood: merchant_id, label, ou parcial. Ver ifood_list_accounts. Omita se só houver uma. |

#### `ifood_get_status`

Status operacional da loja em tempo real (aberta/fechada, available, motivos). _(POST /api/ifood/get/status)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `merchant_id` | string | Não | ID da loja (merchant). Opcional, por padrão usa a loja da conexão (`account`). |
| `account` | string | Não | Quando o install tem mais de uma loja iFood: merchant_id, label, ou parcial. Ver ifood_list_accounts. Omita se só houver uma. |
| `merchant_ids` | string[] | Não | Bulk mode: multiple values for merchant_id |

#### `ifood_list_accounts`

Lista as lojas iFood (conexões) vinculadas a este install — merchant_id, label. _(POST /api/ifood/list/accounts)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando o install tem mais de uma loja iFood: merchant_id, label, ou parcial. Ver ifood_list_accounts. Omita se só houver uma. |

#### `ifood_list_anticipations`

Antecipações de recebíveis no período (se a loja contratou antecipação no iFood). _(POST /api/ifood/list/anticipations)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `start_date` | string | Não | Início YYYY-MM-DD |
| `end_date` | string | Não | Fim YYYY-MM-DD |
| `account` | string | Não | Quando o install tem mais de uma loja iFood: merchant_id, label, ou parcial. Ver ifood_list_accounts. Omita se só houver uma. |

#### `ifood_list_catalogs`

Lista os catálogos (cardápios) da loja — catalogId, groupId, status. _(POST /api/ifood/list/catalogs)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `merchant_id` | string | Não | ID da loja (merchant). Opcional, por padrão usa a loja da conexão (`account`). |
| `account` | string | Não | Quando o install tem mais de uma loja iFood: merchant_id, label, ou parcial. Ver ifood_list_accounts. Omita se só houver uma. |
| `merchant_ids` | string[] | Não | Bulk mode: multiple values for merchant_id |

#### `ifood_list_categories`

Categorias de um catálogo (com itens por padrão): id, nome, status, itens (nome, preço, disponibilidade). _(POST /api/ifood/list/categories)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `merchant_id` | string | Não | ID da loja (merchant). Opcional, por padrão usa a loja da conexão (`account`). |
| `catalog_id` | string | Sim | catalogId (de ifood_list_catalogs) |
| `include_items` | boolean | Não | Incluir os itens (default true) |
| `account` | string | Não | Quando o install tem mais de uma loja iFood: merchant_id, label, ou parcial. Ver ifood_list_accounts. Omita se só houver uma. |
| `merchant_ids` | string[] | Não | Bulk mode: multiple values for merchant_id |
| `catalog_ids` | string[] | Não | Bulk mode: multiple values for catalog_id |

#### `ifood_list_interruptions`

Lista as pausas (interruptions) ativas/agendadas da loja. _(POST /api/ifood/list/interruptions)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `merchant_id` | string | Não | ID da loja (merchant). Opcional, por padrão usa a loja da conexão (`account`). |
| `account` | string | Não | Quando o install tem mais de uma loja iFood: merchant_id, label, ou parcial. Ver ifood_list_accounts. Omita se só houver uma. |
| `merchant_ids` | string[] | Não | Bulk mode: multiple values for merchant_id |

#### `ifood_list_merchants`

Lista as lojas visíveis à conexão (id, nome, razão social). _(POST /api/ifood/list/merchants)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `page` | integer | Não |  |
| `size` | integer | Não |  |
| `account` | string | Não | Quando o install tem mais de uma loja iFood: merchant_id, label, ou parcial. Ver ifood_list_accounts. Omita se só houver uma. |

#### `ifood_list_reviews`

Lista avaliações individuais (nota, comentário, data) paginadas — pra histograma de notas ou ler comentários recentes. _(POST /api/ifood/list/reviews)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `merchant_id` | string | Não | ID da loja (merchant). Opcional, por padrão usa a loja da conexão (`account`). |
| `page` | integer | Não | Página (default 1) |
| `size` | integer | Não | Itens por página (default 10, máx 50) |
| `account` | string | Não | Quando o install tem mais de uma loja iFood: merchant_id, label, ou parcial. Ver ifood_list_accounts. Omita se só houver uma. |
| `merchant_ids` | string[] | Não | Bulk mode: multiple values for merchant_id |

#### `ifood_list_sales`

Lista crua de vendas/pedidos do período (forma de pagamento, valores, taxas) pra análise detalhada. _(POST /api/ifood/list/sales)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `start_date` | string | Não | Início YYYY-MM-DD |
| `end_date` | string | Não | Fim YYYY-MM-DD (<= hoje) |
| `account` | string | Não | Quando o install tem mais de uma loja iFood: merchant_id, label, ou parcial. Ver ifood_list_accounts. Omita se só houver uma. |

#### `ifood_list_settlements`

Repasses (settlements) recebidos no período — valor líquido transferido, saldo. _(POST /api/ifood/list/settlements)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `start_date` | string | Não | Início YYYY-MM-DD |
| `end_date` | string | Não | Fim YYYY-MM-DD |
| `account` | string | Não | Quando o install tem mais de uma loja iFood: merchant_id, label, ou parcial. Ver ifood_list_accounts. Omita se só houver uma. |

#### `ifood_reviews_summary`

Resumo das avaliações da loja: nota agregada (score) e contagem total/válidas. _(POST /api/ifood/reviews/summary)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `merchant_id` | string | Não | ID da loja (merchant). Opcional, por padrão usa a loja da conexão (`account`). |
| `account` | string | Não | Quando o install tem mais de uma loja iFood: merchant_id, label, ou parcial. Ver ifood_list_accounts. Omita se só houver uma. |
| `merchant_ids` | string[] | Não | Bulk mode: multiple values for merchant_id |

---

Este MCP também funciona via **conexão MCP** (Claude / Cursor) em `https://api.mcp.ai/p_ifood` — veja o [README](../../README.md). A skill acima é pra consumir a **REST API** direto (agente próprio / código).
