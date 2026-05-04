```markdown
# n8n Development Patterns

> Auto-generated skill from repository analysis

## Overview
This skill teaches the core development patterns, coding conventions, and common workflows for contributing to the [n8n](https://github.com/n8n-io/n8n) codebase. n8n is a workflow automation tool built primarily in TypeScript, using the Hono framework for backend services. The repository emphasizes clear commit messages, modular code structure, and robust testing practices. This guide will help you understand how to contribute features, manage releases, and update database schemas in line with project standards.

## Coding Conventions

- **File Naming:**  
  Use `camelCase` for file names.  
  _Example:_  
  ```
  userRepository.ts
  workflowRunner.test.ts
  ```

- **Import Style:**  
  Use relative imports for internal modules.  
  _Example:_  
  ```typescript
  import { getUser } from './userRepository';
  ```

- **Export Style:**  
  Use named exports.  
  _Example:_  
  ```typescript
  export function getUser(id: string) { ... }
  export const USER_ROLE = 'admin';
  ```

- **Commit Messages:**  
  - Use prefixes like `fix:` or `feat:` to indicate the type of change.
  - Keep messages concise (~95 characters on average).
  _Example:_  
  ```
  feat: add support for OAuth2 authentication in HTTP node
  fix: correct typo in workflow execution error message
  ```

## Workflows

### Release Version Bump
**Trigger:** When a new release is being published.  
**Command:** `/release`

1. Update `CHANGELOG.md` with release notes.
2. Update the version in the root `package.json` and in any affected packages:
   - `package.json`
   - `packages/*/package.json`
3. Commit your changes and tag the release.

_Example:_
```bash
# 1. Edit CHANGELOG.md and package.json files
git add CHANGELOG.md package.json packages/*/package.json
git commit -m "chore: release vX.Y.Z"
git tag vX.Y.Z
git push && git push --tags
```

---

### Add or Modify Database Table
**Trigger:** When a new database table is needed or an existing one is updated.  
**Command:** `/new-table`

1. Create or update the entity file in `packages/@n8n/db/src/entities/`.
2. Add or update the migration in:
   - `packages/@n8n/db/src/migrations/common/`
   - and the relevant database-specific folder:
     - `packages/@n8n/db/src/migrations/postgresdb/index.ts`
     - `packages/@n8n/db/src/migrations/sqlite/index.ts`
3. Update the repository in `packages/@n8n/db/src/repositories/`.
4. Update index files for entities and repositories.
5. Add or update related tests in `packages/@n8n/db/src/repositories/__tests__/`.

_Example:_
```typescript
// packages/@n8n/db/src/entities/newEntity.ts
export class NewEntity { ... }
```
```typescript
// packages/@n8n/db/src/migrations/common/1234567890-add-new-entity.ts
import { MigrationInterface, QueryRunner } from "typeorm";
export class AddNewEntity1234567890 implements MigrationInterface {
  async up(queryRunner: QueryRunner): Promise<void> { ... }
  async down(queryRunner: QueryRunner): Promise<void> { ... }
}
```

---

### Feature Development with Tests and i18n
**Trigger:** When developing a new feature or enhancing an existing one.  
**Command:** `/feature`

1. Implement the feature in the relevant `.vue`, `.ts`, or `.js` files.
   - Example: `packages/frontend/editor-ui/src/components/MyFeature.vue`
2. Add or update corresponding test files (`*.test.ts` or `*.test.js`).
   - Example: `packages/frontend/editor-ui/src/components/__tests__/MyFeature.test.ts`
3. Update i18n files for new or changed strings.
   - Example: `packages/frontend/@n8n/i18n/src/locales/en.json`
   ```json
   {
     "myFeature.label": "My Feature",
     "myFeature.description": "Description of my feature"
   }
   ```

---

## Testing Patterns

- **Framework:** [Jest](https://jestjs.io/)
- **Test File Pattern:** `*.test.ts`
- **Location:** Tests are typically placed alongside the code or in `__tests__` subdirectories.

_Example:_
```typescript
// packages/@n8n/db/src/repositories/__tests__/userRepository.test.ts
import { getUser } from '../userRepository';

describe('getUser', () => {
  it('should return user by id', async () => {
    const user = await getUser('123');
    expect(user).toBeDefined();
  });
});
```

## Commands

| Command    | Purpose                                                        |
|------------|----------------------------------------------------------------|
| /release   | Start the release version bump workflow                        |
| /new-table | Add or modify a database table, including migrations and tests |
| /feature   | Start a new feature with tests and i18n updates                |
```