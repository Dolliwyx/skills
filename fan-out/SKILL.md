---
name: fan-out
description: Decompose a large task into independent subagent assignments, reconcile their results, and deliver a validated final output.
disable-model-invocation: true
---

# Fan-out

The main agent owns decomposition, integration, and acceptance. Workers own bounded assignments. Use the delegation tools permitted by the current environment; invocation does not override permissions or execution policies.

## 1. Scope

Read the task and relevant source material. Define the final deliverable, constraints, and observable acceptance criteria. Ask for clarification only when missing information materially changes scope or correctness. If no task was supplied, ask for it before proceeding.

**Done:** the requested outcome and how to verify it are explicit.

## 2. Decompose

Build a compact work list. For each unit, record its goal, inputs, dependencies, output, acceptance check, and file ownership when editing. Account for every requirement with a unit or main-agent integration work.

Split along independent boundaries, not arbitrary sizes. Resolve shared interfaces and assumptions before dispatch. Sequence dependent units; parallelize only units that can finish without each other's unfinished results. Give concurrent writers disjoint files or isolated checkouts, with shared-file integration owned by the main agent.

Use the fewest workers that provide useful parallelism. If the task has no useful independent split, explain briefly and complete it directly.

**Done:** every requirement has an owner, dependencies are explicit, and concurrent assignments cannot overwrite each other's work.

## 3. Dispatch

Select the delegation route before launching workers:

- When `HERDR_ENV=1` and Herdr tools are available, read and follow [herdr-delegation](../herdr-delegation/SKILL.md) for preflight, dispatch, recovery, and acceptance.
- Otherwise, use the environment's internal subagent tools to fan out the units.
- Follow applicable authorization policies on either route. Report permission blockers rather than switching routes to bypass them. If neither route is available, report the blocker.

For either route, honor explicit user model and reasoning choices; otherwise select per work unit:

| Work unit | Model | Reasoning |
| --- | --- | --- |
| Complex implementation, ambiguous debugging, cross-cutting or security-sensitive work | `gpt-5.6-sol` | Medium for bounded complexity; high for difficult reasoning or edge cases |
| Bounded features, tests, exploration, straightforward fixes and review | `gpt-5.6-terra` | Medium by default; low when straightforward to verify |
| Mechanical edits, extraction, repetitive transformations with explicit rules | `gpt-5.6-luna` | Low |

Choose reasoning by ambiguity, dependencies, and consequences, not task size alone. Reserve xhigh/max for unusually difficult work when lower effort is insufficient. Resolve available provider-qualified model IDs and supported reasoning settings from local configuration or model listings, and pass both explicitly at launch. If the selected model or reasoning control is unavailable, report the limitation and ask for a routing decision rather than silently substituting defaults.

Send each ready worker a self-contained brief:

- Overall objective and why this unit matters.
- Exact assignment, relevant source paths or inputs, and established decisions.
- Read-only or editing authority, owned files, constraints, and exclusions.
- Expected output and acceptance check.
- Return completed work, evidence or check results, assumptions, and blockers. Identify changed files when applicable.
- Mandatory restriction for every Herdr worker and internal subagent: execute the assignment directly and preserve unrelated changes. Only the main agent may delegate. Do not create additional panes, spawn subagents, launch workflows, or assign work to existing agents through tools, CLIs, scripts, or any other mechanism. Return scope conflicts and requests for additional workers to the main agent.

Where the harness supports worker tool restrictions, disable delegation and pane-creation capabilities for workers as well as including the mandatory brief restriction. Treat prompt-only restrictions as instructions, not a technical sandbox.

Launch independent units concurrently within tool limits. Use the environment's supported completion mechanism and track each unit's state. While workers run, perform distinct integration preparation rather than duplicating their assignments.

**Done:** every ready unit has a dispatched owner and a defined return contract.

## 4. Collect and reconcile

Account for every dispatched unit as completed, partial, failed, or blocked. A missing response is not an empty finding or a successful check. Inspect returned artifacts and evidence rather than accepting summaries as proof.

Combine compatible results, deduplicate overlapping findings, and resolve contradictions against source material and acceptance criteria. Integrate edits without discarding unrelated changes. For a gap, retry with a narrower brief or complete it directly within authorization; if it remains blocked, record its effect on the deliverable.

**Done:** every unit is accounted for, every accepted result has supporting evidence, and conflicts are resolved or explicitly identified as unresolved.

## 5. Validate and deliver

Check the integrated result against every original acceptance criterion. For code, inspect actual diffs and run relevant tests, including cross-unit behavior. For research or documents, verify material claims against sources and check coverage and consistency. Distinguish checks actually run from proposed checks.

Return one coherent deliverable, not concatenated worker reports. Include concise verification evidence and any remaining limitations or blockers. Claim completion only for criteria supported by the integrated result.

**Done:** the final output addresses the original task, with verified outcomes separated from incomplete or uncertain work.
