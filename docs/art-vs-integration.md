# Art pass vs. technical integration

The playbook treats visual production and technical integration as separate deliverables.

## Art pass

The art pass answers:

> Does the asset look right?

Typical concerns:

- silhouette;
- proportion;
- anatomy or mechanical plausibility;
- construction logic;
- secondary forms;
- material character;
- details;
- presentation.

The art pass may rebuild geometry when needed. Its endpoint is **ART APPROVAL**.

## Technical integration

The technical pass answers:

> Can the approved asset be used correctly in its destination?

Typical concerns:

- topology requirements;
- UVs and baking;
- naming;
- scale and transforms;
- export/import;
- rigging and skinning;
- physics or collision;
- LODs;
- optimization;
- engine material setup;
- packaging and validation.

These tasks often benefit from deterministic tools and a cheaper model.

## Why the separation matters

A technically valid asset can still have a bad silhouette.

A beautiful asset can still fail an import, have unusable weights, or be too expensive at runtime.

Keeping the two passes separate gives each one a clear definition of success and prevents technical work from prematurely “locking in” a visually weak model.

## Handoff checklist

Before leaving the art pass, record:

- approved Blender file/version;
- required orientation and scale assumptions;
- material intent;
- any visual features that must survive optimization;
- known non-blocking issues.

The technical task should consume that approved result rather than silently redesigning it.
