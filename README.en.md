# iFood

### iFood for Claude, ChatGPT and AI agents

Insights for your iFood store right in your AI assistant's chat. Generate charts of sales and payouts over time, average ticket, fees, menu mix and satisfaction (ratings), all via the official iFood API. The connection uses the official homologated app, no credentials needed.

- 📊 **16 tools**
- 🔒 **Read-only**
- 💬 **Works with any MCP client**: Claude Desktop, Cursor, VS Code, Cline, Continue
- 🔑 **Magic-link login (no password)**

[Portuguese version](README.md) · [Full docs (PT-BR)](docs/)

---

## One-click install

### Claude (Web and Desktop)

[➕ Open in Claude and connect](https://claude.ai/customize/connectors?modal=add-custom-connector&mcpName=iFood&mcpServerUrl=https%3A%2F%2Fapi.mcp.ai%2Fp_ifood)

Manual: [claude.ai/customize/connectors](https://claude.ai/customize/connectors) → **+** → **Add custom connector** → name `iFood`, URL `https://api.mcp.ai/p_ifood`.

### Cursor

[➕ Install in Cursor](cursor://anysphere.cursor-deeplink/mcp/install?name=ifood&config=eyJ1cmwiOiJodHRwczovL2FwaS5tY3AuYWkvcF9pZm9vZCJ9)

### VS Code (Copilot Chat)

[➕ Install in VS Code](vscode:mcp/install?name=ifood&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fapi.mcp.ai%2Fp_ifood%22%7D)

### Any other MCP-over-HTTP client

```
https://api.mcp.ai/p_ifood
```

---

## 16 tools

| Tool | Description |
|---|---|
| `ifood_list_accounts` | Lista as lojas iFood (conexões) vinculadas a este install — merchant_id, label. |
| `ifood_list_merchants` | Lista as lojas visíveis à conexão (id, nome, razão social). |
| `ifood_get_merchant` | Detalhe da loja: nome, razão social, endereço, ticket médio, tipo, status, canais. |
| `ifood_get_status` | Status operacional da loja em tempo real (aberta/fechada, available, motivos). |
| `ifood_get_opening_hours` | Horários de funcionamento da loja (shifts por dia: dayOfWeek, start, duration em minutos). |
| `ifood_list_interruptions` | Lista as pausas (interruptions) ativas/agendadas da loja. |
| `ifood_financial_summary` | Resumo financeiro agregado do período (chart-ready): total de pedidos, faturamento bruto, ticket médio, série diária (by_day), por forma de pagamento (by_payment_method) e repasses. |
| `ifood_list_sales` | Lista crua de vendas/pedidos do período (forma de pagamento, valores, taxas) pra análise detalhada. |
| `ifood_list_settlements` | Repasses (settlements) recebidos no período — valor líquido transferido, saldo. |
| `ifood_list_anticipations` | Antecipações de recebíveis no período (se a loja contratou antecipação no iFood). |
| `ifood_get_reconciliation` | Conciliação financeira de uma competência (YYYY-MM): links dos arquivos detalhados (CSV) com o financeiro completo por pedido. |
| `ifood_list_catalogs` | Lista os catálogos (cardápios) da loja — catalogId, groupId, status. |
| `ifood_list_categories` | Categorias de um catálogo (com itens por padrão): id, nome, status, itens (nome, preço, disponibilidade). |
| `ifood_catalog_summary` | Resumo do cardápio (chart-ready): totais (catálogos, categorias, itens, disponíveis/indisponíveis), faixa de preço (min/médio/máx) e mix por categoria (by_category). |
| `ifood_reviews_summary` | Resumo das avaliações da loja: nota agregada (score) e contagem total/válidas. |
| `ifood_list_reviews` | Lista avaliações individuais (nota, comentário, data) paginadas — pra histograma de notas ou ler comentários recentes. |

---

## Pricing

See [docs/precos.md](docs/precos.md) (PT-BR).

---

## License

MIT — see [LICENSE](LICENSE). The MCP server at `api.mcp.ai/p_ifood` is proprietary (hosted); this repo (manifests, docs, skills) is MIT.
