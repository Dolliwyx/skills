---
name: create-subagents
description: Create or configure custom agent types for @tintinweb/pi-subagents when the user wants a new subagent, changes to an existing agent, or an override of Explore, Plan, or general-purpose.
---

# Create pi subagents

Build the smallest authoritative agent definition for `@tintinweb/pi-subagents`.

## 1. Resolve the contract

Determine the agent's name, purpose, scope, capabilities, model, and thinking level from the request. Ask only for decisions that cannot be inferred safely, especially scope:

- Global: `$PI_CODING_AGENT_DIR/agents/<name>.md`, defaulting to `~/.pi/agent/agents/<name>.md`
- Project: `.pi/agents/<name>.md`
- Shared project fallback: `.agents/agents/<name>.md`

Priority is `.pi` project, `.agents` project, then global. An exact filename match overrides a built-in agent. This step is complete when one destination and one behavioral contract are unambiguous.

## 2. Pin execution policy

Use frontmatter to enforce capabilities instead of relying on prose. Include only fields needed by the contract:

```yaml
---
description: When this agent should be used
display_name: Optional UI name
tools: read, grep, find, ls, bash
model: provider/model-id
thinking: high
prompt_mode: replace
---
```

Key fields:

- `tools`: built-ins, `*`, `none`, or `ext:<extension>/<tool>` selectors
- `extensions`: `true`, `false`, or an explicit list
- `disallowed_tools`: deny tools after allowlisting
- `model`: exact `provider/modelId` preferred
- `thinking`: `off`, `minimal`, `low`, `medium`, `high`, `xhigh`, or `max`
- `prompt_mode`: `replace` for a standalone specialist; `append` for parent instructions plus the body
- `max_turns`, `inherit_context`, `run_in_background`, `isolated`, `isolation`, `skills`, `memory`, `persist_session`, and `output_transcript`: add only when requested

Frontmatter values for model, thinking, and execution strategy are authoritative and cannot be overridden by the caller. If a model is pinned, verify its exact identifier with `pi --list-models`. This step is complete when every requested constraint is encoded structurally and no speculative field remains.

## 3. Write the agent prompt

Write the Markdown body as an operational system prompt:

1. State the role and expected result.
2. Give the process in task order, adapting only where the role requires judgment.
3. Define a checkable output contract.
4. Put hard safety boundaries in frontmatter where possible; pair unavoidable prohibitions with the positive behavior to follow.

For read-only agents, omit `write` and `edit`; restrict Bash to named read-only uses in the body. For agents that modify code, name verification expectations and keep changes scoped to the assigned task. This step is complete when the agent can execute without hidden assumptions or unrelated behavior.

## 4. Verify the definition

Read the completed file and confirm all of the following:

- Destination matches the requested scope and precedence.
- Filename is the intended `subagent_type`, including built-in override casing where relevant.
- YAML is valid and the description explains when to use the agent.
- Tool access matches the role.
- A pinned model exists and thinking is supported; report any clamping risk.
- Body and frontmatter agree.
- No duplicated or no-op instruction remains.

Tell the user the path, effective model/thinking, tool boundary, and that a new session or reload may be required. Completion requires every check above to pass.

For extension fields or behavior not covered here, read `$PI_CODING_AGENT_DIR/npm/node_modules/@tintinweb/pi-subagents/README.md` (default `~/.pi/agent/npm/node_modules/@tintinweb/pi-subagents/README.md`) before deciding.
