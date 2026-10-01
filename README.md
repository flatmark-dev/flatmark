# flatmark

[![smithery badge](https://smithery.ai/badge/podshalocef/flatmark)](https://smithery.ai/servers/podshalocef/flatmark)

**PDF, Word, PowerPoint and Excel to Markdown**

flatmark converts PDF, Word, PowerPoint, Excel and HTML to Markdown over a REST API and an MCP server. Files up to 8 MB convert in one call with MarkItDown. Files up to 25 MB and 200 pages go through a queue that runs Docling with OCR and table detection. The queue returns Markdown and a JSON structure file, by polling or a signed webhook. The servers are in Germany. The free plan has 100 credits a month and needs no card.

## Links

- **Website:** https://flatmark.dev/go/github
- **API docs:** https://api.flatmark.dev/docs · [OpenAPI](https://api.flatmark.dev/openapi.json)
- **Pricing:** https://flatmark.dev/pricing
- **Convert a PDF free:** https://flatmark.dev/tools/pdf-to-markdown
- **llms.txt:** https://flatmark.dev/llms.txt
- **Privacy policy:** https://flatmark.dev/privacy
- **Support:** https://flatmark.dev/support

## MCP server

Streamable-HTTP endpoint: `https://api.flatmark.dev/mcp/` — the anonymous
tier works without a key; an API key raises the limits.

Claude Code:

```sh
claude mcp add --transport http flatmark https://api.flatmark.dev/mcp/
```

Claude Code: `/plugin marketplace add flatmark-dev/flatmark` then `/plugin install flatmark@flatmark` (set `FLATMARK_API_KEY` for your key).

Cursor / Windsurf / Cline / Claude Desktop:

```json
{
  "mcpServers": {
    "flatmark": {
      "url": "https://api.flatmark.dev/mcp/"
    }
  }
}
```

One-click installs for every client: https://flatmark.dev/connect

## API

Base URL `https://api.flatmark.dev/` — authenticate with an `X-API-Key` header;
anonymous calls work at a lower rate limit.
