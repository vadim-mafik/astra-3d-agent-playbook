# Setup

This guide prepares the minimum environment needed for the playbook. The goal is not to make Astra discover your setup; the goal is to hand Astra a setup that has already been verified.

## 1. Install Blender

Use a normal desktop installation of Blender. The exact supported Blender version depends on the Blender MCP implementation you choose, so verify compatibility with that project rather than assuming a version from this repository.

## 2. Configure Blender MCP

Install and configure a Blender MCP implementation that your Codex client can reach.

Before starting an expensive art session, run a small smoke test:

- Blender is open;
- the intended scene is open;
- Codex can call the Blender MCP tools;
- a harmless scene query or reversible change succeeds;
- the change affects the **currently open** Blender instance if visible work is required.

If this fails, fix the connection before starting Astra.

## 3. Optional Codex project role

The repository includes:

- `.codex/config.toml`, which registers `astra-art`;
- `.codex/agents/astra-art.toml`, which defines the role.

Project custom-agent support can vary by Codex surface and release. If your client does not expose the role, use a clean Astra session directly and supply the same task packet and prompts. The workflow does not depend on child-agent spawning.

## 4. Prepare the task packet

Copy `templates/art-task/` into a task-specific directory and fill in all five files:

- `TASK.md`
- `FILES.txt`
- `CONSTRAINTS.md`
- `ACCEPTANCE.md`
- `STATE.json`

`FILES.txt` is intentionally plain text. Keep one allowed path per line; do not put prose, Markdown comments, or unrelated paths in it.

## 5. Prepare references

References should be explicit and useful for judging form. For a physical asset, a practical set might include:

- side;
- front;
- back;
- three-quarter;
- top or bottom when construction depends on it;
- detail views for important mechanisms or seams.

More images are not automatically better. Prefer a small set that answers concrete shape questions.

## 6. Run preflight

Use `prompts/preflight.md` with a cheaper model or inexpensive session.

Preflight should confirm:

- all task packet files exist;
- every referenced input exists;
- output location is known;
- Blender MCP works;
- acceptance criteria are concrete enough to judge;
- no infrastructure repair remains.

Only then start the art pass.
