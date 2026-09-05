# Cost control

The main cost-control idea is simple: **do not pay the visual specialist to discover facts that a cheaper step can resolve first**.

## Expensive work

Astra is valuable when the problem requires strong visual or spatial judgment:

- interpreting multiple references;
- balancing proportions;
- spotting construction inconsistencies;
- choosing which visible error matters most;
- iterating toward a coherent final asset.

That is where the expensive context should go.

## Cheap work

Do before the art pass:

- locate files;
- verify paths;
- check whether references exist;
- create output folders;
- verify the MCP connection;
- resolve tool configuration;
- identify the exact scene;
- prepare acceptance criteria.

## Keep sessions narrow

A clean art session should not include a long history of:

- installation debugging;
- unrelated coding;
- repository cleanup;
- failed environment experiments;
- engine integration.

Summarize only the facts that constrain the current asset.

## Avoid repeated discovery

Tool discovery can become surprisingly expensive if the agent repeatedly asks what tools or files exist.

Preflight should establish the intended Blender MCP route once. The art session should then use that known route.

## Visual iteration is not waste

Do not confuse repeated **productive visual inspection** with repeated discovery.

This loop is the point of the workflow:

```text
model → inspect → critique → revise → inspect
```

The wasteful loop is:

```text
search environment → list tools → inspect unrelated files → repeat
```

## Use convergence deliberately

Long sessions can drift into low-value polishing. When the asset is close:

- freeze the design direction;
- fix only the largest remaining visible errors;
- perform a final check;
- stop.

That is what `prompts/convergence-pass.md` is for.

## Split art and integration

Art and technical integration ask different questions.

An art pass asks: **Does this asset look right?**

An integration pass asks: **Does this asset satisfy the technical requirements of the destination?**

Combining them encourages the model to spend expensive visual context on file formats, naming, imports, rigging, or engine-specific troubleshooting.

## Do not treat one usage number as universal

Usage varies with:

- asset complexity;
- reference quality;
- reasoning level;
- number of tools called;
- number of visual iterations;
- size of the existing conversation.

Measure your own tasks and compare similar jobs rather than treating one published run as a fixed benchmark.
