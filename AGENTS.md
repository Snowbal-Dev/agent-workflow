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

## ⚡ CRITICAL: First-Run Prerequisites Check / Kiểm Tra Điều Kiện Tiên Quyết

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

#### 3. `playwright-mcp` (Browser Automation & E2E Testing Engine)
- **What**: Headless browser automation via Playwright for live web interaction, screenshots, and E2E validation.
- **Why**: Allows AI to visually verify UI, automate web flows, capture console errors, and validate runtime pages without manual testing.
- **Install**: See `mcp/playwright-setup.md`
- **Check**: Try calling `navigate` or check tool availability.
- **Fallback**: Static code testing via Vitest/Jest and manual browser verification.

### Advanced Enterprise Accelerators / Các MCP Mở Rộng
#### 4. `context7` (Live Docs & Zero-Hallucination)
- **What**: Real-time official documentation lookup for modern libraries (React 19, Next.js 15, Tailwind v4, Supabase).
- **Install**: See `mcp/context7-setup.md`

#### 5. `github-mcp-server` (Git & GitHub Automation)
- **What**: Direct GitHub integration for issues, pull requests, diff reviews, and branch management.
- **Install**: See `mcp/github-setup.md`

#### 6. `memory-mcp` (Cross-Session Knowledge Graph Memory)
- **What**: Official `@modelcontextprotocol/server-memory` knowledge graph retaining user preferences and conventions across sessions.
- **Install**: See `mcp/memory-setup.md`

#### 7. `docker-mcp` (Container Sandbox & Local Services)
- **What**: Docker lifecycle management for isolated test runs, temporary databases, and container debugging.
- **Install**: See `mcp/docker-setup.md`

> **Auto-Reminder Protocol**: On FIRST interaction, silently check MCP
> availability. If missing, include setup reminder at END of first response.

---

## 🔄 THE ENTERPRISE WORKFLOW: 6-Phase Development Lifecycle

This system operates as a full-scale **AI Agent Software Engineering Enterprise (59 Skills)**:

```
MACRO-WORKFLOW (Enterprise Feature Lifecycle)

Phase 1        Phase 2        Phase 3        Phase 4        Phase 5        Phase 6
Discover  -->  Design   -->   Plan    -->  Execute   -->  Review   -->  Ship &
& Spec         & Arch         & Isolate     & Build        & Verify       Observe
(4 skills)     (16 skills)    (10 skills)   (11 skills)    (8 skills)     (8 skills)
                                               |
                                    MICRO-WORKFLOW (per task)
                                    1. Quick clarify (Stage 0)
                                    2. Mini plan & contract
                                    3. TDD + Code implementation
                                    4. Multi-axis review
                                    5. Verification with evidence
                                    6. Git commit
```

**Small task** = Run one of the 5 Micro-Workflows below
**Large feature** = All 6 Macro phases, each spawning Micro-Workflows

### 🔬 THE 5 OPERATIONAL MICRO-WORKFLOWS (Per Task Execution)

Every individual task or sub-problem MUST follow its dedicated Micro-Loop:

1. **Feature Task Loop** (Small feature / task addition):
   `requirements-interview` (Quick clarify edge cases) ➔ `using-git-worktrees` (Isolate branch) ➔ `tdd-workflow` (Red test) ➔ `incremental-delivery` + `vercel-react-best-practices` (Green code) ➔ `simplify-code` (Remove bloat) ➔ `code-review` (Multi-axis check) ➔ `verification-before-completion` (Evidence green) ➔ `finishing-a-development-branch` (Merge).

2. **Hard Bug Diagnosis Loop** (Bugs, errors, regressions):
   `diagnose-bug` (Reproduce ➔ Minimize ➔ Hypothesize) ➔ `debug-issue` (Trace call tree via Graph) ➔ `build-error-resolver` (Minimal-diff compile fix) ➔ `tdd-workflow` (Regression test) ➔ `verification-before-completion`.

