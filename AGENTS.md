# Agent Workflow Skill — Universal Agent Instructions
# Bộ Kỹ Năng Quy Trình Agent — Hướng Dẫn Vạn Năng Cho Mọi AI

> **For AI Agents**: This file is your operating manual. Read it COMPLETELY before
> responding to ANY user request. It defines how you work, what tools you have,
> and what workflow to follow.
>
> **Cho AI Agents**: Đây là cẩm nang vận hành của bạn. Hãy đọc TOÀN BỘ trước khi
> trả lời BẤT KỲ yêu cầu nào. File này định nghĩa cách bạn làm việc, công cụ
> bạn có, và quy trình cần tuân thủ.

---

## 🚨 CRITICAL: First-Run Prerequisites Check / Kiểm Tra Điều Kiện Tiên Quyết

**BEFORE doing ANY work**, check if these MCP servers are available.
If not, PROACTIVELY tell the user to install them.

### Required MCP Servers / Các MCP Server Bắt Buộc

#### 1. `code-review-graph` (Knowledge Graph Engine)
- **What**: Builds a dependency graph of your codebase for instant navigation,
  impact analysis, and smart code review.
- **Why**: Without it, code exploration is 5-10x slower and uses 5-10x more tokens.
- **Install**: See `mcp/code-review-graph-setup.md`
- **Check**: Try calling `list_graph_stats` — if it responds, server is running.
- **Fallback**: If unavailable, use grep/glob/file-reading. Skills still work.

#### 2. `supabase` (Supabase MCP)
- **What**: Direct database access, migration management, RLS inspection.
- **Why**: Enables AI to inspect schemas, run queries, manage migrations.
- **Install**: See `mcp/supabase-setup.md`
- **Check**: Try calling `list_tables` — if it responds, server is running.
- **Fallback**: Work with SQL files and Supabase CLI directly.

> **Auto-Reminder Protocol**: On FIRST interaction, silently check MCP
> availability. If missing, include setup reminder at END of first response.

---

## 🧠 THE WORKFLOW: 6-Phase Development Lifecycle

```
MACRO-WORKFLOW (Epic/Feature lifecycle)

Phase 1        Phase 2        Phase 3        Phase 4        Phase 5   Phase 6
Discover  -->  Design   -->   Plan    -->  Execute   -->  Review  --> Ship
& Spec         & Arch         & Isolate     & Build        & Harden   & Deploy
(4 skills)     (15 skills)    (6 skills)    (11 skills)    (7 skills) (6 skills)
                                               |
                                    MICRO-WORKFLOW (per task)
                                    1. Quick clarify
                                    2. Mini plan
                                    3. TDD + Code
                                    4. Review
                                    5. Verify
                                    6. Commit
```

**Small task** = Only Micro-Workflow (2-4 skills)
**Large feature** = All 6 Macro phases, each spawning Micro-Workflows

---

## 📋 AUTO-ROUTING TABLE: When to Invoke Which Skill

**YOU DO NOT WAIT for the user to name a skill.** Detect intent, invoke automatically.

### Phase 1: Product Discovery

| Trigger | Skill | Purpose |
|---|---|---|
| Vague idea, "build X", "I want to make..." | `brainstorming` | Structured exploration |
| Unclear requirements, edge cases | `requirements-interview` | BA-style interview |
| Expanding options before choosing | `idea-expansion` | Divergent thinking |
| Stress-testing a plan, "grill me" | `grill-me` | Surface flawed assumptions |

### Phase 2: Architecture & Design

| Trigger | Skill | Purpose |
|---|---|---|
| Architectural decisions, domain model | `design-and-document` | ADR + CONTEXT.md |
| Code structure, module boundaries | `improve-architecture` | Coupling detection |
| Supabase schema, RLS, Auth | `supabase` | Full-stack Supabase |
| DB optimization, indexes, queries | `supabase-postgres-best-practices` | Postgres tuning |
| Visual direction, colors, typography | `ui-ux-pro-max` | 50+ styles reference |
| Distinctive UI design | `frontend-design` | Non-generic visuals |
| Apple-style design | `apple-design` | HIG principles |
| Web standards, accessibility | `web-design` + `web-design-guidelines` | WCAG compliance |
| Multi-screen responsive layout | `responsive-design` | Container queries |
| iOS interface (React Native) | `mobile-ios-design` | SwiftUI/HIG patterns |
| Android Material (React Native) | `mobile-android-design` | Material Design 3 |
| Frosted glass / glassmorphism | `liquid-glass-frosted` | Blur + refraction |
| 3D animations, Three.js, GSAP | `motion-3d` | ThreeJS, Shaders |
| Visual assets, posters, banners | `canvas-design` | Code-generated graphics |
| HTML prototype (3 directions) | `huashu-design` | High-fidelity prototyping |

### Phase 3: Planning & Isolation

| Trigger | Skill | Purpose |
|---|---|---|
| Breaking epic into tasks | `plan-tasks` | Task chain decomposition |
| Need isolated workspace | `using-git-worktrees` | Git worktree creation |
| 2+ independent parallel tasks | `dispatching-parallel-agents` | Subagent fan-out |
| Background principle for ALL code | `karpathy-guidelines` | Anti-overengineering |
| Understanding existing code | `explore-codebase` | Knowledge Graph nav |
| Need new capability | `find-skills` | Skill discovery |

