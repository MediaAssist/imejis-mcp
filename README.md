# Imejis MCP Server

[![smithery badge](https://smithery.ai/badge/support-ftxl/imejis-mcp)](https://smithery.ai/servers/support-ftxl/imejis-mcp)

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

- **Discover:** `get_design_guide`, `list_component_types` (all 27 components:
  text, images, QR codes, barcodes, tables, and 12+ chart types), generated
  from the same registry the renderer validates against, so it never drifts.
- **Design:** `create_design`, `create_design_from_template`, `update_design`,
  `duplicate_design`, `preview_design`, plus `create_design_variation` to add
  another size (it reflows the master's layout onto the new canvas).
- **Render:** `export_design` (one image), `get_render_url` (a permanent URL
  that re-renders per request with field overrides), `get_stored_image_url`
  (stores the render, returns a hosted or expiring URL) and `bulk_export` (up
  to 25 renders in one call — several sizes, several data variants, several
  designs, or the ordered slides of a carousel).
- **Publish:** every edit publishes a numbered version you can name, list,
  read back and roll back (`publish_design`, `list_design_versions`,
  `get_design_version`, `rollback_design`). `create_share_link` gives the
  design a public page anyone with the URL can open, and
  `create_template_from_design` makes it reusable across the workspace. Both
  serve a pinned version, so `update_share_link` / `sync_template` /
  `set_live_version` control exactly what the public sees.
- **Gallery:** ask an admin to list a template publicly with
  `submit_template_for_review` and follow it with `list_template_reviews`.
  Approving is an admin action in the imejis dashboard — there is no tool for
  it, so an agent can ask but never publish to the gallery itself.
- **Assets & account:** manage files, fonts, templates, API keys, and read plan,
  credits, and quota.

Anywhere a tool takes a design id, both ids work: the one a list returns or the
short code from a render URL.

It also ships ready-made **prompts**: `create_social_post`, `make_og_image`,
`edit_design`, `turn_design_into_api` and `export_design_image`.

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
