---
name: "flatmark"
description: "Document to Markdown MCP server: PDF, Word, PowerPoint, Excel and HTML, with OCR for large files. Use it through the flatmark MCP server at https://api.flatmark.dev/mcp/ — the anonymous tier needs no key."
license: "MIT"
compatibility: "Needs network access to https://api.flatmark.dev/mcp/; an API key is optional."
---

# flatmark

flatmark converts PDF, Word, PowerPoint, Excel and HTML to Markdown over a REST API and an MCP server. Files up to 8 MB convert in one call with MarkItDown. Files up to 25 MB and 200 pages go through a queue that runs Docling with OCR and table detection. The queue returns Markdown and a JSON structure file, by polling or a signed webhook. The servers are in Germany. The free plan has 100 credits a month and needs no card.

## Connect

- MCP endpoint (streamable HTTP): https://api.flatmark.dev/mcp/ — the anonymous tier works without a key.
- An API key raises the limits: send it in the `X-API-Key` header. The Claude Code plugin reads it from `FLATMARK_API_KEY`.
- API reference: https://api.flatmark.dev/docs

Maintained by the flatmark team.