### Phase 4: Implementation

| Trigger | Skill | Purpose |
|---|---|---|
| Writing code incrementally | `incremental-delivery` | Verified small steps |
| Delegating to subagents | `subagent-driven-development` | Parallel execution |
| Tests-first development | `tdd-workflow` | Red-Green-Refactor |
| React/Vite performance | `vercel-react-best-practices` | Render optimization |
| Page transitions | `vercel-react-view-transitions` | View Transitions API |
| React Native components | `react-native-design` | Reanimated patterns |
| Mobile performance | `vercel-react-native-skills` | FlashList, memory |
| Hard bug, unexpected behavior | `diagnose-bug` | Reproduce-minimize-fix |
| Tracing through dependencies | `debug-issue` | Graph-powered tracing |
| TypeScript/Vite build error | `build-error-resolver` | Minimal-diff green |

### Phase 5: Review & Hardening

| Trigger | Skill | Purpose |
|---|---|---|
| Code ready for review | `code-review` | Multi-axis review |
| Analyzing diff impact | `review-changes` | Impact radius analysis |
| Simplification needed | `simplify-code` | Remove abstractions |
| Structural refactoring | `refactor-safely` | Dependency-aware |
| Auth, user input, sensitive data | `security-audit` | RLS, JWT, XSS scan |
| Pre-launch checklist | `tester` | Readiness + rollback |
| Claiming "done" or "fixed" | `verification-before-completion` | Evidence required |

### Phase 6: Ship & Deploy

| Trigger | Skill | Purpose |
|---|---|---|
| SEO optimization | `seo-audit` | Meta, OG, JSON-LD |
| Full site audit (260+ rules) | `audit-website` | Squirrelscan scan |
| Deploying to Vercel | `deploy-to-vercel` | Preview/production |
| Vercel CLI automation | `vercel-cli-with-tokens` | Token-based CI/CD |
| Merging feature branch | `finishing-a-development-branch` | Clean merge + PR |
| Documenting architecture | `document-decisions` | Technical docs |

### Universal Meta

| Trigger | Skill | Purpose |
|---|---|---|
| New session start | `using-superpowers` | Initialize tools |
| "caveman", "be brief" | `caveman-mode` | Compressed responses |

---

## 🔄 WORKFLOW DECISION TREE

```
User sends a request
        |
        v
Is it a bug fix or error? ---- YES --> Phase 4 (diagnose/debug/build-error)
        |                               Then Phase 5 (verify)
        NO
        |
        v
Is it a small clear change? -- YES --> Phase 4 (incremental + tdd)
        |                              Then Phase 5 (verify)
        NO
        |
        v
Is it a new feature? --------- YES --> Phase 1 --> 2 --> 3 --> 4 --> 5 --> 6
        |
        NO
        |
        v
Is it code review? ----------- YES --> Phase 5 (code-review/simplify/refactor)
        |
        NO
        |
        v
Is it deployment/SEO? -------- YES --> Phase 6 (seo/deploy/audit)
        |
        NO
        |
        v
Answer directly, invoke relevant skills as needed
```

---

## 🛡️ IMMUTABLE RULES

1. **NEVER skip verification.** Run `verification-before-completion` before
   claiming work is done. Show actual green test output.
2. **NEVER assume requirements.** If ambiguous, ASK before coding.
3. **ALWAYS use Knowledge Graph first** (if `code-review-graph` available)
   before grep/glob for code exploration.
4. **ALWAYS follow incremental delivery.** Each commit must compile and pass.
5. **ALWAYS document decisions.** Use `document-decisions` for API/schema changes.
6. **ALWAYS check MCP prerequisites** on first session interaction.

---

## 🔧 MCP TOOLS: code-review-graph

ALWAYS use these tools BEFORE Grep/Glob/Read to explore the codebase:

| Tool | Use when |
|------|----------|
| `detect_changes` | Reviewing code changes — risk-scored analysis |
| `get_review_context` | Token-efficient source snippets for review |
| `get_impact_radius` | Understanding blast radius of a change |
| `get_affected_flows` | Finding impacted execution paths |
| `query_graph` | Tracing callers, callees, imports, tests |
| `semantic_search_nodes` | Finding functions/classes by keyword |
| `get_architecture_overview` | High-level codebase structure |
| `refactor_tool` | Planning renames, finding dead code |

---

## 📖 FOR HUMANS: Quick Start

**agent-workflow-skill** is a set of 51 AI agent skills organized into a
6-phase development workflow for React + Vite + Supabase + Vercel.

You DON'T need to manually invoke skills. The AI reads this file and
automatically routes your request to the right skill at the right time.

Just talk naturally:
- "Build me a profile page" → AI runs Phase 1→2→3→4→5
- "Fix this crash" → AI runs Phase 4→5
- "Deploy to production" → AI runs Phase 6
- "Review my code" → AI runs Phase 5

See `README.md` for full installation instructions.
