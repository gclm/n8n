---
name: release-version-bump
description: Workflow command scaffold for release-version-bump in n8n.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /release-version-bump

Use this workflow when working on **release-version-bump** in `n8n`.

## Goal

Release a new version of n8n, including updating package versions and changelog.

## Common Files

- `CHANGELOG.md`
- `package.json`
- `packages/*/package.json`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Update CHANGELOG.md with release notes.
- Update version in package.json at the root and in affected packages.
- Commit and tag the release.

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.