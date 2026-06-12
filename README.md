# iFood

### iFood para Claude, ChatGPT e agentes de IA

Insights da sua loja no iFood direto no chat do seu assistente de IA. Gere gráficos de vendas e repasses no tempo, ticket médio, taxas, mix de cardápio e satisfação (avaliações), tudo pela API oficial do iFood. A conexão usa o app oficial homologado, você não informa credenciais.

- 📊 **16 ferramentas**
- 🔒 **Somente leitura**
- 💬 **Funciona com qualquer cliente MCP**: Claude Desktop, Cursor, VS Code, Cline, Continue
- 🔑 **Login via magic-link (sem senha)**

[English version](README.en.md) · [Documentação completa](docs/) · [Skill pra agentes](skills/)

---

## Instalar em 1 clique

### Claude (Web e Desktop)

A Anthropic unificou a instalação de MCPs em `claude.ai/customize/connectors`. **O mesmo link serve pra Claude Web e Claude Desktop** (basta estar logado):

[➕ Abrir no Claude e conectar](https://claude.ai/customize/connectors?modal=add-custom-connector&mcpName=iFood&mcpServerUrl=https%3A%2F%2Fapi.mcp.ai%2Fp_ifood)

**Manual** (se o deeplink não abrir): [claude.ai/customize/connectors](https://claude.ai/customize/connectors) → **+** → **Adicionar conector personalizado** → cole **Nome** `iFood` e **URL** `https://api.mcp.ai/p_ifood`.

### Cursor

[➕ Instalar iFood no Cursor](cursor://anysphere.cursor-deeplink/mcp/install?name=ifood&config=eyJ1cmwiOiJodHRwczovL2FwaS5tY3AuYWkvcF9pZm9vZCJ9)

### VS Code (Copilot Chat)

[➕ Instalar iFood no VS Code](vscode:mcp/install?name=ifood&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fapi.mcp.ai%2Fp_ifood%22%7D)

### ChatGPT, Manus, OpenClaw e mais 40+ clientes

Funciona em qualquer cliente MCP que suporte **MCP over HTTP**. A URL do servidor é sempre:

```
https://api.mcp.ai/p_ifood
```

Detalhes por cliente: [INSTALL.md](INSTALL.md).

---

## Exemplos de uso

```
Gere um gráfico das minhas vendas no iFood nos últimos 30 dias
Qual meu ticket médio e o total de repasses neste mês?
Mostra o mix do meu cardápio e minha nota no iFood
```

---

## 16 ferramentas disponíveis

| Tool | Descrição |
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

Detalhe de cada tool: [docs/ferramentas.md](docs/ferramentas.md)

---

## Preços

Cobrança por conexão ativa. Veja [docs/precos.md](docs/precos.md).

---

## Privacidade & LGPD

- **Somente leitura**, nenhuma ferramenta altera dados na origem.
- **Sub-processadores**: iFood, o LLM host que você escolher (Claude, ChatGPT, Cursor, agente próprio). Lista completa em [docs/privacidade-lgpd.md](docs/privacidade-lgpd.md).
- Os dados retornados pelas tools são enviados ao **LLM host que você escolher**, sub-processador fora do nosso controle. Recomendamos planos com opt-out de treinamento.

---

## Perguntas frequentes

**O servidor é open source?**
O servidor é proprietário (hosted). Este repositório é o wrapper público com manifestos, docs e skills — tudo MIT.

**Posso usar com agente próprio (não Claude/Cursor)?**
Sim — qualquer cliente que suporte MCP over HTTP. URL: `https://api.mcp.ai/p_ifood`.


---

## Suporte

- 📧 [ifood@mcp.ai](mailto:ifood@mcp.ai)
- 🐛 [GitHub Issues](https://github.com/mcp-dir/ifood-mcp/issues)
- 📄 [docs/](docs/)

---

## Licença

MIT — veja [LICENSE](LICENSE). O servidor MCP em `api.mcp.ai/p_ifood` é proprietário (hosted); este repositório (manifestos, docs, skills) é MIT.
