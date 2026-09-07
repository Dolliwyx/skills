---
name: herdr-delegation
description: Delegate bounded exploration, implementation, or review through Herdr when authorized by the user or applicable project policy. Requires HERDR_ENV=1. Covers worker model selection, dispatch, pane lifecycle, recovery, and verification.
---

# Herdr Delegation

## Preconditions

1. Resolve authorization under the applicable instruction hierarchy. Follow explicit project delegation policy; otherwise require an explicit user request for Herdr. If higher-priority instructions prohibit the requested delegation, identify the conflicting instruction and report the blocker.
2. Confirm that `HERDR_ENV=1` and Herdr tools are available. If either is missing, report the blocker rather than silently switching to internal subagents.
3. Define a bounded objective and worker role: exploration and review are read-only; implementation permits changes only within assigned ownership. The main agent retains task understanding, decomposition, and final acceptance.
4. Keep Herdr and internal-subagent delegation separate within a workstream unless the user explicitly requests the combination.

Preflight is complete when authorization, environment, role, and scope are explicit.

## Worker Model Selection

Honor explicit user choices. Otherwise select by ambiguity and consequence, not task size alone:

| Model | Assignment | Reasoning |
|---|---|---|
| Sol | Ambiguous debugging, complex implementation, cross-cutting changes, security-sensitive review | Medium; high for difficult edge cases |
| Terra | Default worker for bounded features, tests, exploration, straightforward fixes and review | Medium |
| Luna | Mechanical edits, extraction, repetitive transformations with explicit rules and cheap verification | Low |

When uncertain between worker tiers, choose the stronger tier. Reserve xhigh/max for unusually difficult problems when lower effort proves insufficient. Workers return unexpected complexity to the main agent rather than changing scope or delegating.

Resolve the exact available provider/model ID and supported reasoning setting from local configuration or Pi's model listing before launch. Pass them explicitly in `herdr_agent start` arguments; do not rely on an inherited default or invent an ID. If the selected model is unavailable, report it to the main thread for a routing decision.

This routing is a local recommendation based on the vendor's positioning: [Sol](https://developers.openai.com/api/docs/models/gpt-5.6-sol) for complex professional work, [Terra](https://developers.openai.com/api/docs/models/gpt-5.6-terra) for intelligence/cost balance, and [Luna](https://developers.openai.com/api/docs/models/gpt-5.6-luna) for cost-sensitive, high-volume workloads. A web lookup is not required for each dispatch.

## Dispatch

1. Create a fresh pane with `herdr_layout` for each new delegated workstream. Default to a sibling pane in the caller's tab and working directory; if the user names a workspace, create the pane there. Preserve focus unless asked otherwise. Reuse a pane only when created for the same workstream or explicitly identified by the user for reuse. An idle agent is not permission to reuse its pane; naming a workspace does not authorize messaging its existing agents.
2. Parallelize only independent workstreams. Assign explicit file ownership for implementation, using isolated checkouts when concurrent modifications could overlap. Require workers to preserve changes outside their assignment.
3. Start `pi` through `herdr_agent` in the new shell pane with the selected model and reasoning effort. Use `herdr_agent` for agent prompts, lifecycle waits, reads, and interactive keys; use `herdr_pane` for ordinary commands, not coding-agent interaction.
4. Send a brief containing:
   - Objective and relevant context.
   - Role, scope, exclusions, and owned files or read-only search boundary.
   - Observable acceptance criteria and expected verification commands or evidence.
   - Required report: findings or changed files, checks and results, unresolved issues.
   - Restriction: work directly within the assigned scope; do not spawn agents, launch workflows, create panes, or delegate through any mechanism. Return blockers, unexpected complexity, and requests for additional workers to the main thread.
5. Prompt with waiting enabled, then read the worker's response. Use the returned pane ID or unique live agent name rather than constructing a target.

## Recovery and Acceptance

- Treat `idle` and `done` as ready to inspect, not proof of success. For `blocked` or `unknown`, inspect the response and state before deciding whether input or another wait is needed.
- Send corrections to the same worker. If a worker cannot continue, report the blocker and replacement rationale before starting a replacement; resolve file ownership before another worker writes the same files.
- If terminal reads cannot recover the full response after increasing the line count, ask the worker to write its complete report to a temporary Markdown file and read it directly.
- Inspect actual changes and verification results before accepting implementation. For exploration or review, check cited files and evidence for the findings used in the final answer. Worker summaries alone are not proof.
- Leave panes you did not create open unless the user asks to close them.

The work is complete when every assigned workstream has reported, the main agent has checked its evidence, required verification passes, and required revisions are resolved. Report remaining blockers or unrun checks explicitly.
