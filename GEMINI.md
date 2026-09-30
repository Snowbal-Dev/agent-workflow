# Agent Workflow Skill — Gemini / Antigravity Configuration

> Read `AGENTS.md` first for the complete workflow. This file adds
> Gemini/Antigravity-specific configuration.

## Skill Loading

All skills are in `skills/` directory. Each skill has a `SKILL.md` file
with YAML frontmatter (name, description) that Antigravity auto-discovers.

## MCP Tools: code-review-graph

**IMPORTANT: This project has a knowledge graph. ALWAYS use the
code-review-graph MCP tools BEFORE using Grep/Glob/Read to explore
the codebase.**

### Key Tools

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

### Workflow

1. The graph auto-updates on file changes (via hooks).
2. Use `detect_changes` for code review.
3. Use `get_affected_flows` to understand impact.
4. Use `query_graph` pattern="tests_for" to check coverage.

Fall back to Grep/Glob/Read only when the graph does not cover what you need.

## Language Rule

Respond in the same language the user uses. If user writes in Vietnamese,
respond in Vietnamese. If in English, respond in English.

## Refer to AGENTS.md

For the complete 6-phase workflow, auto-routing table, decision tree,
and skill catalog, see `AGENTS.md`. That file is the single source of truth
for all workflow orchestration.
