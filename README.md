# 🚀 Agent Workflow Skill
# Bộ Kỹ Năng Quy Trình Agent

[![Skills](https://img.shields.io/badge/skills-51-blue)]()
[![Stack](https://img.shields.io/badge/stack-React%20%2B%20Vite%20%2B%20Supabase-green)]()
[![Harness](https://img.shields.io/badge/harness-7%2B%20supported-purple)]()

> **EN**: A production-grade AI agent skill pack with 51 skills organized into
> a 6-phase software development workflow. Designed for **React/React Native +
> Vite + Supabase + Vercel** projects. Works with Antigravity, Claude Code,
> Cursor, Windsurf, Codex, GPT, Grok, and any agent that reads `AGENTS.md`.
>
> **VN**: Bộ kỹ năng AI agent cấp sản xuất với 51 skills được tổ chức thành
> quy trình phát triển phần mềm 6 giai đoạn. Thiết kế cho dự án **React/React
> Native + Vite + Supabase + Vercel**. Tương thích Antigravity, Claude Code,
> Cursor, Windsurf, Codex, GPT, Grok và mọi agent đọc `AGENTS.md`.

---

## ✨ What Makes This Different? / Điểm Khác Biệt

### vs Generic Skill Packs (ECC, Superpowers...)

| Feature | Generic Packs | agent-workflow-skill |
|---|---|---|
| Stack focus | Everything (generic) | React + RN + Vite + Supabase |
| Workflow | Skills are standalone | **6-phase lifecycle with auto-routing** |
| AI autonomy | User must invoke skills | **AI auto-detects intent & invokes** |
| Design skills | 0-2 | **15+ (Apple, Material, Frosted Glass, 3D...)** |
| Code intelligence | grep/glob only | **Knowledge Graph (code-review-graph)** |
| Multi-harness | 1-3 platforms | **7+ platforms** |

### The Key Innovation: AI-Driven Workflow / Đổi Mới Cốt Lõi

**The user does NOT need to know skill names.** The `AGENTS.md` file contains
a complete auto-routing table that maps user intent → correct skill → correct
workflow phase. The AI reads this once and knows exactly what to do.

**Người dùng KHÔNG CẦN biết tên skill.** File `AGENTS.md` chứa bảng định tuyến
tự động ánh xạ ý định người dùng → skill đúng → giai đoạn workflow đúng.
AI đọc file này 1 lần và biết chính xác phải làm gì.

---

## 📦 Installation / Cài Đặt

### Method 1: Copy to your project / Copy vào dự án

```bash
# Clone this repo
git clone https://github.com/YOUR_USERNAME/agent-workflow-skill.git

# Copy skills into your project
cp -r agent-workflow-skill/skills/ YOUR_PROJECT/.agents/skills/
cp -r agent-workflow-skill/rules/ YOUR_PROJECT/.agents/rules/
cp agent-workflow-skill/AGENTS.md YOUR_PROJECT/AGENTS.md
cp agent-workflow-skill/GEMINI.md YOUR_PROJECT/GEMINI.md
cp agent-workflow-skill/CLAUDE.md YOUR_PROJECT/CLAUDE.md
cp agent-workflow-skill/.cursorrules YOUR_PROJECT/.cursorrules
```

### Method 2: Use as git submodule

```bash
cd YOUR_PROJECT
git submodule add https://github.com/YOUR_USERNAME/agent-workflow-skill.git .agents
```

### Method 3: Direct download (Windows)

```powershell
git clone https://github.com/YOUR_USERNAME/agent-workflow-skill.git
robocopy agent-workflow-skill\skills YOUR_PROJECT\.agents\skills /E
copy agent-workflow-skill\AGENTS.md YOUR_PROJECT\AGENTS.md
copy agent-workflow-skill\GEMINI.md YOUR_PROJECT\GEMINI.md
```

---

## 🔧 Required: MCP Server Setup / Bắt Buộc: Cài MCP Server

These MCP servers supercharge the workflow. Without them, skills still work
but are slower and less intelligent.

### 1. code-review-graph (Knowledge Graph)

Builds a dependency graph for instant code navigation and impact analysis.

> **Full guide**: See [`mcp/code-review-graph-setup.md`](mcp/code-review-graph-setup.md)

Quick install:
```bash
npm install -g code-review-graph
```

### 2. Supabase MCP (Database Access)

Direct AI access to your Supabase schema, queries, and migrations.

> **Full guide**: See [`mcp/supabase-setup.md`](mcp/supabase-setup.md)

Quick install:
```bash
npm install -g @supabase/mcp-server-supabase
```

> **Don't worry if you skip this step.** The AI will remind you on first
> interaction if MCP servers are missing. Skills gracefully fall back to
> manual methods (grep, SQL files, CLI commands).
>
> **Đừng lo nếu bỏ qua bước này.** AI sẽ tự nhắc bạn trong lần tương tác
> đầu tiên nếu thiếu MCP server. Các skill tự động chuyển sang phương pháp
> thủ công (grep, file SQL, lệnh CLI).

---

## 🧠 The 6-Phase Workflow / Quy Trình 6 Giai Đoạn

```
Phase 1: DISCOVER ──> Phase 2: DESIGN ──> Phase 3: PLAN
(4 skills)            (15 skills)          (6 skills)
Brainstorm ideas      Supabase schema      Break into tasks
Interview user        UI/UX design         Git worktrees
Expand options        Architecture docs    Parallel dispatch
Stress-test plan      Design prototypes    Explore codebase

Phase 4: EXECUTE ──> Phase 5: REVIEW ──> Phase 6: SHIP
(11 skills)           (7 skills)           (6 skills)
TDD + incremental     Code review          SEO optimization
React best practices  Security audit       Site audit (260+)
Diagnose bugs         Refactor safely      Deploy to Vercel
Build error fixes     Verify completion    Document decisions
```

### Small vs Large Tasks / Tác Vụ Nhỏ vs Lớn

- **Bug fix**: Phase 4 (diagnose) → Phase 5 (verify). Done in 5 minutes.
- **New feature**: All 6 phases. Takes hours to days.
- **Code review**: Phase 5 only.
- **Deploy**: Phase 6 only.

The AI automatically determines which phases to run based on your request.

---

## 📁 Directory Structure / Cấu Trúc Thư Mục

```
agent-workflow-skill/
├── AGENTS.md                    # Universal AI instructions (ALL agents read this)
├── GEMINI.md                    # Antigravity/Gemini-specific config
├── CLAUDE.md                    # Claude Code-specific config
├── .cursorrules                 # Cursor config
├── .windsurfrules               # Windsurf config
├── README.md                    # This file (human documentation)
│
├── skills/                      # 51 AI agent skills
│   ├── brainstorming/           # Phase 1: Discovery
│   ├── requirements-interview/  # Phase 1: Deep BA interview
│   ├── idea-expansion/          # Phase 1: Divergent thinking
│   ├── grill-me/                # Phase 1: Stress-test assumptions
│   ├── design-and-document/     # Phase 2: ADR + CONTEXT.md
│   ├── improve-architecture/    # Phase 2: Module boundary analysis
│   ├── supabase/                # Phase 2: Full Supabase design
│   ├── ui-ux-pro-max/           # Phase 2: Design system reference
│   ├── frontend-design/         # Phase 2: Distinctive visual design
│   ├── plan-tasks/              # Phase 3: Task decomposition
│   ├── using-git-worktrees/     # Phase 3: Workspace isolation
│   ├── dispatching-parallel-agents/ # Phase 3: Subagent orchestration
│   ├── incremental-delivery/    # Phase 4: Verified small steps
│   ├── tdd-workflow/            # Phase 4: Red-Green-Refactor
│   ├── diagnose-bug/            # Phase 4: Bug diagnosis loop
│   ├── code-review/             # Phase 5: Multi-axis review
│   ├── security-audit/          # Phase 5: Vulnerability scanning
│   ├── verification-before-completion/ # Phase 5: Evidence gate
│   ├── seo-audit/               # Phase 6: SEO optimization
│   ├── deploy-to-vercel/        # Phase 6: Vercel deployment
│   ├── finishing-a-development-branch/ # Phase 6: Clean merge
│   └── ... (51 total)
│
├── rules/                       # Behavioral rules for AI
│   ├── disciplined-reasoning.md
│   └── ...
│
├── mcp/                         # MCP server setup guides
│   ├── code-review-graph-setup.md
│   └── supabase-setup.md
│
└── templates/                   # Config file templates (future)
```

---

## 🎯 Skill Catalog / Danh Mục Kỹ Năng

### Phase 1: Product Discovery (4 skills)

| Skill | Trigger / Khi nào dùng |
|---|---|
| `brainstorming` | New ideas, "build me X" |
| `requirements-interview` | Unclear requirements |
| `idea-expansion` | Need more options |
| `grill-me` | Stress-test a plan |

### Phase 2: Architecture & Design (15 skills)

| Skill | Trigger / Khi nào dùng |
|---|---|
| `design-and-document` | Architecture decisions |
| `improve-architecture` | Module boundaries |
| `supabase` | Database schema, Auth, RLS |
| `supabase-postgres-best-practices` | Query optimization |
| `ui-ux-pro-max` | Design system reference |
| `frontend-design` | Distinctive visual design |
| `apple-design` | Apple HIG style |
| `web-design` | Web standards |
| `web-design-guidelines` | Accessibility audit |
| `responsive-design` | Multi-screen layouts |
| `mobile-ios-design` | iOS patterns for RN |
| `mobile-android-design` | Material Design 3 for RN |
| `liquid-glass-frosted` | Frosted glass effects |
| `motion-3d` | 3D animations, Three.js |
| `canvas-design` | Graphic design in code |
| `huashu-design` | HTML prototyping |

### Phase 3: Planning & Isolation (6 skills)

| Skill | Trigger / Khi nào dùng |
|---|---|
| `plan-tasks` | Breaking work into tasks |
| `using-git-worktrees` | Isolated workspace |
| `dispatching-parallel-agents` | Parallel task execution |
| `karpathy-guidelines` | Anti-overengineering |
| `explore-codebase` | Code navigation |
| `find-skills` | Discover new skills |

### Phase 4: Implementation (11 skills)

| Skill | Trigger / Khi nào dùng |
|---|---|
| `incremental-delivery` | Small verified steps |
| `subagent-driven-development` | Delegated execution |
| `tdd-workflow` | Tests-first development |
| `vercel-react-best-practices` | React performance |
| `vercel-react-view-transitions` | Page transitions |
| `react-native-design` | RN components |
| `vercel-react-native-skills` | Mobile performance |
| `diagnose-bug` | Hard bug diagnosis |
| `debug-issue` | Dependency tracing |
| `build-error-resolver` | Build error fixes |

### Phase 5: Review & Hardening (7 skills)

| Skill | Trigger / Khi nào dùng |
|---|---|
| `code-review` | Pre-merge review |
| `review-changes` | Diff impact analysis |
| `simplify-code` | Remove complexity |
| `refactor-safely` | Safe refactoring |
| `security-audit` | Vulnerability scan |
| `tester` | Launch readiness |
| `verification-before-completion` | Evidence gate |

### Phase 6: Ship & Deploy (6 skills)

| Skill | Trigger / Khi nào dùng |
|---|---|
| `seo-audit` | SEO optimization |
| `audit-website` | Full site audit |
| `deploy-to-vercel` | Vercel deployment |
| `vercel-cli-with-tokens` | CLI automation |
| `finishing-a-development-branch` | Branch cleanup |
| `document-decisions` | Architecture docs |

### Meta / Universal (2 skills)

| Skill | Trigger / Khi nào dùng |
|---|---|
| `using-superpowers` | Session initialization |
| `caveman-mode` | Compressed responses |

---

## 🤝 Supported Platforms / Nền Tảng Hỗ Trợ

| Platform | Config File | Status |
|---|---|---|
| Antigravity (Google) | `GEMINI.md` | ✅ Full support |
| Claude Code (Anthropic) | `CLAUDE.md` | ✅ Full support |
| Cursor | `.cursorrules` | ✅ Full support |
| Windsurf | `.windsurfrules` | ✅ Full support |
| Codex (OpenAI) | `AGENTS.md` | ✅ Full support |
| GPT / ChatGPT | `AGENTS.md` | ✅ Via AGENTS.md |
| Grok (xAI) | `AGENTS.md` | ✅ Via AGENTS.md |
| Any agent reading AGENTS.md | `AGENTS.md` | ✅ Universal |

---

## 📄 License

MIT License. Use freely in any project.

---

## 🙏 Credits / Nguồn Gốc

Inspired by:
- [obra/superpowers](https://github.com/obra/superpowers) — Multi-harness skill system
- [affaan-m/ECC](https://github.com/affaan-m/ECC) — Engineering Coding Companion
- Real-world production experience with React + Supabase + Vercel stack

Built with ❤️ for developers who want their AI assistants to truly understand
the full software development lifecycle.