3. **Data Contract & State Loop** (Database, API schemas, caching):
   `api-and-interface-design` (Zod schemas & contracts) ➔ `supabase` (SQL migration + RLS) ➔ `supabase-postgres-best-practices` (Index & query tuning) ➔ `tanstack-query-best-practices` (Server cache & optimistic UI) ➔ `zustand-state-management` (Client UI store).

4. **UI/UX Crafting Loop** (Components & visuals):
   `huashu-design` (3 high-fidelity directions) ➔ User picks ➔ `apple-design` / `ui-ux-pro-max` (Design system) ➔ `responsive-design` (Container queries) ➔ `liquid-glass-frosted` / `motion-3d` (Visual polish) ➔ `web-design-guidelines` (WCAG compliance).

5. **E2E & Release Loop** (Quality gate & shipping):
   `playwright-best-practices` (E2E headless browser test) ➔ `security-audit` (Vulnerability & RLS scan) ➔ `ci-cd-and-automation` (GitHub Actions workflow) ➔ `observability-and-instrumentation` (Sentry & telemetry) ➔ `deploy-to-vercel`.

---

## 🧭 AUTO-ROUTING TABLE: When to Invoke Which Skill (59 Skills)

**YOU DO NOT WAIT for the user to name a skill.** Detect intent, invoke automatically.

### Phase 1: Product Discovery & Requirements (4 skills)

| Trigger | Skill | Purpose |
|---|---|---|
| Vague idea, "build X", "I want to make..." | `brainstorming` | Structured exploration |
| Unclear requirements, edge cases | `requirements-interview` | BA-style interview |
| Expanding options before choosing | `idea-expansion` | Divergent thinking |
| Stress-testing a plan, "grill me" | `grill-me` | Surface flawed assumptions |

### Phase 2: Architecture & Design (16 skills)

| Trigger | Skill | Purpose |
|---|---|---|
| Architectural decisions, domain model | `design-and-document` | ADR + CONTEXT.md |
| Code structure, module boundaries | `improve-architecture` | Coupling detection |
| API design, Zod schemas, RPC contracts | `api-and-interface-design` | Type-safe REST/RPC contracts |
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

### Phase 3: Planning, State Architecture & Isolation (10 skills)

| Trigger | Skill | Purpose |
|---|---|---|
| Breaking epic into tasks | `plan-tasks` | Task chain decomposition |
| Server data caching, TanStack Query | `tanstack-query-best-practices` | Server cache & optimistic updates |
| Client UI state, store slices, persist | `zustand-state-management` | Lightweight client store |
| Complex React state strategy | `react-state-management` | Global state architecture |
| Multi-language, i18n, translations | `internationalization-i18n` | Locale & translation setup |
| Need isolated workspace | `using-git-worktrees` | Git worktree creation |
| 2+ independent parallel tasks | `dispatching-parallel-agents` | Subagent fan-out |
| Background principle for ALL code | `karpathy-guidelines` | Anti-overengineering |
| Understanding existing code | `explore-codebase` | Knowledge Graph navigation |
| Need new capability | `find-skills` | Skill discovery |

### Phase 4: Implementation & Engineering (11 skills)

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

### Phase 5: Review, Hardening & QA Automation (8 skills)

| Trigger | Skill | Purpose |
|---|---|---|
| E2E browser test, user journeys | `playwright-best-practices` | Playwright browser automation |
| Code ready for review | `code-review` | Multi-axis review |
| Analyzing diff impact | `review-changes` | Impact radius analysis |
| Simplification needed | `simplify-code` | Remove abstractions |
| Structural refactoring | `refactor-safely` | Dependency-aware |
| Auth, user input, sensitive data | `security-audit` | RLS, JWT, XSS scan |
| Pre-launch checklist | `tester` | Readiness + rollback |
| Claiming "done" or "fixed" | `verification-before-completion` | Evidence required |

### Phase 6: Ship, CI/CD, Observability & Operations (8 skills)

