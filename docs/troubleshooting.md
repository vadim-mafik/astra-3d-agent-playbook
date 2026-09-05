# Troubleshooting

This page covers the failures that most often derail the workflow.

## Blender MCP is not visible

Do not start the art pass.

Check the MCP installation and Codex connection with a cheap session. The presence of a Blender executable does not prove that Blender MCP is connected.

## The agent edits a hidden Blender instance

If the task is meant to be visible, explicitly require the currently open Blender instance and forbid a separate headless/background process.

Use `prompts/visible-blender-session.md`.

## The task packet cannot be read

Treat this as a missing dependency. Fix the path or permissions before starting/restarting Astra.

Do not ask Astra to recursively search the machine for “something that looks like the task.”

## The agent stops after the first mesh

The art loop has not happened yet.

Ask for a viewport/render review against the references and a correction of the largest visible mismatch. If the asset already exists, use `prompts/revision-pass.md`.

## The silhouette is wrong but details look polished

Return to the priority order:

1. silhouette;
2. proportions;
3. construction;
4. secondary forms;
5. materials;
6. details.

Delete or rebuild low-value detail if it is preventing a primary-form correction.

## Materials look plastic

First confirm that the geometry and lighting are not causing the problem. Then inspect roughness variation, normal response, scale of surface detail, and whether the material matches the reference under comparable lighting.

Do not use scratches or noise to compensate for incorrect base response.

## The session keeps adding new ideas

Use the convergence prompt. Freeze design expansion and permit only remaining high-impact corrections.

## Context/usage is growing too quickly

Look for:

- broad filesystem searches;
- repeated MCP/tool enumeration;
- large generated scripts for small visual edits;
- repeated log polling;
- unrelated engine/infrastructure work;
- excessive conversation history.

Move those activities out of the art session.

## Custom agent does not appear in Codex

Custom-agent support can vary by client surface/version. Verify the current Codex configuration format. If the role still cannot be selected, run the workflow in a clean Astra session directly; the task packet and prompts remain usable.
