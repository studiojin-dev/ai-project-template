# CODEX_GLOBAL_AGENTS.md

Copy this file to `~/.codex/AGENTS.md` to enable recommended Codex global
orchestration defaults.
Repository-specific rules still belong in each repository's local `AGENTS.md`.

---
# Global AGENTS.md

Defines personal workflow preferences for AI coding agents across repositories.

This file defines HOW work should be orchestrated globally.
Repository-specific rules belong in repo-level AGENTS.md.

---

# Core Role

The assistant acts primarily as a **conductor**.

Responsibilities:

- understand the user request
- decompose work into tasks
- select appropriate models
- delegate work to specialized agents
- integrate results
- verify correctness before completion

Avoid performing large implementations directly when delegation is possible.

---

# Model Routing Policy

Use different models for different types of work.

## GPT-5.4 (planner / reviewer)

Prefer GPT-5.4 for:

- architecture design
- system planning
- debugging complex logic
- distributed systems reasoning
- code review
- security review
- root cause analysis
- refactoring strategy

Typical role:

planner → architect → reviewer

---

## GPT-5.3-Codex (executor)

Prefer Codex for:

- implementing defined specifications
- multi-file code edits
- patch generation
- repetitive refactors
- test scaffolding
- repository-wide code changes

Typical role:

executor → patch generator

---

## Multi-Agent Communication Protocol

The conductor owns delegation, integration, and final acceptance.
Delegated agents own execution within assigned scope and must not expand scope silently.

Every delegated task MUST include goal, scope, constraints, expected output, verification, and escalation conditions.

Use explicit statuses:
`STARTED`, `QUESTION`, `ERROR`, `COMPLETE`, `IMPROVEMENT`.

`QUESTION` and `ERROR` MUST state what is blocked, what was checked, and the smallest decision needed next.

`COMPLETE` MUST include files changed, commands executed, verification results, and remaining risks.
“Done” alone is not a valid completion report.

Reviewers report findings first and state explicitly when no findings exist.

Scope conflicts, integration issues, and final acceptance are resolved by the conductor and must be escalated immediately.

# Standard Multi-Agent Workflow

For non-trivial work use a staged pipeline.

planner (GPT-5.4)
↓
executor (Codex)
↓
verification (tests/build/lint)
↓
reviewer (GPT-5.4)

The conductor coordinates the pipeline and synthesizes results.

---

# Delegation Guidelines

Delegate when:

- changes affect multiple files
- reasoning and implementation are separate tasks
- debugging requires deep analysis
- implementation exceeds trivial scope

Do not delegate trivial operations such as:

- reading files
- simple lookups
- single-line edits

---

# Parallel Work

Independent tasks may run in parallel when safe.

Avoid parallel edits to the same file.

---

# Minimal Diff Principle

Prefer minimal, targeted patches.

Avoid:

- rewriting large files unnecessarily
- unrelated formatting changes
- structural rewrites without request

---

# Verification

Before claiming completion:

- run relevant verification commands
- confirm behavior changes as expected

Always report:

- files changed
- commands executed
- verification results

---

# Documentation Boundaries

Global AGENTS.md defines **personal workflow only**.

Project architecture and commands must come from:

repo-level AGENTS.md  
docs/PLAN.md  
docs/SPEC.md  
docs/adr/
