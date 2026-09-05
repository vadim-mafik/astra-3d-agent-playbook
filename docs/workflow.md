# Workflow

The playbook separates **preparation**, **visual production**, and **technical integration** so the expensive visual model spends its context on the asset rather than the environment around it.

## Stage 1 — Preflight

Resolve uncertainty before Astra starts.

A useful preflight answers four questions:

1. What exactly is being built or revised?
2. Which files and references are authoritative?
3. Where does the result go?
4. How will we know the art pass is finished?

If the answers are still vague, the task is not ready.

## Stage 2 — Clean art session

Start a clean Astra High session or the `astra-art` role with only the context needed for this asset.

Avoid dragging long infrastructure/debugging history into the art pass. Previous failures can be summarized as constraints when they materially affect the work.

## Stage 3 — Establish the primary form

The first pass should solve the largest structural questions:

- silhouette;
- scale and proportion;
- primary volumes;
- construction logic.

Do not spend early iterations on tiny bevels, stitching, scratches, or presentation lighting.

## Stage 4 — Inspect, critique, revise

After a meaningful modelling pass:

1. inspect the viewport or render;
2. compare it to the references;
3. name the highest-impact mismatch;
4. fix that mismatch;
5. inspect again.

A good critique is specific: “the toe box is too tall and too narrow in top view” is actionable; “make it better” is not.

## Stage 5 — Secondary forms and materials

Once the silhouette is stable, move down the priority stack:

- secondary construction;
- seams, panels, fasteners, trim;
- material response;
- smaller details.

Material polish should not be used to disguise incorrect geometry.

## Stage 6 — Convergence

Near the end of the session, stop inventing new features.

Use `prompts/convergence-pass.md` to:

- preserve the best current version;
- correct only remaining high-impact issues;
- make one final inspection;
- stop.

## Stage 7 — ART APPROVAL

Approval means the asset satisfies the visual acceptance criteria. It does **not** mean the asset is already optimized, rigged, exported, or engine-ready.

Record approval in `STATE.json` if you use the task packet mechanically.

## Stage 8 — Technical integration

Create a new task for export, topology requirements, rigging, LODs, collision, engine import, packaging, or platform validation.

Keeping this separate makes both tasks easier to reason about and easier to repeat.
