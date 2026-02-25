# Handoff

Pass completed work to another role for the next phase.

## Arguments

- `$ARGUMENTS` — Target role and context (e.g. "reviewer: PR #12 ready for review" or "developer: auth spec is finalized")

## Instructions

1. Make sure your current task is updated to `done` or `review` status.
2. Create a handoff note with:
   - **From:** Your role
   - **To:** Target role
   - **Task:** The task ID and title
   - **Summary:** What you completed
   - **Next steps:** What the target role should do
   - **Files:** Key files they should look at
   - **Open questions:** Anything unresolved
3. Add the handoff note to the task file under **Notes**.
4. If the next step requires a new task, add it to `tasks/backlog.md` and tag the target role.
