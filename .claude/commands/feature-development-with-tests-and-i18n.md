---
name: feature-development-with-tests-and-i18n
description: Workflow command scaffold for feature-development-with-tests-and-i18n in n8n.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /feature-development-with-tests-and-i18n

Use this workflow when working on **feature-development-with-tests-and-i18n** in `n8n`.

## Goal

Implement a new feature or enhancement, including code, tests, and internationalization updates.

## Common Files

- `packages/frontend/editor-ui/src/**/*.vue`
- `packages/frontend/editor-ui/src/**/*.ts`
- `packages/frontend/editor-ui/src/**/*.test.ts`
- `packages/frontend/@n8n/i18n/src/locales/en.json`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Implement feature in relevant .vue, .ts, or .js files.
- Add or update corresponding test files (*.test.ts or *.test.js).
- Update i18n files for new/changed strings.

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.