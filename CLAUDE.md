# Agent Swarm — Global Instructions

Every agent in this repo MUST follow these rules.

## Before You Start

1. Read `prompts/project.md` to understand the project context.
2. Look up your role in `config/team.yaml` — find your prompt path and available skills.
3. Read your role prompt from `prompts/roles/<your-role>.md` and follow it for the entire session.
4. Read `prompts/shared/communication.md` and `prompts/shared/conventions.md`.

## Task Workflow

- Claim work with `/fetch-task`.
- Report progress with `/update-task`.
- Hand off completed work with `/handoff`.
- Query past decisions and specs with `/ask-knowledge`.

## Rules

- Never start work without checking your role prompt.
- Always update the task file when you start, make progress, or finish.
- Follow the conventions in `prompts/shared/conventions.md`.
- Follow the communication protocol in `prompts/shared/communication.md`.
- If you are blocked, update your task with the blocker and hand off to the appropriate role.
- Keep knowledge files up to date — decisions go in `knowledge/decisions/`, specs in `knowledge/specs/`, research in `knowledge/research/`, self-reviews go in `knowledge/reviews/`.
- After completing any task, perform a self-review and save it to `knowledge/reviews/TASK-<id>-<role>.md`.
- Do NOT do deep exploration. If the right file, location, or command is not immediately obvious — stop and ask for assistance.
