---
name: bug-diagnosis-retrospective
description: Diagnose and reproduce reported software bugs or unexpected behavior, seek approval for a fix, and retrospect on automated prevention.
---

# Bug diagnosis and retrospective

## 1. Diagnose

Trace the reported behavior through the relevant code and callers. Reproduce the failure with the smallest practical check, recording the inputs, environment, expected and actual behavior. Use temporary artifacts only; leave project files unchanged before fix-plan approval. Obtain explicit approval before destructive actions or actions with external side effects.

Test competing explanations with safe checks until the evidence supports a cause or further investigation is blocked. If reproduction fails, report what was tried and offer evidence-based next steps: request missing information or seek approval for a clearly labeled best-effort fix with an alternative verification plan. Do not present an unverified cause as fact.

## 2. Propose and wait

Present the reproduction and evidence, root cause and uncertainty, affected scope, proposed fix, regression and verification checks, and risks. Ask for approval of the fix plan and wait. If implementation later requires a materially different approach or scope, present the change and obtain approval again.

## 3. Fix and verify

Implement the approved plan. Add a targeted automated regression test when feasible; otherwise explain the limitation and use the best available verification. Where practical, demonstrate that the regression check fails on the bug and passes with the fix. Run the relevant checks and report their results or blockers.

## 4. Retrospect

For the reported bug, trace the relevant tests, CI configuration, rules and instructions, and other available evidence. Identify a specific automated check that could have detected it, the earliest practical lifecycle stage to run it, and why the existing safeguards did not catch it. Consider local development, CI, review, deployment and production monitoring where relevant. Separate observed gaps from hypotheses; state what remains unknown rather than inventing a cause.

Rank actionable prevention recommendations by value and trade-offs, including when each would run and how it would detect the bug. Distinguish the fix's regression test from potential earlier or broader safeguards. Report findings in the conversation and ask for separate approval before changing prevention safeguards.

## 5. Apply approved prevention

If the user approves a recommendation, implement only the approved safeguards and verify them. Where feasible, demonstrate that the check detects the original bug. Report the changes, checks and any remaining limitations.
