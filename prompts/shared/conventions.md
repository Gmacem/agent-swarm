# Conventions

<!-- Customize these for your project. -->

## Branching Strategy

- `main` — stable, always deployable
- `feat/<name>` — new features
- `fix/<name>` — bug fixes
- `chore/<name>` — maintenance, tooling, docs

Branch from `main`, merge via PR. Delete branch after merge.

## Commit Messages

Use conventional commits:

```
<type>(<scope>): <short description>

<optional body>
```

Types: `feat`, `fix`, `docs`, `style`, `refactor`, `test`, `chore`, `ci`

## Naming

- Files: `kebab-case` (e.g. `user-service.ts`)
- Variables/functions: `camelCase`
- Classes/types: `PascalCase`
- Constants: `UPPER_SNAKE_CASE`
- Database tables: `snake_case`

## Code Style

- Prefer readability over cleverness.
- Keep functions short and focused.
- Name things descriptively — avoid abbreviations.
- Add comments only where the "why" isn't obvious from the code.
- Handle errors explicitly, don't swallow them.

## Pull Requests

- Keep PRs small and focused on one thing.
- Include a description of what changed and why.
- Link to the task file.
- All PRs need at least one review before merge.

## Documentation

- Architecture decisions go in `knowledge/decisions/` as ADRs.
- API specs go in `knowledge/specs/`.
- Research findings go in `knowledge/research/`.
- Runbooks go in `knowledge/runbooks/`.
