# Review PR

Review a pull request for correctness, style, and quality.

## Arguments

- `$ARGUMENTS` — PR number or URL to review

## Instructions

1. Fetch the PR diff and description.
2. Review for:
   - **Correctness:** Does the code do what the task requires? Are acceptance criteria met?
   - **Style:** Does it follow `prompts/shared/conventions.md`?
   - **Readability:** Is the code clear and well-structured?
   - **Tests:** Are there tests? Do they cover the changes?
   - **Edge cases:** Are boundary conditions handled?
3. Check for common issues:
   - Unused imports or variables.
   - Hard-coded values that should be configurable.
   - Missing error handling.
   - Performance concerns.
4. Provide feedback using the review output format from `prompts/roles/reviewer.md`.
5. Either approve or request changes with specific, actionable comments.
