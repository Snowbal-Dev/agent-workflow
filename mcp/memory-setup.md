# Setup Guide: Persistent Memory MCP Server
# Hướng Dẫn Cài Đặt: MCP Server Memory (@modelcontextprotocol/server-memory)

## What is Memory MCP Server? / Đây là gì?

The official Knowledge Graph-based persistent memory server created by the Model Context Protocol team. It enables AI coding agents to store, retrieve, update, and search structured entities, relations, and observations across separate chat sessions.

MCP server quản lý bộ nhớ dài hạn chính thức dựa trên Đồ thị Tri thức (Knowledge Graph). Nó cho phép AI agent lưu trữ, truy xuất, cập nhật và tìm kiếm các thực thể, mối quan hệ và ghi nhớ nghiệp vụ xuyên suốt các phiên chat khác nhau mà không bao giờ bị quên.

**Registry Link**: [https://claudemarketplaces.com/mcp/modelcontextprotocol/servers/memory](https://claudemarketplaces.com/mcp/modelcontextprotocol/servers/memory)  
**Package**: `@modelcontextprotocol/server-memory`

---

## Why install it? / Tại sao cần cài?

| Without / Không có | With / Có |
|---|---|
| AI forgets project conventions in fresh sessions | Retains coding preferences, architectural choices, and team rules |
| Repeatedly explaining business rules every morning | AI instantly recalls entities, schemas, and API constraints |
| Context degradation over long conversations | Clean context window with offloaded long-term memory graph |
| Zero continuity between team tasks | Continuous cross-session institutional knowledge |

---

## Prerequisites / Yêu cầu

- **Node.js**: v18.0.0 or later installed on your machine.

---

## Installation & Configuration / Cài đặt & Cấu hình

### 1. Claude Code CLI

```bash
claude mcp add memory -- npx -y @modelcontextprotocol/server-memory
```

---

### 2. Antigravity IDE (Gemini)

Add to `~/.gemini/config/mcp_config.json`:

```json
{
  "mcpServers": {
    "memory": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-memory"]
    }
  }
}
```

---

### 3. Cursor & Windsurf

Add to `.cursor/mcp.json` or IDE Settings -> MCP:

```json
{
  "mcpServers": {
    "memory": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-memory"]
    }
  }
}
```

---

### 4. Claude Desktop

Add to `claude_desktop_config.json`:

```json
{
  "mcpServers": {
    "memory": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-memory"]
    }
  }
}
```

---

## Available Tools / Danh Sách Công Cụ Khả Dụng

- **`create_entities`**: Create new entities (e.g. "UserAuthModule", "SupabaseRLSPolicy") in the knowledge graph.
- **`create_relations`**: Define links between entities (e.g. "UsNoteFeature depends_on MomentsApi").
- **`add_observations`**: Attach specific notes or learnings to existing entities.
- **`read_graph`**: Read the entire memory graph.
- **`search_nodes`**: Search entities and relations by keywords.
- **`open_nodes`**: Retrieve detailed nodes and their relationships.

---

## Verification / Kiểm tra

Ask your agent:
> *"Remember that in this project we always use Zod for validation and snake_case for PostgreSQL columns"*

In a new chat session, ask:
> *"What validation library and column casing convention do we use in this project?"*

If the agent recalls Zod and snake_case without prompting, your Memory MCP is working!
