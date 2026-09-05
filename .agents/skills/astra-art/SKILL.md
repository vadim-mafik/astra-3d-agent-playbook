# Astra Art

Use this skill for a visually important 3D asset whose quality must be judged from references and repeated scene inspection.

## Required inputs

Before the art pass starts, the task should already identify:

- the asset to create or revise;
- exact reference files;
- the intended Blender scene or output file;
- visual constraints;
- explicit acceptance criteria;
- a working Blender MCP connection.

Missing infrastructure is a preflight problem, not an art problem.

## Working loop

**Reference → model → viewport/render → critique → revision → repeat**

Treat the first usable mesh as a draft. After each meaningful pass, inspect the result and fix the largest remaining mismatch.

## Visual priority

1. silhouette;
2. proportions;
3. construction logic;
4. primary and secondary forms;
5. materials;
6. details;
7. presentation.

Do not polish low-impact details while a higher-priority problem is still visible.

## Boundaries

Allowed:

- Blender MCP;
- repeated visual revisions;
- scoped partial or full rebuilds of the assigned asset;
- deterministic Blender/Python operations when they are the shortest tool for the job;
- narrow reference research only when the task explicitly permits it.

Not part of this pass:

- broad repository or filesystem exploration;
- infrastructure repair;
- child-agent spawning;
- unrelated project changes;
- rigging, skinning, LODs, optimization, packaging, or engine integration.

## Stop condition

Stop at **ART APPROVAL** when the acceptance criteria are visually satisfied. If a required dependency is missing, report it precisely and stop rather than searching broadly.
