# flatmark

[![smithery badge](https://smithery.ai/badge/podshalocef/flatmark)](https://smithery.ai/servers/podshalocef/flatmark)

**Document to Markdown API and MCP server for PDF, Word, PowerPoint, Excel and HTML. OCR queue for large files. Hosted in Germany.**

flatmark converts PDF, Word, PowerPoint, Excel and HTML to Markdown over a REST API and an MCP server. Files up to 8 MB convert in one call with MarkItDown. Files up to 25 MB and 200 pages go through a queue that runs Docling with OCR and table detection. The queue returns Markdown and a JSON structure file, by polling or a signed webhook. The servers are in Germany. The free plan has 100 credits a month and needs no card.

## Quickstart

Convert a PDF to Markdown in one call. The anonymous tier needs no key; add
`-H "X-API-Key: $FLATMARK_API_KEY"` for your plan's limits.

```sh
curl -sO https://flatmark.dev/app-static/samples/sample.pdf
curl -F file=@sample.pdf https://api.flatmark.dev/v1/convert
```

```json
{"markdown":"Hello Docling smoke test\n\n","meta":{"filename":"sample.pdf"}}
```

Files over 8 MB and scanned documents go through the OCR queue instead:
`POST /v1/convert/jobs`, then poll or receive a signed webhook.

## Use it from

### MCP server

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

**Integrations** (n8n, Zapier, Make, Workato, Dify, SDKs and templates): https://github.com/flatmark-dev/flatmark-integrations

## Links

- **Website:** https://flatmark.dev/go/github
- **API docs:** https://api.flatmark.dev/docs · [OpenAPI](https://api.flatmark.dev/openapi.json)
- **Pricing:** https://flatmark.dev/pricing
- **Convert a PDF free:** https://flatmark.dev/tools/pdf-to-markdown
- **llms.txt:** https://flatmark.dev/llms.txt
- **Privacy policy:** https://flatmark.dev/privacy
- **Support:** https://flatmark.dev/support

## API

Base URL `https://api.flatmark.dev/` — authenticate with an `X-API-Key` header;
anonymous calls work at a lower rate limit.

## About the files here

- `.claude-plugin/` — Claude Code plugin, with this repo as its own marketplace.
- `.mcp.json` — the MCP server the Claude Code plugin connects to.
- `gemini-extension.json` — Gemini CLI extension manifest.
- `glama.json` — Glama server claim (names the maintainer).
- `mcp.json` — Agent Plugins 1.0 MCP server config.
- `plugin.json` — Agent Plugins 1.0 plugin manifest.
- `server.json` — the entry in the official MCP Registry.
- `skills/` — an Agent Skill (agentskills.io SKILL.md) for skill galleries.
