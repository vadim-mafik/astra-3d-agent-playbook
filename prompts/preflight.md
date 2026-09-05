# Preflight

Run this with a cheaper model/session before starting Astra.

```text
Prepare this 3D art task for an Astra art pass without launching Astra.

Verify only the bounded task inputs:

- TASK.md exists and states one clear visual objective;
- FILES.txt contains explicit input/reference/output paths;
- every required reference exists;
- the intended output location is known;
- CONSTRAINTS.md is present and unambiguous;
- ACCEPTANCE.md contains observable visual criteria;
- STATE.json is valid and reflects the current task state;
- Blender MCP is connected and a minimal smoke test succeeds against the intended Blender session.

Do not recursively explore unrelated folders.
Do not repair unrelated infrastructure.
Do not create the asset.

If anything required is missing, return the exact missing dependency and the smallest next action needed to resolve it.

If all checks pass, return ART_READY=true.
```
