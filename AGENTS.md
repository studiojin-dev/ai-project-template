# AGENTS.md

This repository uses AI coding agents.
If rules are missing or unclear, the agent must ask before proceeding.

## Scope

This file defines HOW the agent works.
WHAT to build is defined in SPECS.
WHY decisions were made is defined in ADRs when the project uses them.

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

## Localization / Translation Rule (MUST)

When a task includes i18n or localization work:

- use a dedicated translator/localization agent when the tool supports specialized routing; otherwise apply the same constraints directly
- preserve placeholders, ICU message syntax, variables, HTML/Markdown, and key structure exactly
- prefer the strongest translation-capable model already available in the active AI toolchain; if an external service is required, use an approved frontier-quality model endpoint
- do not rely on free/public commodity machine-translation APIs or unofficial wrappers as the primary translation source
- escalate when glossary, tone, product terminology, or locale-specific style guidance is missing

## Specialist Lanes

When the active tool supports installed skills or specialist agents, prefer the
bundled specialist lanes for:

- security review
- governance/compliance review
- UI/UX/accessibility review
- localization review

If the tool does not support installed skills or specialist agents, apply the
same constraints directly.

## ADR Rule (MUST)

If the project uses ADRs, architectural or design decisions with trade-offs
MUST be recorded as ADRs (e.g. in `docs/adr/`).
The agent MUST NOT override existing ADRs without updating them first.
If a change introduces new constraints or non-obvious choices in a project that
uses ADRs, stop and request an ADR.

## Plan Then Act

1) Restate the goal in one sentence
2) Propose a short plan
3) (TDD) Red: write a failing test or a clear reproduction
4) (TDD) Green: make the minimal change to pass
5) (TDD) Blue: refactor for clarity and maintainability
6) Summarize what changed and why
7) Code Review to verify the goal, security, and license compliance; if not, go back to step 2

## Iterative Validation Loop (MUST)

For non-trivial implementation requests, the agent MUST execute iterative loops,
not a single-pass implementation.

Required baseline loop:

1) Implement
2) Code Review (findings prioritized by severity)
3) Fix findings
4) Code Review again

If unresolved high-severity findings remain, new risks are discovered, or acceptance
criteria are not fully met, the agent MUST:

- re-plan the remaining work,
- implement follow-up changes,
- and repeat review + verification.

Completion gate (all required):

- no unresolved P0/P1 findings,
- verification commands pass for touched scope (tests/build/lint),
- requirements, ADR constraints, and license/security rules are satisfied.

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

## Documentation Workflow

This template does not require ADRs by default.
If a project adopts ADRs:

- ADRs MUST be written in `docs/adr/*.md`.
- When an ADR is added or modified, `docs/adr/index.json` MUST be updated.
- The ADR index MUST be generated using the `adr-index` skill.

AGENTS.md MUST NOT accumulate completed work logs.
If the project uses ADRs, decisions MUST be recorded there; only links or short
summaries are allowed here.

### ADR Detection Rule

If you make or rely on a decision that:

- introduces architectural constraints,
- involves trade-offs,
- or is not obvious from code alone,

then, in projects that use ADRs, you MUST pause and explicitly state:
"An ADR is required for this decision."
