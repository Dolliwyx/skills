---
name: bug-investigation
description: Investigate a bug with evidence, then request approval before applying the smallest justified fix.
disable-model-invocation: true
---

# Bug investigation

## Investigate

1. Establish expected and actual behavior, the triggering input, and relevant environment. Inspect existing working-tree changes and preserve unrelated work.
2. Reproduce safely when possible using a focused test or exact command. Record the input, command, and observed failure; distinguish the reported symptom from what you reproduced.
3. Trace the relevant execution path through callers, state, and affected dependencies. Cite file and line references for consequential findings.
4. Rank up to three plausible root-cause hypotheses. For each, record supporting evidence, contradicting evidence, and the observation that would distinguish it from credible alternatives. Mark missing evidence explicitly; use fewer hypotheses when warranted.

Before diagnosis, edits are limited to focused reproduction tests and minimal temporary instrumentation. Do not make speculative behavior changes.

## Resolve uncertainty

When evidence does not distinguish the hypotheses:

1. Inspect the unresolved code paths and choose the smallest test or probe whose possible outcomes separate the hypotheses.
2. Add only the temporary instrumentation needed to capture those observations. Avoid secrets and sensitive payloads; keep probes bounded and preserve application behavior.
3. Run the reproduction and analyze the captured output against each hypothesis, updating their ranking. A proposed probe or predicted output is not observed evidence.
4. If reproduction requires the user's environment, provide exact prerequisites, commands or UI actions, expected distinguishing signals, and instructions for capturing and safely sharing output. Identify any probes left in place and wait for results.

Remove your temporary instrumentation once its evidence is captured, before the approval handoff; retain useful regression tests. Preserve unrelated logging and user changes. If evidence remains inconclusive, report the missing observation and next discriminating check rather than asserting a root cause.

## Evidence and approval gate

A supported root cause needs a failing test, runtime observation, or concrete code-path proof that explains the symptom and distinguishes it from credible alternatives. Code inspection can suffice when it establishes that proof; plausibility alone cannot.

Report concisely:

- Reproduction command or steps, actual result, and any environment limitation.
- Ranked hypotheses with evidence for and against each.
- The best-supported root cause, with file and line references, separating observations from assumptions and remaining uncertainty.
- The smallest proposed fix and how it will be verified.

Ask for explicit approval and stop before implementing the fix. If the evidence gate is unmet, request the missing evidence instead of approval to fix.

## After approval

Apply the smallest change justified by the evidence, covering affected callers and tests without unrelated cleanup. Prefer a regression test demonstrated to fail for the original bug and pass after the fix; disclose when that demonstration is infeasible.

Verify the original reproduction and relevant existing checks. Confirm your temporary instrumentation is gone and rerun affected checks if cleanup changed code. Report what changed, checks actually performed, and remaining limitations.
