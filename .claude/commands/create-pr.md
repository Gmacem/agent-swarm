# Create PR

Create a pull request with a structured description.

## Arguments

- `$ARGUMENTS` — Optional: target branch (defaults to main)

## Instructions

1. Verify all tests pass (`/run-tests`) and linting is clean (`/lint`).
2. Check that changes are committed and pushed to the remote branch.
3. Create a PR with:
   - **Title:** Short, descriptive (under 70 chars). Use conventional format: `feat:`, `fix:`, etc.
   - **Body:**
     - Summary of changes (what and why).
     - Link to the task file.
     - Testing done.
     - Screenshots if UI changes.
4. Report the PR URL.
5. Hand off to Reviewer using `/handoff`.
