# Agent Swarm

A reusable template for running multi-agent AI teams with [Claude Code](https://docs.anthropic.com/en/docs/claude-code). Define roles, assign tasks, and coordinate work across specialized agents using file-based task management and native slash commands.

## Roles

| Role | Description |
|------|-------------|
| **Coordinator** | Breaks epics into tasks, assigns work, prioritizes, unblocks |
| **Architect** | System design, ADRs, API contracts, tech decisions |
| **Developer** | Implementation, coding, pull requests |
| **Reviewer** | Code review, security analysis, quality |
| **Tester** | Test writing, coverage analysis, validation |
| **DevOps** | Infrastructure, CI/CD, deployment, monitoring |
| **Researcher** | Tech research, library comparison, reports |

Roles are defined in `config/team.yaml` and detailed in `prompts/roles/`.

## Slash Commands

Shared across all roles:

- `/fetch-task` — Claim next task from the backlog
- `/update-task` — Report progress or blockers
- `/ask-knowledge` — Query decisions, specs, and research
- `/handoff` — Pass completed work to another role

Role-specific commands are listed in each role's prompt and in `config/team.yaml`.

## Project Structure

```
.claude/commands/    # Slash commands (skills)
config/team.yaml     # Role registry
prompts/
  project.md         # Project context (fill in per project)
  shared/            # Communication protocol, conventions
  roles/             # Per-role prompts + template for new roles
knowledge/
  decisions/         # Architecture Decision Records
  specs/             # API contracts, data models
  research/          # Research reports, comparisons
  runbooks/          # Operational procedures
tasks/
  backlog.md         # Task queue
  active/            # In-progress task files
```

## Getting Started

1. Clone this repo (or use it as a template).
2. Fill in `prompts/project.md` with your project's details.
3. Customize `prompts/shared/conventions.md` for your stack.
4. Open Claude Code in the repo root — slash commands are available automatically.
5. Start by acting as the Coordinator: add tasks to `tasks/backlog.md`, then hand off to other roles.

## Adding a New Role

1. Copy `prompts/roles/_template.md` to `prompts/roles/<role-name>.md`.
2. Fill in the identity, responsibilities, and rules.
3. Add the role to `config/team.yaml` with its skills and permissions.
4. Create any role-specific slash commands in `.claude/commands/`.

## Generating Knowledge

The `knowledge/` directory is the shared memory of your agent swarm. There are several ways to populate it:

**Using agents:**

- **Researcher** — Use `/search-web` to gather information, `/summarize-docs` to distill documentation, and `/compare-options` to evaluate alternatives. The Researcher writes structured reports to `knowledge/research/`.
- **Architect** — Creates Architecture Decision Records (ADRs) in `knowledge/decisions/` and API specs in `knowledge/specs/`.
- **DevOps** — Writes operational runbooks to `knowledge/runbooks/`.

**Manually:**

You can create knowledge files directly. Follow the formats defined in each role's prompt:

- ADRs: `knowledge/decisions/NNN-title.md` (Status, Context, Decision, Consequences)
- Research: `knowledge/research/topic.md` (structured comparison/report)
- Specs: `knowledge/specs/component.md` (API contracts, data models)
- Runbooks: `knowledge/runbooks/procedure.md` (step-by-step operational guides)

**Querying knowledge:**

Any role can use `/ask-knowledge` to search across all knowledge files for past decisions, specs, and research.

## Adding a New Skill

1. **Create the command file.** Add `.claude/commands/<skill-name>.md` with a title line and instructions. Use `$ARGUMENTS` for user input:
   ```markdown
   # Skill Name

   Do the thing with: $ARGUMENTS

   ## Steps
   1. ...
   ```
2. **Register in team config.** Add the skill name to the role's `skills` list in `config/team.yaml`.
3. **Document in the role prompt.** Mention the new skill under "Available Skills" in `prompts/roles/<role>.md`.
4. **Add permissions if needed.** If the skill runs shell commands that aren't already allowed, add them to `.claude/settings.json` under `allowedTools`.

## Manual Orchestration

You can directly control agents without going through the full task workflow.

**Assume a role directly:**

Tell Claude Code to act as a specific role:

```
Act as Coordinator and break this epic into tasks: "Add user authentication"
```

```
Act as Researcher and compare Redis vs Memcached for our caching layer
```

**Manage tasks by hand:**

- Add tasks directly to `tasks/backlog.md` in the standard format.
- Edit files in `tasks/active/` to change assignments, priorities, or status.
- Override an agent mid-stream by giving direct instructions or editing the task file it's working on.

**Common scenarios:**

| Goal | What to do |
|------|------------|
| Quick architecture question | "Act as Architect and write an ADR for choosing PostgreSQL over MongoDB" |
| One-off code task | "Act as Developer and implement the login endpoint" |
| Get a second opinion | "Act as Reviewer and review the changes in the last commit" |
| Research a library | "Act as Researcher and compare options for form validation" |

## Human Checkpoints

Use these review gates to stay in control of the workflow.

**Plan review (before implementation):**

- Use Claude Code's built-in plan mode — the agent will outline its approach and wait for your approval before writing code.
- Or instruct the agent explicitly: "Outline your approach before coding. Don't implement until I approve."
- Review the plan for scope, approach, and potential issues before giving the go-ahead.

**Code review (after testing):**

- After the Tester role finishes validation, review the changes yourself before merging.
- Use `/review-pr` to get an automated review, then inspect the diff manually.
- Check that tests pass, code matches the plan, and no unintended changes were introduced.

**Moving a task back to in-progress:**

If a completed task is missing something:

1. **Edit the task file directly** — change the status from `done` or `review` back to `in-progress` and add a note explaining what's missing.
2. **Or tell an agent** — "Act as Coordinator, move TASK-X back to in-progress because error handling is missing."
3. The task will re-enter the active queue for the assigned role to pick up.

## License

MIT
