# Setup Guide: Docker MCP Server
# Hướng Dẫn Cài Đặt: MCP Server Docker (@modelcontextprotocol/server-docker)

## What is Docker MCP Server? / Đây là gì?

A Model Context Protocol server that grants your AI agent full lifecycle management over Docker containers, images, volumes, and networks. It allows AI agents to spin up sandbox environments, execute isolated test suites, inspect container health, and debug containerized microservices safely.

MCP server cung cấp cho AI agent khả năng quản lý toàn diện vòng đời của Docker: tạo và chạy container cô lập, build image, quản lý volume và network. Giúp AI có thể chạy thử nghiệm code, test database an toàn trong môi trường sandbox mà không ảnh hưởng tới máy chủ thật.

---

## Why install it? / Tại sao cần cài?

| Without / Không có | With / Có |
|---|---|
| AI runs risky scripts directly on host OS | AI spins up isolated Docker sandbox for dangerous tasks |
| Manual `docker ps` and `docker logs` debugging | AI inspects container logs, status, and ports autonomously |
| Manual database spin-up for local testing | AI launches temporary Postgres / Redis containers on demand |
| Guessing Dockerfile syntax errors | AI builds, validates, and fixes Dockerfiles in real-time |

---

## Prerequisites / Yêu cầu

1. **Docker Engine / Docker Desktop**: Running on your machine.
2. **Node.js**: v18.0.0 or later.

---

## Installation & Configuration / Cài đặt & Cấu hình

### 1. Claude Code CLI

```bash
claude mcp add docker -- npx -y @modelcontextprotocol/server-docker
```

---

### 2. Antigravity IDE (Gemini)

Add to `~/.gemini/config/mcp_config.json`:

```json
{
  "mcpServers": {
    "docker": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-docker"]
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
    "docker": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-docker"]
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
    "docker": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-docker"]
    }
  }
}
```

---

## Verification / Kiểm tra

Ask your agent:
> *"List running Docker containers and their status"*

If the agent returns active containers via Docker API, your Docker MCP is connected and working.
