# Leaf workers

Only the main agent delegates. Every internal subagent and Herdr worker is a leaf: it performs its assignment directly and returns to the main agent.

## Required brief

Include this restriction in every worker's instructions:

> Execute the assigned work directly and preserve unrelated changes. Only the main agent may delegate. Do not spawn subagents, launch workflows, create panes, or assign work to existing agents through tools, CLIs, scripts, or any other mechanism. Return blockers, scope conflicts, and requests for additional workers to the main agent. Keep your assigned tool restrictions unchanged.

## Enforce before dispatch

Use a worker tool allowlist, not just a prompt prohibition:

| Worker role | Pi tool allowlist |
| --- | --- |
| Read-only exploration or review | `read,grep,find,ls` |
| Editing assigned files | `read,grep,find,ls,edit,write` |

For Herdr Pi workers, launch with `--no-extensions --tools <allowlist>`. Keep repository context instructions loaded. Extension discovery stays off; explicit extensions require review for indirect execution and delegation capabilities before inclusion.

For internal subagents, select a worker configuration with equivalent restrictions. Inspect its actual tools before launching. A name such as `Explore`, an isolation flag, or a no-recursion prompt does not establish this boundary. If the harness cannot enforce a suitable tool surface, report the blocker and do the unit in the main agent rather than launching an unrestricted worker.

Exclude process execution, agent/workflow tools, Herdr controls, MCP gateways, scripting tools, and tool-enabling controls. Shell access can launch another agent or call Herdr even when their named tools are hidden. The main agent runs tests, builds, git operations, and other commands requested in worker reports after inspecting relevant changes. Workers report proposed commands separately from checks actually run.

If worker-side execution is essential, require an approved constrained runner that prevents delegation and access to Herdr control endpoints. Merely filtering command names is insufficient for arbitrary scripts. Without that runner, keep execution in the main agent.

**Dispatch gate:** the selected worker exposes only the approved tools, and its brief contains the leaf restriction. Prompt-only restrictions do not satisfy this gate. Tool allowlists constrain the agent's callable surface; they are not an OS sandbox for untrusted code.
