---
name: add-or-modify-database-table
description: Workflow command scaffold for add-or-modify-database-table in n8n.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /add-or-modify-database-table

Use this workflow when working on **add-or-modify-database-table** in `n8n`.

## Goal

Add a new database table or modify an existing one, including entity, migration, and repository updates.

## Common Files

- `packages/@n8n/db/src/entities/*.ts`
- `packages/@n8n/db/src/migrations/common/*.ts`
- `packages/@n8n/db/src/migrations/postgresdb/index.ts`
- `packages/@n8n/db/src/migrations/sqlite/index.ts`
- `packages/@n8n/db/src/repositories/*.ts`
- `packages/@n8n/db/src/repositories/index.ts`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Create or update entity file in packages/@n8n/db/src/entities/.
- Add or update migration in packages/@n8n/db/src/migrations/common/ and database-specific folders.
- Update repository in packages/@n8n/db/src/repositories/.
- Update index files for entities and repositories.
- Add or update related tests.

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.