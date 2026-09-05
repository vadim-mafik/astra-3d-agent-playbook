# Constraints

## Allowed

- assigned reference files;
- the intended Blender scene/output;
- Blender MCP;
- scoped visual iteration;
- partial or full rebuild of the assigned asset when necessary;
- deterministic Blender/Python operations that stay inside the task;
- narrow external research only when explicitly enabled for this task.

## Not allowed during the art pass

- broad repository or filesystem exploration;
- unrelated infrastructure repair;
- child-agent spawning;
- unrelated project edits;
- credentials or sensitive data;
- engine integration;
- rigging, skinning, LODs, optimization, or packaging unless this task explicitly changes scope.

## Safety

Do not overwrite the only good version of an asset. Save a new working version or preserve a recoverable backup before destructive changes.
