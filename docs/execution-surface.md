# Execution surface

For the deeper public architecture version of this topic, see `runtime-architecture.md`.

## Separate the control plane from the execution plane

A useful architecture split is:
- control plane: policies, approvals, assignments, run history, operator UX
- execution plane: tool execution near repositories, APIs, secrets, and customer infrastructure

This matters because agentic systems become dangerous when orchestration and execution are collapsed into one trust boundary.

## What the execution plane should do

- claim work
- receive a scoped context bundle
- execute through explicit drivers or sandbox tools
- emit structured results
- record artifacts and audit data

## What it should not do

- invent its own permissions
- keep broad standing access without scope
- bypass approval requirements
- hide side effects in opaque logs

## Design properties worth preserving

- explicit allowlists for commands and hosts
- per-job credentials or leases instead of long-lived env secrets
- structured results rather than free-form "it worked"
- stable delivery policy
- auditable artifacts

## Why this is especially important for AI-native systems

The more capable the model becomes, the more important it is to narrow and explain the execution surface.

A stronger model is not a substitute for:
- sandboxing
- scope enforcement
- policy checks
- operator visibility
