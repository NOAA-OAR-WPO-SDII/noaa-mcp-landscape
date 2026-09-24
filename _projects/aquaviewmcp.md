---
name: Aquaview MCP
organization: Aquaview
affiliation: External       # NOAA | External
poc: Aquaview (https://aquaview.org)
summary: >-
  MCP access to publicly available oceanographic and environmental data
  aggregated from NOAA, NDBC, IOOS, and other sources through Aquaview's
  federated catalog.

status: production
mcp_type: server
resource: data access

overview: >
  Aquaview is a multi-cloud environmental-data platform whose STAC-based catalog
  federates 290K+ oceanographic and environmental datasets across sources. Its
  MCP server lets AI agents query, discover, and analyze that catalog through a
  hosted, remote endpoint — usable from any MCP-capable client without a local
  install.

capabilities:
  - "Query oceanographic and environmental datasets in the Aquaview catalog"
  - "Discover datasets across federated sources (STAC-based catalog)"
  - "Retrieve and analyze data for AI-agent workflows"

resources_exposed:
  - "Federated STAC catalog of 290K+ oceanographic and environmental datasets"
  - "Sources including NOAA, NDBC, IOOS (Integrated Ocean Observing System), World Ocean Database, and Alaska Ocean Observing System"

architecture: >
  Remote, hosted MCP server (FastMCP with a Starlette adapter) at
  https://mcp.aquaview.org/mcp over Streamable HTTP, with a legacy SSE endpoint
  at https://mcp.aquaview.org/sse. Documented for Claude Desktop (custom
  connector), Gemini CLI, VS Code, and Windsurf. The platform uses OIDC/OAuth
  identity with role-scoped access; whether the MCP endpoint itself requires
  authentication isn't stated on the public page.

status_detail: >
  Publicly available hosted service, part of an always-on enterprise platform.

evidence:
  - label: "MCP server (overview & client setup)"
    url: https://aquaview.org/mcp
  - label: "MCP developer documentation"
    url: https://aquaview.org/documentation?page=/developer-guide/platform-features/mcp-server
  - label: "API"
    url: https://api.aquaview.org

last_verified: 2026-09-24
---
