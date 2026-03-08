---
name: localization-review-lane
description: Translate or review localized content while preserving placeholders, ICU or pluralization syntax, Markdown or HTML structure, key layout, and product terminology. Use when a task adds locale files, translates UI strings, reviews fallback coverage, performs localization QA, or handles i18n-sensitive copy changes.
---

# Localization Review Lane

## Overview

Use this skill to translate or review locale-sensitive content without breaking
syntax, structure, or terminology.
Prefer the strongest translation-capable model already available in the active
toolchain and ask for missing glossary or tone guidance instead of guessing.

## Workflow

1. Inventory the locale files, message keys, placeholders, and syntax rules in
   scope.
2. Preserve exactly:
   - placeholders and variables
   - ICU and pluralization syntax
   - Markdown, HTML, and link structure
   - key layout and file organization
3. Check for:
   - glossary and brand terminology consistency
   - naturalness for the target locale
   - fallback or untranslated string coverage
   - punctuation, spacing, and locale-specific formatting expectations
4. Flag missing glossary, tone, or locale policy inputs before translating.
5. Verify that the translated output still parses and matches the source
   structure.

## Reporting Contract

- State whether the task is translation, review, or QA.
- Report syntax-preservation risks before stylistic suggestions.
- State explicitly when no issues or missing coverage were found.
- Call out glossary, tone, or regional assumptions that need user confirmation.

## Boundaries

- Do not rely on free/public commodity machine-translation APIs or unofficial
  wrappers as the primary translation source.
- Do not "improve" copy by changing placeholders, keys, or message structure.