| Trigger | Skill | Purpose |
|---|---|---|
| GitHub Actions, CI/CD pipeline | `ci-cd-and-automation` | PR checks, build cache, release |
| Production logs, errors, telemetry | `observability-and-instrumentation` | Sentry, logs, metrics, alerts |
| SEO optimization | `seo-audit` | Meta, OG, JSON-LD |
| Full site audit (260+ rules) | `audit-website` | Squirrelscan scan |
| Deploying to Vercel | `deploy-to-vercel` | Preview/production |
| Vercel CLI automation | `vercel-cli-with-tokens` | Token-based CI/CD |
| Merging feature branch | `finishing-a-development-branch` | Clean merge + PR |
| Documenting architecture | `document-decisions` | Technical docs |

### Universal Meta (2 skills)

| Trigger | Skill | Purpose |
|---|---|---|
| New session start | `using-superpowers` | Initialize tools |
| "caveman", "be brief" | `caveman-mode` | Compressed responses |

---

## 🌳 WORKFLOW DECISION TREE

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
Is it a new feature/system? -- YES --> Phase 1 --> 2 --> 3 --> 4 --> 5 --> 6
        |
        NO
        |
        v
Is it code review/testing? --- YES --> Phase 5 (code-review/playwright/security)
        |
        NO
        |
        v
Is it CI/CD, deploy, monitor?- YES --> Phase 6 (ci-cd/observability/deploy)
        |
        NO
        |
        v
Answer directly, invoke relevant skills as needed
```

---

## 🔒 IMMUTABLE CONSTITUTIONAL RULES (Hệ Thống Quy Tắc Bất Biến)

Every agent MUST comply with the rules located in `rules/` and `.agents/rules/`:

1. **STAGE 0 CLARIFICATION (`rules/disciplined-reasoning.md`)**:
   NEVER assume or guess user requirements. If any ambiguity exists, STOP and ask.
   Only proceed when 100% clear.
2. **KARPATHY SIMPLICITY & SURGICAL CHANGES (`rules/disciplined-reasoning.md`)**:
   Prioritize extreme simplicity. 50 lines of clean code beat 200 lines of abstractions.
   Only touch what is strictly necessary. Never touch or refactor unrelated working code.
3. **TYPESCRIPT STRICT & ANTI-CHEAT (`rules/typescript.md`)**:
   - **NO `any`**: Use `unknown` with safe Type Narrowing.
   - **NO CHEATING ASSERTIONS**: Cấm `as any` or `as unknown as T`.
   - **NO COMPILER SUPPRESSION**: ABSOLUTELY NO `// @ts-ignore` or `// @ts-nocheck`.
   - **EXPLICIT RETURN TYPES**: Required for all exported functions and APIs.
4. **VERIFICATION WITH HARD EVIDENCE (`verification-before-completion`)**:
   NEVER claim work is done without running verification commands and presenting real green test output.
5. **KNOWLEDGE GRAPH FIRST (`code-review-graph`)**:
   Always query the Knowledge Graph before falling back to manual grep/glob.
6. **SECURITY & ZERO-SECRET LEAK (`rules/typescript/security.md`)**:
   Never hardcode keys/tokens. Always enforce Supabase Row Level Security (RLS).
7. **DECISION DOCUMENTATION (`rules/typescript/patterns.md`)**:
   Always record architectural decisions and schema changes in living docs.

---
## 📊 MCP TOOLS: code-review-graph

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

## 👥 FOR HUMANS: Quick Start

**agent-workflow-skill** is a complete, self-contained AI Agent Software
Development Agency featuring **59 skills** organized into a 6-phase enterprise
lifecycle for React + Vite + Supabase + Vercel.

You DON'T need to manually invoke skills. The AI reads this file and
automatically routes your request to the right skill at the right time.

Just talk naturally:
- "Build me a profile page" ➔ AI runs Phase 1 ➔ 2 ➔ 3 ➔ 4 ➔ 5
- "Fix this crash" ➔ AI runs Phase 4 ➔ 5
- "Set up CI/CD & monitoring" ➔ AI runs Phase 6
- "Review my code" ➔ AI runs Phase 5

See `README.md` for full documentation and architectural guides.