---
name: security-review-lane
description: Review code, plans, and diffs for application-security risks including authentication, authorization, secrets, trust boundaries, injection, data exposure, and unsafe configuration. Use when a task touches auth, permissions, secrets, untrusted input, external integrations, sensitive data, dependency/configuration risk, or when Codex is asked for a security review, abuse-case review, or threat-model check.
---

# Security Review Lane

## Overview

Use this skill to run a focused AppSec review or threat-model pass.
Stay in review mode by default and edit code only when the user explicitly asks
for remediation.

## Workflow

1. Define the asset, actor, and trust boundary in scope.
2. Inspect the changed files and the nearest call sites that influence data
   flow, authorization, or privilege.
3. Check for:
   - authentication and authorization gaps
   - secret handling and credential exposure
   - injection and input-validation failures
   - data leakage in APIs, logs, caches, and errors
   - dependency, configuration, and default-permission risk
   - privilege escalation and boundary crossing through external services
4. Prioritize findings by severity and exploitability.
5. Recommend the smallest effective mitigation and the narrowest meaningful
   verification.

## Reporting Contract

- Report findings first, ordered by severity.
- State explicitly when no findings were found.
- Name the vulnerable flow, the impact, and the shortest plausible exploit
  path.
- Separate confirmed issues from assumptions that depend on missing context.
- If unresolved risk depends on a design trade-off or persistent constraint,
  state: `An ADR is required for this decision.`

## Boundaries

- Do not pad the review with generic style or performance comments unless they
  create or amplify security risk.
- Do not claim an exploit is feasible if evidence is only speculative.
