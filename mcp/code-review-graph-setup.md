# Setup Guide: code-review-graph MCP Server
# Hướng Dẫn Cài Đặt: MCP Server code-review-graph

## What is code-review-graph? / Đây là gì?

A Knowledge Graph engine that indexes your codebase and provides instant
structural analysis: dependency tracing, impact radius, dead code detection,
and intelligent code review.

Một engine Knowledge Graph lập chỉ mục codebase và cung cấp phân tích
cấu trúc tức thì: truy vết phụ thuộc, bán kính ảnh hưởng, phát hiện
dead code và review code thông minh.

## Why install it? / Tại sao cần cài?

| Without / Không có | With / Có |
|---|---|
| AI reads files one by one (slow) | AI queries the graph (instant) |
| Uses grep to find callers (misses many) | Uses `callers_of` (finds all) |
| ~5000 tokens per exploration | ~500 tokens per exploration |
| Cannot detect impact radius | `get_impact_radius` in 1 call |

## Installation / Cài đặt

### Option 1: npm (Recommended / Khuyến nghị)

```bash
npm install -g code-review-graph
```

### Option 2: From source

```bash
git clone https://github.com/anthropics/code-review-graph
cd code-review-graph
npm install
npm run build
```

## Configuration for each IDE / Cấu hình cho từng IDE

### Antigravity (Gemini)

Add to your MCP config (`.gemini/mcp_config.json` or IDE settings):

```json
{
  "mcpServers": {
    "code-review-graph": {
      "command": "code-review-graph",
      "args": ["--project-root", "."],
      "env": {}
    }
  }
}
```

### Claude Code

Add to `claude_desktop_config.json`:

```json
{
  "mcpServers": {
    "code-review-graph": {
      "command": "code-review-graph",
      "args": ["--project-root", "."]
    }
  }
}
```

### Cursor / Windsurf

Add MCP server in IDE settings → MCP → Add Server:
- Name: `code-review-graph`
- Command: `code-review-graph`
- Args: `--project-root .`

## Verification / Kiểm tra

After installing, ask your AI: "Run `list_graph_stats`"

If it responds with node/edge counts, the server is working.
If it errors, check that the command is in your PATH.

## Fallback / Dự phòng

If you cannot install this server, the workflow skills will still work.
They will automatically fall back to grep/glob/file-reading, which is
slower but functional.
