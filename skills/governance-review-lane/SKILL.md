---
name: governance-review-lane
description: Review code, documentation, and workflow changes for ADR compliance, repository policy conformance, documentation completeness, licensing/process requirements, and release readiness. Use when a task changes agent workflow, architecture constraints, CI or release behavior, approval paths, licensing, or other policy-sensitive behavior, or when Codex is asked for governance or compliance review.
---

# Governance Review Lane

## Overview

Use this skill to check whether a change is consistent with the repository's
documented process and decision records.
Stay in review mode by default and ask for missing policy inputs instead of
inventing them.

## Workflow

1. Read the nearest applicable AGENTS.md and any referenced project documents.
2. Identify which policies actually govern the change: ADR workflow, release
   process, documentation requirements, licensing, or approval gates.
3. Check for:
   - decisions that should be captured in an ADR
   - mismatches between behavior and documented workflow
   - incomplete operator or reviewer guidance
   - release, CI, or approval changes without explicit acknowledgment
   - license, attribution, or process compliance gaps
4. Flag where the repo-level instructions are ambiguous, stale, or internally
   inconsistent.
5. Recommend the smallest documentation or process correction that closes the
   gap.

## Reporting Contract

- Report findings first, ordered by severity and blast radius.
- Cite the governing file or instruction that a finding depends on.
- State explicitly when no findings were found.
- If the change introduces a non-obvious trade-off or persistent constraint,
  state: `An ADR is required for this decision.`

## Boundaries

- Do not invent policy requirements that are not grounded in the repository.
- Do not downgrade a missing ADR or missing approval path into a stylistic note.
