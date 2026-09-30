# Agent Workflow Skill — Claude Code Configuration

> Read `AGENTS.md` first for the complete workflow. This file adds
> Claude Code-specific configuration.

## Skill Discovery

Claude Code reads skills from `skills/` directory. Each SKILL.md contains
the full instructions for that skill.

## MCP Tools: code-review-graph

ALWAYS use these MCP tools BEFORE grep/glob/read for code exploration:

- `detect_changes` — Risk-scored change analysis
- `get_review_context` — Token-efficient source snippets
- `get_impact_radius` — Blast radius of changes
- `get_affected_flows` — Impacted execution paths
- `query_graph` — Trace callers, callees, imports, tests
- `semantic_search_nodes` — Find functions/classes by keyword
- `get_architecture_overview` — High-level structure

Fall back to Grep/Glob/Read only when graph doesn't cover your needs.

## Stack

- React / React Native + Vite + Supabase + Vercel
- TypeScript strict mode
- All database operations through Supabase client or MCP

## Workflow

Refer to `AGENTS.md` for the complete 6-phase development lifecycle,
auto-routing table, and decision tree. That file is the single source
of truth for all workflow orchestration across all AI platforms.
