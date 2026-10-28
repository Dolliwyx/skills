---
name: dolli-mode
description: Ground the task in code, clarify decisions, confirm intent visually, then implement and verify with bounded delegation when useful.
disable-model-invocation: true
---

# Dolli mode

Use the accompanying prompt and conversation context as the task; ask if none is identifiable. Follow the five gates below for implementation. For explanations, investigations, and reviews, use gates 1–2 as needed and deliver a read-only result with a visual where useful; implementation approval does not apply.

For architecture, planning, or design requests, follow [architect](../architect/SKILL.md) during gates 1–3 and use its brief for confirmation. Planning-only requests end with the brief.

Stay read-only until approval. Invocation authorizes context exploration and, after approval, bounded implementation delegation. Consequential external actions need separate authorization. Report blocked prerequisites and pause dependent work.

## 1. Gather context

Inspect repository instructions and workspace changes; surface ownership conflicts. Search and read directly for targeted lookups. Delegate open-ended discovery to a read-only explorer with the task, lookup questions, and search breadth. Request paths and symbols, existing patterns, available checks, and unresolved facts; prohibit further delegation.

Read the relevant files yourself before making decisions. Advance when affected behavior and change sites, existing patterns, and verification options are grounded in sources. Track pending facts so independent questions can proceed.

## 2. Clarify decisions

Resolve material scope, behavior, design, and acceptance decisions using [grilling](../grilling/SKILL.md). Override its prose format with `ask_user_question`: recommendations and up to four independent questions per round. Find facts through gate 1 rather than asking the user; targeted lookups override grilling's subagent rule. Unambiguous tasks need no interview.

Carry constraints and decisions forward. Advance when material decisions are settled and facts needed for the next gate are checked; running exploration remains an open prerequisite.

## 3. Confirm intent visually

Show the agreed intent with the smallest useful inline visual: pseudocode, tree, diff, or diagram. Ground it in files read, include relevant paths, and label proposals and assumptions. Show whole blocks when omitted context would obscure ownership or order.

Pair it with the outcome, scope, exclusions, consequential assumptions, observable acceptance criteria, planned checks, and direct or delegated approach with worker boundaries.

Ask: **“Does this match your intent, and may I proceed?”** Wait for explicit approval of the current scope and approach, even when no interview was needed. Interview answers are not implementation approval. Corrections require updated confirmation.

## 4. Implement

Implement small, cohesive changes directly; delegate bounded work when useful. Use configured model and reasoning defaults unless the user specifies otherwise. Each worker gets:

- Approved objective, relevant context, concrete changes, owned files or isolated scope, exclusions, and preservation of others' work.
- Observable acceptance criteria, required checks, and a report of changed files, actual check results, blockers, and uncertainty.
- No further delegation through any mechanism; return scope conflicts and blockers to the parent.

Parallelize independent work with non-overlapping ownership or isolated worktrees; sequence dependencies. Continue independent work while background agents run and await notifications rather than polling. If delegation is unavailable, disclose it and work directly within scope.

Return material scope or behavior changes to clarification and approval. Advance when every agreed change is implemented and every delegated result received; blockers mean partial work.

## 5. Verify and show changes

Inspect actual changes against every approved acceptance criterion; worker summaries are not proof. Integrate results, run meaningful and repository-required checks, fix caused failures, and recheck affected behavior.

Show relevant actual changes using gate 3's visual guidance and file paths, distinguished from the proposal. Report outcome, changed files, checks actually run and results, and limitations. Claim completion only when every criterion has evidence and required checks pass; otherwise report partial or blocked work and the missing evidence.
