# Blender MCP

Blender MCP is the bridge between the agent and Blender. In this workflow its main value is not simply “remote control”; it is **persistent scene state plus visual feedback**.

## Why it helps art iteration

A visual 3D task often needs many small corrections:

- move or reshape geometry;
- inspect from another angle;
- render;
- compare against a reference;
- correct the largest mismatch;
- repeat.

When the agent can operate on the same live scene, each correction starts from the current state instead of reconstructing the state from a long script or a new process.

## Visible-session mode

For interactive work, target the Blender instance already open on screen.

Use `prompts/visible-blender-session.md` to make this explicit. This is particularly useful when a human wants to supervise the work and intervene manually.

A visible Blender workflow does **not** require Computer Use. Blender MCP can manipulate the scene while the normal Blender window remains visible.

## Blender MCP vs. Computer Use

**Blender MCP**

- calls Blender-specific tools;
- works with scene objects and data directly;
- is appropriate for repeated structured edits;
- can keep the current scene visible.

**Computer Use**

- operates an interface more like a human;
- is useful when a required action has no programmatic/MCP route;
- can add overhead for routine modelling operations.

Use Computer Use only when it solves a real gap.

## Blender MCP vs. Python

Python remains valuable for:

- deterministic transforms;
- procedural geometry;
- repetitive object creation;
- batch renaming or cleanup;
- data inspection;
- export preparation.

The issue is not Python itself. A Python-first workflow becomes inefficient when the model repeatedly writes large scripts merely to discover how the result looks.

A good hybrid rule is:

> Use Python for deterministic operations; use Blender MCP and viewport/render feedback for visual judgment.

## Smoke test

Before the art session:

1. open Blender and the intended scene;
2. verify MCP connectivity;
3. query a simple scene fact or make a reversible change;
4. confirm the expected open scene changed;
5. undo the test if needed.

If Codex can see the Blender executable but cannot reach Blender MCP, the art dependency is still missing.

## Do not silently launch another scene

If the task requires visible work, do not solve a broken connection by starting a separate headless/background Blender process. That hides state from the user and can result in the agent editing the wrong file.
