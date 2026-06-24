# Frontify MCP Server

The Frontify MCP Server connects AI assistants — such as Claude, ChatGPT, and Cursor — directly to your Frontify digital asset management (DAM) system. Built on the [Model Context Protocol (MCP)](https://modelcontextprotocol.io), an open standard for connecting AI models to external tools and data, it lets you discover brands, search and retrieve assets, manage metadata, collaborate, and automate creative workflows through natural language.

The server is **hosted by Frontify** — there's nothing to install or run yourself. Connect your MCP client to the official endpoint and authorize access to your Frontify instance.

> **Beta:** The Frontify MCP Server is an experimental integration. Write access carries real risk, and AI models can hallucinate — generating responses that are plausible but wrong. Verify outputs before taking important actions.

## Features

The server exposes a broad set of capabilities for working with your Frontify content:

- **Brand & structure discovery** — browse brands, libraries, projects, and their structure.
- **Navigation & search** — search assets across brands, libraries, and projects with type filtering.
- **Asset retrieval, upload & creation** — fetch assets with full metadata and download URLs; create assets from a URL or by uploading files.
- **Organizing assets** — manage tags, targets, custom metadata, collections, and folders.
- **Comments & collaboration** — read, add, and reply to comments and annotations on assets.
- **Guidelines** — explore brand portals and read guideline pages and library page assets.
- **Creative templates** — list templates and export creatives with custom text, image, and color variables.
- **Workflow automation** — manage workflow tasks, statuses, and checklists across the content lifecycle.

## Tool Packs

The server organizes its tools into curated **packs** tailored to different roles and risk appetites. Each pack is available at its own endpoint, and visiting a pack URL in your browser shows a human-readable overview of the tools it contains.

| Pack                  | Endpoint                                                      | Description                                             |
| --------------------- | ------------------------------------------------------------ | ------------------------------------------------------- |
| `admin`               | `https://mcp.frontify-integrations.com/mcp/packs/admin`               | Full access — all tools, no restrictions                |
| `discovery`           | `https://mcp.frontify-integrations.com/mcp/packs/discovery`           | Read-only exploration — no writes or mutations          |
| `collaboration`       | `https://mcp.frontify-integrations.com/mcp/packs/collaboration`       | Comments, replies, and workflow tasks                   |
| `asset-organization`  | `https://mcp.frontify-integrations.com/mcp/packs/asset-organization`  | Tags, targets, metadata, collections, and folders       |
| `asset-creation`      | `https://mcp.frontify-integrations.com/mcp/packs/asset-creation`      | Upload, update, tag, and add metadata to assets         |
| `creative-automation` | `https://mcp.frontify-integrations.com/mcp/packs/creative-automation` | Template export and upload results                      |
| `workflow-automation` | `https://mcp.frontify-integrations.com/mcp/packs/workflow-automation` | Full workflow lifecycle and comments                    |
| `brand-admin`         | `https://mcp.frontify-integrations.com/mcp/packs/brand-admin`         | Projects, folders, collections, and asset moves         |
| `brand-portal`        | `https://mcp.frontify-integrations.com/mcp/packs/brand-portal`        | List guidelines, read pages, browse library page assets |
| `bulk-operations`     | `https://mcp.frontify-integrations.com/mcp/packs/bulk-operations`     | Multi-asset move, update, metadata, and targets         |

## Setup

The Frontify MCP Server is hosted by Frontify — pick the pack endpoint that fits your use case, point your MCP client at it, and authorize access to your Frontify instance on first connection. We recommend starting with the read-only `discovery` pack.

Authorization follows the flow described in the [MCP specification](https://modelcontextprotocol.io/specification/2025-11-25/basic/authorization), including both client registration approaches — Client ID Metadata Documents (CIMD) and Dynamic Client Registration (DCR).

### Cursor / Claude Desktop

Add the chosen pack endpoint to your MCP configuration file (`~/.cursor/mcp.json` or `claude_desktop_config.json`):

```json
{
  "mcpServers": {
    "frontify": {
      "url": "https://mcp.frontify-integrations.com/mcp/packs/discovery"
    }
  }
}
```

### ChatGPT

Add the chosen pack endpoint as a connector in your ChatGPT app settings.

On first connection, you'll be guided through the Frontify OAuth flow to authorize access to your instance.

## Links

- [Model Context Protocol](https://modelcontextprotocol.io)
- [Frontify](https://www.frontify.com)

## License

Licensed under the [MIT License](./LICENSE).
