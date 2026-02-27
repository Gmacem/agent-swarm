# Communication Protocol

All agents follow this protocol for status reporting and handoffs.

## Status Updates

When working on a task, update it at these checkpoints:
1. **Claimed** — You picked up the task. Set status to `in-progress`, add your role.
2. **Progress** — Meaningful progress or a new finding. Add a note with what changed.
3. **Blocked** — You hit a blocker. Describe the blocker, tag the role that can unblock you.
4. **Done** — Work is complete. Set status to `done`, summarize what was delivered.
5. **Self-Review** — After completing the task, write a self-review and save it to `knowledge/reviews/`.

Use `/update-task` to record each checkpoint.

## Self-Review

Every agent MUST perform a self-review after completing a task. Save it to `knowledge/reviews/TASK-<id>-<role>.md`.

```markdown
# Self-Review: TASK-<id> — <role>

**Date:** <date>
**Task:** <task title>
**Role:** <role>

## What Was Done
<brief summary of completed work>

## What Went Well
- <positive outcome or good decision>

## What Could Be Improved
- <mistake, inefficiency, or missed item>

## Blockers Encountered
- <any blockers and how they were resolved, or "None">

## Lessons Learned
- <takeaway for future tasks>
```

## Handoffs

When your part is done and another role needs to continue:
1. Finish your task and set it to `done`.
2. Use `/handoff` to pass context to the next role.
3. Include: what was done, what's next, any open questions, relevant file paths.

## Handoff Targets

| From         | Typical handoff to           |
|--------------|------------------------------|
| Coordinator  | Architect, Developer         |
| Architect    | Developer, Coordinator       |
| Developer    | Reviewer, Tester             |
| Reviewer     | Developer (if changes needed)|
| Tester       | Developer (if bugs found)    |
| DevOps       | Coordinator, Developer       |
| Researcher   | Architect, Coordinator       |

## Task File Format

Task files in `tasks/active/` use this structure:

```markdown
# TASK-<id>: <title>

- **Status:** backlog | in-progress | blocked | review | done
- **Assigned:** <role>
- **Priority:** critical | high | medium | low
- **Created:** <date>
- **Updated:** <date>

## Description

<what needs to be done>

## Acceptance Criteria

- [ ] criterion 1
- [ ] criterion 2

## Notes

<progress updates, blockers, decisions>
```
