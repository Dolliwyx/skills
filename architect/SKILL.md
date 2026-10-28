---
name: architect
description: Architect, plan, or design features, workflows, and systems grounded in the repository, or review existing software architecture. Requires explicit approval before implementation.
---

# Architect

Produce a decision-ready brief recommending the smallest architecture that meets demonstrated requirements.

## Frame and investigate

Infer whether the request needs a design, a review, or review findings followed by a design. Establish the goal, boundaries, constraints, and observable success criteria. Investigate facts; ask about consequential choices with a recommendation and tradeoff. Carry low-impact assumptions into the brief.

Trace relevant implementation, callers, interfaces, data flow, and tests, including infrastructure and cross-system boundaries where they affect the decision. Investigate uncertainties that could change the recommendation. Assess compatibility, data integrity, security, failure modes, performance, operations, and migration where relevant.

Support material claims with repository references or check results. Distinguish observations, inferred risks, and unknowns; resolve blocking unknowns before recommending a design.

Use non-mutating checks within existing permissions. When inspection cannot settle a material uncertainty, propose a bounded experiment and obtain approval before writes, state changes, or external effects. Experiment approval covers only that experiment.

## Present the brief

Scale the structure to the decision. Keep the brief in the conversation unless the user requests a document or ADR; follow repository documentation conventions when saving it.

**Design:** cover the goal, success criteria, and exclusions; recommended responsibilities, boundaries, interfaces, and data flow tied to repository areas; meaningful alternatives (including the status quo when viable) and tradeoffs; risks, assumptions, unresolved decisions, and transition/recovery needs; proposed implementation scope, sequencing, affected callers/tests, and verification. Add extension points only for demonstrated requirements.

**Review:** lead with actionable findings ranked by consequence. For each, cite the affected location or boundary, explain the problem and conditions that expose it, and recommend the smallest sufficient correction. Separate demonstrated problems from conditional concerns; tie architectural preferences to concrete requirements or consequences. Say when no actionable findings are supported. Finish with coverage, unchecked areas, and any proposed implementation and verification scope. Recommend redesign only when findings justify it.

## Approval gate

For implementation, stop after the brief and obtain explicit approval of its implementation and verification scope—even if the initial request said “design and implement.” Saving a document or approving an experiment does not satisfy this gate. Advice-only requests end with the brief, without soliciting implementation.

After approval, follow the repository workflow within the agreed scope. Seek renewed approval if new evidence materially changes the scope, architecture, or permissions.
