# Setup Guide: Supabase MCP Server
# Hướng Dẫn Cài Đặt: MCP Server Supabase

## What is Supabase MCP? / Đây là gì?

An MCP server that gives your AI agent direct access to your Supabase
project: inspect schemas, run queries, manage migrations, check RLS
policies, and deploy Edge Functions — all without leaving the chat.

MCP server cho phép AI agent truy cập trực tiếp vào dự án Supabase:
kiểm tra schema, chạy query, quản lý migration, kiểm tra RLS policy
và deploy Edge Functions — tất cả mà không cần rời khỏi chat.

## Why install it? / Tại sao cần cài?

| Without / Không có | With / Có |
|---|---|
| AI guesses your schema | AI inspects real schema via `list_tables` |
| Manual SQL file editing | AI creates migrations directly |
| No RLS visibility | AI audits RLS policies in real-time |
| Copy-paste connection strings | AI connects seamlessly |

## Prerequisites / Yêu cầu

1. A Supabase project (local or hosted)
2. Supabase CLI installed: `npm install -g supabase`
3. Your project's connection string or Supabase URL + anon key

## Installation / Cài đặt

### Option 1: Official Supabase MCP (Recommended)

```bash
npm install -g @supabase/mcp-server-supabase
```

### Option 2: Via Supabase CLI

```bash
supabase mcp start
```

## Configuration / Cấu hình

### Antigravity (Gemini)

Add to MCP config:

```json
{
  "mcpServers": {
    "supabase": {
      "command": "npx",
      "args": ["-y", "@supabase/mcp-server-supabase"],
      "env": {
        "SUPABASE_URL": "https://your-project.supabase.co",
        "SUPABASE_SERVICE_ROLE_KEY": "your-service-role-key"
      }
    }
  }
}
```

### Claude Code

Add to `claude_desktop_config.json`:

```json
{
  "mcpServers": {
    "supabase": {
      "command": "npx",
      "args": ["-y", "@supabase/mcp-server-supabase"],
      "env": {
        "SUPABASE_URL": "https://your-project.supabase.co",
        "SUPABASE_SERVICE_ROLE_KEY": "your-service-role-key"
      }
    }
  }
}
```

### Cursor / Windsurf

Add MCP server in IDE settings:
- Name: `supabase`
- Command: `npx -y @supabase/mcp-server-supabase`
- Environment variables:
  - `SUPABASE_URL`: Your project URL
  - `SUPABASE_SERVICE_ROLE_KEY`: Your service role key

## Security Warning / Cảnh Báo Bảo Mật

⚠️ **NEVER commit your `SUPABASE_SERVICE_ROLE_KEY` to git!**
Use environment variables or a `.env` file (added to `.gitignore`).

⚠️ **KHÔNG BAO GIỜ commit `SUPABASE_SERVICE_ROLE_KEY` vào git!**
Sử dụng biến môi trường hoặc file `.env` (đã thêm vào `.gitignore`).

## Verification / Kiểm tra

Ask your AI: "List all tables in my Supabase project"

If it returns table names, the server is working.

## Fallback / Dự phòng

Without Supabase MCP, the AI will work with:
- Manual SQL migration files in `supabase/migrations/`
- Supabase CLI commands (`supabase db push`, `supabase functions deploy`)
- Direct API calls via `supabase-js` client library
