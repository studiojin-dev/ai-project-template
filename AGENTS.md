# AGENTS.md

This repository uses AI coding agents.
If rules are missing or unclear, the agent must ask before proceeding.

## Scope
This file defines HOW the agent works.
WHAT to build is defined in SPECS.
WHY decisions were made is defined in ADRs.

## Core Rules
- Prefer correctness and clarity over cleverness
- Do not introduce new dependencies or services unless explicitly requested
- Avoid large refactors unless explicitly requested
- Preserve existing public behavior by default

## Documentation Rule (MUST)
Consult authoritative documentation when tasks involve:
- specific APIs, options, or signatures
- version-dependent or “latest” behavior
- deployment, auth, cloud, or security concerns
- production reliability or performance

If documentation is required and unavailable, ask for it or state uncertainty.

## ADR Rule (MUST)
Architectural or design decisions with trade-offs MUST be recorded as ADRs
(e.g. in `docs/adr/`).
The agent MUST NOT override existing ADRs without updating them first.
If a change introduces new constraints or non-obvious choices, stop and request an ADR.

## Plan Then Act
For non-trivial tasks:
1) Restate the goal in one sentence
2) Propose a short plan
3) (TDD) Red: write a failing test or a clear reproduction
4) (TDD) Green: make the minimal change to pass
5) (TDD) Blue: refactor for clarity and maintainability
6) Summarize what changed and why

## Verification
Do not claim correctness without describing how to verify it
(tests, build, or realistic checks).

## Repository Hygiene
If a .gitignore file does not exist, create one before adding
environment-, build-, or tool-specific files.

## Stop and Ask
Ask before proceeding if requirements are unclear,
changes are breaking, or behavior depends on docs or decisions.
After completing any implementation work, the agent MUST ask the user
whether a pull request draft is needed.
