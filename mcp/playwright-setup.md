# Setup Guide: Playwright MCP Server
# Hướng Dẫn Cài Đặt: MCP Server Playwright (@playwright/mcp)

## What is Playwright MCP? / Đây là gì?

An official Model Context Protocol (MCP) server that empowers your AI coding agent with real browser automation capabilities using Microsoft Playwright. It gives your AI agent "eyes and hands" to navigate web pages, click elements, fill forms, execute scripts, and take screenshots directly during development.

Một MCP server chuẩn giúp cung cấp khả năng tự động hóa trình duyệt web thực tế cho AI agent thông qua Microsoft Playwright. Nó trao cho AI "đôi mắt và bàn tay" để mở trang web, tương tác click, điền form, chạy script và chụp ảnh màn hình ngay trong chu trình lập trình.

---

## Why install it? / Tại sao cần cài?

| Without / Không có | With / Có |
|---|---|
| AI writes E2E tests blindly | AI runs and verifies tests in a real headless browser |
| Can only guess if UI looks right | Takes real screenshots to verify responsive layouts & styles |
| Manual clicking & testing forms | AI automates login, form filling, and flow verification |
| Cannot see console errors | Captures runtime browser console logs and failed network requests |
| Requires manual browser switching | Full hands-free verification from inside your IDE / CLI |

---

## Prerequisites / Yêu cầu

1. **Node.js**: v18.0.0 or later installed on your machine.
2. **Playwright Browsers**: Automatic on first run via `npx -y @playwright/mcp` (or run `npx playwright install chromium`).

---

## Installation & Configuration / Cài đặt & Cấu hình

### 1. Claude Code CLI (Recommended / Khuyến nghị)

Run the one-liner in your terminal:
```bash
claude mcp add playwright-mcp -- npx -y @playwright/mcp
```

---

### 2. Antigravity IDE (Gemini)

Add to your global or project MCP configuration file (`~/.gemini/config/mcp_config.json`):

```json
{
  "mcpServers": {
    "playwright-mcp": {
      "command": "npx",
      "args": ["-y", "@playwright/mcp"]
    }
  }
}
```

---

### 3. Cursor & Windsurf

Add to your project's `.cursor/mcp.json` or IDE Settings -> MCP:

```json
{
  "mcpServers": {
    "playwright-mcp": {
      "command": "npx",
      "args": ["-y", "@playwright/mcp"]
    }
  }
}
```

---

### 4. Claude Desktop

Add to `claude_desktop_config.json` (located in `%APPDATA%\Claude\claude_desktop_config.json` on Windows or `~/Library/Application Support/Claude/` on macOS):

```json
{
  "mcpServers": {
    "playwright-mcp": {
      "command": "npx",
      "args": ["-y", "@playwright/mcp"]
    }
  }
}
```

---

## Available Tools & Capabilities / Danh Sách Công Cụ Khả Dụng

When connected, the AI agent has direct access to the following tools:

- **`navigate`**: Navigate to any URL (including local development servers like `http://localhost:5173`).
- **`click`**: Click buttons, links, or specific CSS selectors with automatic element waiting.
- **`fill` / `type`**: Type text into input fields, textareas, and submit forms.
- **`screenshot`**: Capture high-resolution viewport or full-page screenshots for visual inspection.
- **`evaluate`**: Run custom JavaScript directly within the browser context.
- **`get_console_logs`**: Read browser console warnings, errors, and uncaught exceptions.

---

## Pairing with Skills / Kết Hợp Cùng Kỹ Năng

This MCP engine pairs seamlessly with:
1. **`skills/playwright-best-practices`**: Formulates maintainable, resilient E2E test suites with locator strategies and page-object models.
2. **Phase 4 (Automated Verification)**: Validates newly built frontend components in runtime before committing code.

---

## Verification / Kiểm tra

Ask your agent:
> *"Navigate to http://localhost:5173 and take a screenshot"*

If the agent returns a screenshot or browser log, your Playwright MCP is successfully connected and ready.

---

## Fallback / Dự phòng

If Playwright MCP cannot be launched (e.g. headless environment without browser binaries), the agent will fall back to static unit testing via Vitest/Jest and manual test review.
