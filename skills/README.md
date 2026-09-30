# Skills Directory / Thư Mục Kỹ Năng

This directory contains 51 AI agent skills organized into 6 workflow phases.

## Name Mapping / Bảng Đổi Tên

Some skills were originally named in Vietnamese. This table maps old names
to new English names for reference:

| Old Name (Vietnamese) | New Name (English) | Phase |
|---|---|---|
| `bat-benh-sua-loi` | `diagnose-bug` | Phase 4: Implementation |
| `bien-ai-thanh-BA` | `requirements-interview` | Phase 1: Discovery |
| `cai-thien-cau-truc` | `improve-architecture` | Phase 2: Design |
| `danh-gia-code` | `code-review` | Phase 5: Review |
| `di-theo-lo-trinh` | `incremental-delivery` | Phase 4: Implementation |
| `don-gian-hoa-code` | `simplify-code` | Phase 5: Review |
| `kiem-tra-bao-mat` | `security-audit` | Phase 5: Review |
| `len-ke-hoach` | `plan-tasks` | Phase 3: Planning |
| `mo-rong-idea` | `idea-expansion` | Phase 1: Discovery |
| `phong-van-toi` | `grill-me` | Phase 1: Discovery |
| `thiet-ke-va-luu-docs` | `design-and-document` | Phase 2: Design |
| `tra-loi-ngan-gon` | `caveman-mode` | Universal Meta |
| `viet-tai-lieu-khi-thay-doi-cau-truc-code` | `document-decisions` | Phase 6: Ship |

## How Skills Work / Cách Skill Hoạt Động

Each skill directory contains a `SKILL.md` file with:
1. **YAML frontmatter**: `name` and `description` (used for auto-discovery)
2. **Instructions**: Step-by-step guide for the AI to follow

AI agents automatically discover and invoke skills based on the routing
table in `AGENTS.md`. Users do not need to manually call skills.

## Phase Organization / Tổ Chức Theo Giai Đoạn

### Phase 1: Product Discovery (4)
brainstorming, requirements-interview, idea-expansion, grill-me

### Phase 2: Architecture & Design (15+)
design-and-document, improve-architecture, supabase,
supabase-postgres-best-practices, ui-ux-pro-max, frontend-design,
apple-design, web-design, web-design-guidelines, responsive-design,
mobile-ios-design, mobile-android-design, liquid-glass-frosted,
motion-3d, canvas-design, huashu-design

### Phase 3: Planning & Isolation (6)
plan-tasks, using-git-worktrees, dispatching-parallel-agents,
karpathy-guidelines, explore-codebase, find-skills

### Phase 4: Implementation (11)
incremental-delivery, subagent-driven-development, tdd-workflow,
vercel-react-best-practices, vercel-react-view-transitions,
react-native-design, vercel-react-native-skills,
diagnose-bug, debug-issue, build-error-resolver

### Phase 5: Review & Hardening (7)
code-review, review-changes, simplify-code, refactor-safely,
security-audit, tester, verification-before-completion

### Phase 6: Ship & Deploy (6)
seo-audit, audit-website, deploy-to-vercel, vercel-cli-with-tokens,
finishing-a-development-branch, document-decisions

### Universal Meta (2)
using-superpowers, caveman-mode
