# Ask Knowledge

Query the knowledge base for decisions, specs, research, or runbooks.

## Arguments

- `$ARGUMENTS` — What you want to find (e.g. "auth decision", "API spec for users", "database comparison")

## Instructions

1. Search the `knowledge/` directory for relevant files:
   - `knowledge/decisions/` — Architecture Decision Records
   - `knowledge/specs/` — API contracts and specifications
   - `knowledge/research/` — Research reports and comparisons
   - `knowledge/runbooks/` — Operational procedures
2. Read matching files and extract the relevant information.
3. Summarize what you found, including file paths for reference.
4. If nothing relevant is found, say so and suggest which role should create the missing knowledge (Architect for decisions/specs, Researcher for research, DevOps for runbooks).
