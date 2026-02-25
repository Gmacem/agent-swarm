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

## License

MIT
