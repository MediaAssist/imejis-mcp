# Imejis MCP Server

Give your AI agent a design studio. The Imejis MCP server lets Claude, ChatGPT,
Cursor, or any MCP client design and render **real, on-brand images** for you.

Your agent designs a template once, then renders it in bulk with the same layout
every time, only the data changing. Unlike a plain image model, the output is
deterministic and pixel-perfect, so your brand never drifts.

- **Endpoint:** `https://api.imejis.io/api/mcp`
- **Transport:** Streamable HTTP
- **Auth:** OAuth 2.0 (RFC 8707 audience binding, RFC 9728 protected-resource metadata)
- **Hosted:** yes, nothing to install
- **Landing page & quick tour:** https://www.imejis.io/agents
- **Server card:** https://www.imejis.io/.well-known/mcp/server-card.json

> This is a hosted MCP server. This repository holds its public metadata
> (`server.json`) and connection docs; the server runs at `api.imejis.io`.

## Connect

Add the endpoint as a remote MCP server and authorize once over OAuth.

- **Claude:** Settings → Connectors → Add custom connector → paste
  `https://api.imejis.io/api/mcp` → approve the sign-in.
  [Full guide](https://www.imejis.io/blogs/tutorials/generate-images-claude-mcp)
- **ChatGPT:** Settings → Connectors → add an MCP server → enter the URL → sign in.
  [Full guide](https://www.imejis.io/blogs/tutorials/generate-images-from-chatgpt-mcp)
- **Cursor:** Settings → MCP → Add new server → paste the URL → approve.
  [Full guide](https://www.imejis.io/blogs/tutorials/generate-images-in-cursor-mcp)

## What your agent can do

Once connected, the agent discovers the full catalog, designs, and renders:

- **Discover:** `get_design_guide`, `list_component_types` (all 24 components:
  text, images, QR codes, barcodes, tables, and 12+ chart types), generated
  from the same registry the renderer validates against, so it never drifts.
- **Design:** `create_design`, `create_design_from_template`, `update_design`,
  `preview_design`.
- **Render:** `export_design` (one image) and `get_render_url` (a permanent URL
  that re-renders per request with field overrides, for bulk).
- **Assets & account:** manage files, fonts, templates, API keys, and read plan,
  credits, and quota.

It also ships ready-made **prompts**: `create_social_post`, `make_og_image`,
`edit_design`, and `turn_design_into_api`.

## Try these

- "Create a 1200×630 OG image for a post titled 'How MCP works' and export the PNG."
- "Make a QR code that links to imejis.io/agents and give me the SVG."
- "Build a bar chart from this data, then render one image per row of my CSV with the same layout."

## Prefer code?

The same renderer has a REST API with tested examples in cURL, Node.js, Python,
Ruby, Go, PHP, Java, and C#: https://www.imejis.io/apis

## Pricing

The free plan includes 100 renders per month, no credit card. Agent renders
count against your plan the same as a direct API call. See
https://www.imejis.io/pricing.

## Links

- Website: https://www.imejis.io
- AI Agents: https://www.imejis.io/agents
- API docs: https://www.imejis.io/apis
- Components: https://www.imejis.io/components
- Privacy: https://www.imejis.io/privacy-policy
