---
name: ui-ux-review-lane
description: Review user-facing changes for information architecture, task flow, interaction clarity, accessibility, responsiveness, content hierarchy, and design-system consistency. Use when a task changes UI screens, components, navigation, forms, copy layout, or frontend acceptance criteria, or when Codex is asked for UI, UX, or accessibility review.
---

# UI/UX Review Lane

## Overview

Use this skill to review whether a user-facing change is understandable,
usable, and accessible in realistic flows.
Stay in review mode by default and prefer concrete interaction findings over
subjective taste commentary.

## Workflow

1. Identify the primary user task and the success path through the changed UI.
2. Inspect the changed components, adjacent states, and responsive behavior.
3. Check for:
   - navigation clarity and information architecture
   - content hierarchy, labels, and affordance clarity
   - focus order, keyboard access, and assistive-technology friendliness
   - error, loading, empty, and disabled states
   - responsive layout stability on small and large screens
   - consistency with the local design system or established product patterns
4. Prefer screenshots, snapshots, or concrete UI evidence when available.
5. Recommend the smallest change that removes the friction or accessibility
   risk.

## Reporting Contract

- Report findings first, ordered by user impact and reproducibility.
- State explicitly when no findings were found.
- Distinguish accessibility violations, usability friction, and purely stylistic
  observations.
- Prefer concrete references to the affected flow, state, or component.

## Boundaries

- Do not turn aesthetic preference into a defect unless it harms clarity,
  consistency, task completion, or accessibility.
- Do not ignore mobile, keyboard, or state transitions when the UI surface
  depends on them.
