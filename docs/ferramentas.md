# Ferramentas

iFood expõe 16 ferramentas (todas somente leitura).

### 1. `ifood_list_accounts`
**Input**: `account` (opcional)

Lista as lojas iFood (conexões) vinculadas a este install — merchant_id, label.

### 2. `ifood_list_merchants`
**Input**: `page` (opcional), `size` (opcional), `account` (opcional)

Lista as lojas visíveis à conexão (id, nome, razão social).

### 3. `ifood_get_merchant`
**Input**: `merchant_id` (opcional), `account` (opcional), `merchant_ids` (opcional)

Detalhe da loja: nome, razão social, endereço, ticket médio, tipo, status, canais.

### 4. `ifood_get_status`
**Input**: `merchant_id` (opcional), `account` (opcional), `merchant_ids` (opcional)

Status operacional da loja em tempo real (aberta/fechada, available, motivos).

### 5. `ifood_get_opening_hours`
**Input**: `merchant_id` (opcional), `account` (opcional), `merchant_ids` (opcional)

Horários de funcionamento da loja (shifts por dia: dayOfWeek, start, duration em minutos).

### 6. `ifood_list_interruptions`
**Input**: `merchant_id` (opcional), `account` (opcional), `merchant_ids` (opcional)

Lista as pausas (interruptions) ativas/agendadas da loja.

### 7. `ifood_financial_summary`
**Input**: `start_date` (opcional), `end_date` (opcional), `account` (opcional)

Resumo financeiro agregado do período (chart-ready): total de pedidos, faturamento bruto, ticket médio, série diária (by_day), por forma de pagamento (by_payment_method) e repasses.

### 8. `ifood_list_sales`
**Input**: `start_date` (opcional), `end_date` (opcional), `account` (opcional)

Lista crua de vendas/pedidos do período (forma de pagamento, valores, taxas) pra análise detalhada.

### 9. `ifood_list_settlements`
**Input**: `start_date` (opcional), `end_date` (opcional), `account` (opcional)

Repasses (settlements) recebidos no período — valor líquido transferido, saldo.

### 10. `ifood_list_anticipations`
**Input**: `start_date` (opcional), `end_date` (opcional), `account` (opcional)

Antecipações de recebíveis no período (se a loja contratou antecipação no iFood).

### 11. `ifood_get_reconciliation`
**Input**: `competence`, `account` (opcional)

Conciliação financeira de uma competência (YYYY-MM): links dos arquivos detalhados (CSV) com o financeiro completo por pedido.

### 12. `ifood_list_catalogs`
**Input**: `merchant_id` (opcional), `account` (opcional), `merchant_ids` (opcional)

Lista os catálogos (cardápios) da loja — catalogId, groupId, status.

### 13. `ifood_list_categories`
**Input**: `merchant_id` (opcional), `catalog_id`, `include_items` (opcional), `account` (opcional), `merchant_ids` (opcional), `catalog_ids` (opcional)

Categorias de um catálogo (com itens por padrão): id, nome, status, itens (nome, preço, disponibilidade).

### 14. `ifood_catalog_summary`
**Input**: `merchant_id` (opcional), `account` (opcional), `merchant_ids` (opcional)

Resumo do cardápio (chart-ready): totais (catálogos, categorias, itens, disponíveis/indisponíveis), faixa de preço (min/médio/máx) e mix por categoria (by_category).

### 15. `ifood_reviews_summary`
**Input**: `merchant_id` (opcional), `account` (opcional), `merchant_ids` (opcional)

Resumo das avaliações da loja: nota agregada (score) e contagem total/válidas.

### 16. `ifood_list_reviews`
**Input**: `merchant_id` (opcional), `page` (opcional), `size` (opcional), `account` (opcional), `merchant_ids` (opcional)

Lista avaliações individuais (nota, comentário, data) paginadas — pra histograma de notas ou ler comentários recentes.

## Prompts de exemplo

```
Gere um gráfico das minhas vendas no iFood nos últimos 30 dias
Qual meu ticket médio e o total de repasses neste mês?
Mostra o mix do meu cardápio e minha nota no iFood
```
