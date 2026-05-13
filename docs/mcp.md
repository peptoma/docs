# MCP Server Guide

Connect Claude Desktop, Cursor, VS Code, and any MCP-compatible AI agent to PEPTOMA.

**GitHub:** [github.com/peptoma/mcp](https://github.com/peptoma/mcp)  
**npm:** [npmjs.com/package/peptoma-mcp](https://www.npmjs.com/package/peptoma-mcp)

## Quick Start

```bash
npx peptoma-mcp --api-key pptm_your_key_here
```

## Claude Desktop Setup

`~/.claude/claude_desktop_config.json`:
```json
{
  "mcpServers": {
    "peptoma": {
      "command": "npx",
      "args": ["peptoma-mcp", "--api-key", "pptm_your_key_here"]
    }
  }
}
```

## Cursor Setup

`.cursor/mcp.json`:
```json
{
  "mcpServers": {
    "peptoma": {
      "command": "npx",
      "args": ["peptoma-mcp", "--api-key", "pptm_your_key_here"]
    }
  }
}
```

## Available Tools

`analyze_sequence` · `get_analysis` · `search_feed` · `get_feed_stats` · `get_trending` · `list_annotations` · `create_annotation` · `vote_annotation` · `get_token_balance` · `get_leaderboard`

Full reference: [github.com/peptoma/mcp](https://github.com/peptoma/mcp)
