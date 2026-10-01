# Setup Guide: Context7 MCP Server
# Hướng Dẫn Cài Đặt: MCP Server Context7 (Live Documentation)

## What is Context7? / Đây là gì?

A live documentation and context injection MCP server. It fetches real-time, official, up-to-date documentation and API references for modern frameworks and libraries (React 19, Next.js 15, Supabase, Tailwind CSS, TypeScript, etc.), preventing model hallucinations and outdated code patterns.

Một MCP server chuyên tra cứu tài liệu sống và bơm ngữ cảnh thời gian thực. Nó lấy tài liệu và API reference chính thức mới nhất cho các framework/thư viện hiện đại, ngăn chặn triệt để tình trạng AI sinh code theo cú pháp cũ bị lỗi thời.

---

## Why install it? / Tại sao cần cài?

| Without / Không có | With / Có |
|---|---|
| AI uses deprecated API patterns (e.g. Next.js 13 syntax) | AI pulls real-time docs for Next.js 15 / React 19 |
| Hallucinates library function arguments | Reads exact TypeScript types & method signatures |
| Fails on newly released library versions | Real-time query to official documentation repositories |
| Dev must manually copy-paste docs into chat | AI auto-queries docs as an autonomous tool call |

---

## Prerequisites / Yêu cầu

- **Node.js**: v18.0.0 or later installed.

---

## Installation & Configuration / Cài đặt & Cấu hình

### 1. Claude Code CLI

```bash
claude mcp add context7 -- npx -y @upstash/context7-mcp
```

---

### 2. Antigravity IDE (Gemini)

Add to `~/.gemini/config/mcp_config.json`:

```json
{
  "mcpServers": {
    "context7": {
      "command": "npx",
      "args": ["-y", "@upstash/context7-mcp"]
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
    "context7": {
      "command": "npx",
      "args": ["-y", "@upstash/context7-mcp"]
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
    "context7": {
      "command": "npx",
      "args": ["-y", "@upstash/context7-mcp"]
    }
  }
}
```

---

## Verification / Kiểm tra

Ask your agent:
> *"Query the latest documentation for React 19 useActionState hook"*

If the agent returns accurate, real-time documentation snippets, Context7 is functioning properly.
