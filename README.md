# Astra 3D Agent Playbook

Practical, cost-aware workflows for creating high-quality 3D assets with **GPT-6 Astra**, **Blender**, and a compatible **Blender MCP** connection.

🇷🇺 [Русская версия](README.ru.md)

> **Core idea:** technical validity is not visual success. A mesh can be structurally valid and still have the wrong silhouette, proportions, construction logic, materials, or presentation.

This repository packages a workflow that keeps expensive visual reasoning focused on the work where it matters most: **reference-driven art direction and iterative correction inside Blender**.

## What this repository is

The playbook is for artists and technical users who want an AI agent to help build or revise visually important 3D assets without spending the most capable model on file discovery, setup debugging, or engine integration.

The workflow separates two jobs that are easy to mix up:

- **Art pass** — shape, proportion, construction, secondary forms, materials, details, presentation.
- **Technical pass** — export/import, rigging, skinning, LODs, optimization, naming, packaging, engine integration.

The art pass ends at **ART APPROVAL**. Integration starts only after the asset looks right.

## The production loop

```text
cheap preflight
    ↓
clean Astra High session
    ↓
Blender MCP
    ↓
reference → model → viewport/render → critique → revision
                         ↑                         ↓
                         └──────── repeat ─────────┘
    ↓
ART APPROVAL
    ↓
separate technical integration
```

The first mesh is a draft, not the finish line. The agent should inspect the result, identify the highest-impact mismatch, correct it, and inspect again.

## Why Blender MCP

A compatible Blender MCP connection gives the agent direct access to the working scene and lets it use viewport or render feedback as part of the iteration loop.

That is different from:

- **Computer Use**, which drives the interface through mouse/keyboard-style interaction;
- **headless Blender**, which runs a separate background process;
- **Python-first automation**, which is excellent for deterministic geometry operations and batch work, but can become inefficient when every visual correction requires generating, running, inspecting, and rewriting scripts.

Python is not discouraged here. Use it where it is the shortest deterministic tool. Use Blender MCP where persistent scene state and visual feedback matter.

## Quick start

1. Install Blender.
2. Configure a compatible Blender MCP server and verify that Codex can reach it.
3. Copy `.codex/` and `.agents/skills/astra-art/` into your project if you want the included custom-agent setup.
4. Copy `templates/art-task/` into a new task directory.
5. Fill in the task packet:
   - `TASK.md` — objective and visual priorities;
   - `FILES.txt` — exact input/output allowlist;
   - `CONSTRAINTS.md` — boundaries and permitted tools;
   - `ACCEPTANCE.md` — what must be true before approval;
   - `STATE.json` — small machine-readable state.
6. Run the cheap [preflight prompt](prompts/preflight.md).
7. Start a **clean Astra High** art session, or use the included `astra-art` role if your Codex surface exposes project custom agents.
8. Use the [art-pass prompt](prompts/art-pass.md).
9. If the asset exists but is visually weak, use [revision-pass](prompts/revision-pass.md).
10. When only a few high-impact fixes remain, use [convergence-pass](prompts/convergence-pass.md).
11. Stop at **ART APPROVAL** and move engine integration to a separate task.

## Repository map

| Path | Purpose |
| --- | --- |
| `.codex/config.toml` | Registers the optional project-scoped `astra-art` role |
| `.codex/agents/astra-art.toml` | Astra model and visual-production instructions |
| `.agents/skills/astra-art/SKILL.md` | Compact reusable art-workflow skill |
| `docs/` | Human-readable setup, workflow, MCP, cost, and troubleshooting guides |
| `prompts/` | Copyable task prompts |
| `templates/art-task/` | Reusable bounded task packet |
| `examples/generic-footwear/` | Neutral worked example |

## Visual priority order

When time or context is limited, fix the largest visible problem first:

1. silhouette;
2. overall proportions;
3. construction logic;
4. primary and secondary forms;
5. material response;
6. small details;
7. presentation.

Do not spend the final third of a run polishing stitches while the overall shape is still wrong.

## Keeping usage under control

The expensive model should receive **known inputs**, not a mystery repository.

Good preparation means:

- exact reference paths are known;
- the output path is known;
- Blender MCP has already passed a smoke test;
- the task has a narrow visual objective;
- acceptance criteria are explicit;
- infrastructure problems are resolved before the art pass.

See [Cost control](docs/cost-control.md) for the full rationale.

## Visible Blender workflow

If you want to watch the work happen in your current Blender scene, use the [visible-session prompt](prompts/visible-blender-session.md). The key requirement is that the agent works through Blender MCP against the currently open Blender instance instead of launching a hidden background copy.

## Requirements

- Codex access to GPT-6 Astra;
- Blender;
- a compatible Blender MCP implementation;
- explicit local references for the asset you want to build or revise;
- Git is optional but recommended for versioning task/config changes.

Exact Codex surfaces and MCP implementations can change. The workflow is intentionally separated from any single Blender MCP vendor.

## Limitations

This is a workflow playbook, not a guarantee that every asset will become production-ready in one session. Complex assets can still require manual art direction, topology cleanup, retopology, UV work, baking, rigging, or engine-specific validation.

Custom-agent availability can also vary by Codex surface/version. If the `astra-art` role is not available in your current client, the same workflow still works by opening a clean Astra session and supplying the task packet directly.

## Public-repository hygiene

This repository is intentionally generic. Examples use placeholders rather than real project names, private asset paths, credentials, logs, or production screenshots. If you adapt the templates, review them before publishing.

## Documentation

- [Setup](docs/setup.md)
- [Workflow](docs/workflow.md)
- [Blender MCP](docs/blender-mcp.md)
- [Cost control](docs/cost-control.md)
- [Art vs. technical integration](docs/art-vs-integration.md)
- [Troubleshooting](docs/troubleshooting.md)

## License

MIT — see [LICENSE](LICENSE).
