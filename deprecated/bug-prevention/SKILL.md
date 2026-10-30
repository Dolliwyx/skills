---
name: bug-prevention
description: Turn a software bug or agent failure into the smallest verified prevention change.
disable-model-invocation: true
---

# Bug prevention

Cover the incident, affected callers, and sibling cases sharing its root cause; leave unrelated defects alone.

## Explain before editing

Establish expected behavior, actual behavior, and root cause from incident evidence, code/history, checks, and applicable instructions. For agent failures, inspect the available transcript and context at the decision point. Reproduce safely where practical; distinguish findings from hypotheses.

If evidence cannot justify a prevention change, stop, report what is missing, and ask for evidence unavailable locally. Otherwise, explain the bug, root cause, and supporting evidence to the user before editing any files.

## Identify the escape

Answer with evidence:

1. **What specific check should have caught this bug?** Name its input and observable failure.
2. **At what stage should that check have run?** Choose the earliest reliable stage with the necessary information.
3. **Why didn't existing tests, rules, or instructions catch it?** Distinguish missing coverage, ineffective assertions, skipped execution, wrong stage, unclear instructions, and missing context. Verify execution where possible; mark unknowns.
4. **What change will catch it automatically?** Identify executable protection and its execution path, or explain why reliable automation is unavailable.

## Close the gap

Use existing project patterns for the smallest change addressing the evidenced escape mechanism. Prefer executable protection; add guidance only for gaps it leaves open.

**Red first:** before production-code edits, write or reuse a regression test and confirm it fails for the intended reason. For an already-fixed bug, demonstrate red against the buggy version in an isolated worktree, fixture, or bounded simulation preserving unrelated work. Explain any infeasible or inapplicable failing test and its verification limit before proceeding.

- Test gap → write or repair the regression test, asserting expected behavior.
- Execution gap → wire the existing check into the test command, hook, or CI at the chosen stage.
- Review gap → add an actionable rule where review occurs.
- Instruction gap → improve the authoritative instruction.
- Context gap → provide the nearest durable source and make it discoverable before the failing decision.

Local edits and verification are authorized. Obtain approval before changing shared agent instructions or review policies, introducing services, or taking destructive/external actions. Complete separable authorized work and present gated changes for approval.

## Verify and report

Confirm the regression test passes after the fix. For other executable protections, demonstrate detection where safely reproducible. Run relevant existing checks, fix failures caused by the change, and verify the protection's execution path.

For guidance/context, verify authority and discovery at the intended stage; inspection is not demonstrated behavioral improvement. Written guidance is not automation: disclose judgment-only gaps and any unverified detection.

Conclude in the conversation with the four answers, changes, actual verification, remaining gaps, and pending approvals. Save an incident note only if requested.
