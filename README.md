# @settlegrid/discovery

[![npm](https://img.shields.io/npm/v/@settlegrid/discovery)](https://www.npmjs.com/package/@settlegrid/discovery)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

An MCP (Model Context Protocol) server that lets AI agents discover and invoke 1,444+ monetized tools on the [SettleGrid](https://settlegrid.ai) marketplace. One connection gives agents access to MCP servers, AI models, REST APIs, agent tools, and SDK packages — all with per-call billing.

## Quick Start

### With npx (no install)

```bash
npx @settlegrid/discovery
```

### Install globally

```bash
npm install -g @settlegrid/discovery
settlegrid-discovery
```

### From source

```bash
git clone https://github.com/lexwhiting/settlegrid-discovery.git
cd settlegrid-discovery
npm install
npm run build
npm start
```

## Add to Claude Desktop

Edit `~/Library/Application Support/Claude/claude_desktop_config.json` (macOS) or `%APPDATA%\Claude\claude_desktop_config.json` (Windows):

```json
{
  "mcpServers": {
    "settlegrid": {
      "command": "npx",
      "args": ["-y", "@settlegrid/discovery"]
    }
  }
}
```

## Add to Cursor

In Cursor Settings → MCP, add:

```json
{
  "mcpServers": {
    "settlegrid": {
      "command": "npx",
      "args": ["-y", "@settlegrid/discovery"]
    }
  }
}
```

## Available Tools

### `search_tools`

Search for monetized AI tools by keyword, category, price, or rating.

| Parameter  | Type   | Required | Description                     |
|------------|--------|----------|---------------------------------|
| `query`    | string | no       | Free-text search query          |
| `category` | string | no       | Filter by category              |
| `limit`    | number | no       | Max results, 1-100 (default 20) |

### `get_tool`

Get full details for a specific tool by slug.

| Parameter | Type   | Required | Description          |
|-----------|--------|----------|----------------------|
| `slug`    | string | yes      | Tool slug identifier |

### `list_categories`

List all 24 tool categories with counts. No parameters.

### `get_developer`

Get a developer's public profile and their published tools.

| Parameter | Type   | Required | Description            |
|-----------|--------|----------|------------------------|
| `slug`    | string | yes      | Developer profile slug |

### `list_marketplace_tools`

List popular tools with pricing and availability info.

| Parameter  | Type   | Required | Description        |
|------------|--------|----------|--------------------|
| `category` | string | no       | Filter by category |
| `limit`    | number | no       | Max results        |

### `call_tool`

Invoke any marketplace tool directly. Routes through SettleGrid's Smart Proxy for billing.

| Parameter | Type   | Required | Description                |
|-----------|--------|----------|----------------------------|
| `slug`    | string | yes      | Tool slug                  |
| `method`  | string | no       | Tool method to call        |
| `args`    | object | no       | Arguments to pass          |

> **Note:** Discovery tools are free with no API key. `call_tool` requires an API key for billed invocations — get one at [settlegrid.ai](https://settlegrid.ai).

## Configuration

| Variable             | Default                 | Description                    |
|----------------------|-------------------------|--------------------------------|
| `SETTLEGRID_API_URL` | `https://settlegrid.ai` | Base URL of the SettleGrid API |

## What is SettleGrid?

SettleGrid is the universal settlement layer for the AI economy — per-call billing, usage metering, and automated payouts for any AI service. 15 payment protocols. Free forever at 50K ops/month.

- **Marketplace**: [settlegrid.ai/marketplace](https://settlegrid.ai/marketplace)
- **Templates**: [settlegrid.ai/templates](https://settlegrid.ai/templates) (991 forkable MCP servers)
- **Free Tools**: [settlegrid.ai/free-tools](https://settlegrid.ai/free-tools) (29 callable tools, no API key needed)
- **Docs**: [settlegrid.ai/docs](https://settlegrid.ai/docs)
- **Platform**: [settlegrid.ai/platform](https://settlegrid.ai/platform)

## License

MIT
