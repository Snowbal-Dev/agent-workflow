# Setup Guide: GitHub MCP Server
# Hướng Dẫn Cài Đặt: MCP Server GitHub

## What is GitHub MCP Server? / Đây là gì?

An official Model Context Protocol server that bridges your AI agent directly with GitHub repositories: read issues, create pull requests, inspect commit history, review diffs, manage branches, and automate release workflows directly from chat.

MCP server chính thức kết nối trực tiếp AI agent với kho mã nguồn GitHub: đọc issue, tạo pull request, xem lịch sử commit, phân tích diff, quản lý branch và tự động hóa quy trình phát hành code mà không cần rời khỏi môi trường làm việc.

---

## Why install it? / Tại sao cần cài?

| Without / Không có | With / Có |
|---|---|
| Manually open browser to read Issues | AI reads issue descriptions and acceptance criteria directly |
| Manually push branch and write PR description | AI creates PR, links issues, and formats markdown changelogs |
| Manually check PR review comments | AI fetches review comments and fixes code accordingly |
| Copy-pasting commit hashes and diffs | AI runs full Git & GitHub workflows seamlessly |

---

## Prerequisites / Yêu cầu

1. A **GitHub Personal Access Token (Classic or Fine-Grained)** with `repo` permissions.
2. **Docker** (Option 1) OR **Node.js 18+** (Option 2).

---

## Installation & Configuration / Cài đặt & Cấu hình

### Option 1: Docker (Official GitHub Container - Recommended)

#### Claude Code CLI:
```bash
claude mcp add github -e GITHUB_PERSONAL_ACCESS_TOKEN=ghp_your_token -- docker run -i --rm -e GITHUB_PERSONAL_ACCESS_TOKEN ghcr.io/github/github-mcp-server
```

#### Antigravity / Cursor / Windsurf (`mcp_config.json`):
```json
{
  "mcpServers": {
    "github-mcp-server": {
      "command": "docker",
      "args": [
        "run",
        "-i",
        "--rm",
        "-e",
        "GITHUB_PERSONAL_ACCESS_TOKEN",
        "ghcr.io/github/github-mcp-server"
      ],
      "env": {
        "GITHUB_PERSONAL_ACCESS_TOKEN": "ghp_your_token_here"
      }
    }
  }
}
```

---

### Option 2: npm / npx (`@modelcontextprotocol/server-github`)

#### Claude Code CLI:
```bash
claude mcp add github -e GITHUB_PERSONAL_ACCESS_TOKEN=ghp_your_token -- npx -y @modelcontextprotocol/server-github
```

#### Antigravity / Cursor / Windsurf (`mcp_config.json`):
```json
{
  "mcpServers": {
    "github-mcp-server": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": {
        "GITHUB_PERSONAL_ACCESS_TOKEN": "ghp_your_token_here"
      }
    }
  }
}
```

---

## Verification / Kiểm tra

Ask your agent:
> *"List the recent open issues in my repository"*

If the agent returns your repository issues list, GitHub MCP is connected and working.
