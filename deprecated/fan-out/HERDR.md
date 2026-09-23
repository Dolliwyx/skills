# Herdr quick usage

Use this reference for the Herdr route. Resolve authorization first: require an explicit user request for Herdr unless applicable higher-priority policy authorizes it. Confirm `HERDR_ENV=1` and Herdr tools are available. A missing prerequisite is a blocker, not permission to switch routes. Keep Herdr and internal subagents separate within a workstream unless the user requests the combination.

Before launch, apply [model routing](MODELS.md) and the [leaf-worker gate](LEAF-WORKERS.md). Current tool schemas and `pi --help` are authoritative for syntax; the sequence below is a compact example, not permission to expand scope.

## Create → start → prompt → read

1. Create a shell pane with `herdr_layout`. Default to a sibling in the caller's current tab and cwd, preserving focus:

   ```json
   {"action":"pane_split","focus":false}
   ```

   Read the opaque pane ID from the result. Set `cwd` explicitly for an assigned checkout. Create a workspace or tab only when requested. Reuse a pane only if created for this workstream or explicitly authorized for reuse; an idle agent is not permission to assign it work.

2. Start Pi in that pane with the selected model, reasoning, and restricted tools. Example for a read-only Terra worker:

   ```json
   {
     "action":"start",
     "pane":"<returned-pane-id>",
     "name":"review-api",
     "kind":"pi",
     "agentArgs":[
       "--provider","openai-codex",
       "--model","gpt-5.6-terra",
       "--thinking","medium",
       "--no-extensions",
       "--tools","read,grep,find,ls"
     ]
   }
   ```

   Use a unique live name. For an editing assignment, use the editing allowlist in the leaf-worker reference. Layout creation does not start an agent; `start` requires an available shell pane.

3. Send the complete brief through `herdr_agent`, including the leaf restriction:

   ```json
   {"action":"prompt","target":"review-api","prompt":"<self-contained brief>","wait":true}
   ```

   For multiple independent workers, submit their calls concurrently when the harness permits. Keep disjoint file ownership or isolated checkouts. If a wait times out, inspect and continue waiting on the same worker; a timeout is not a failed assignment.

4. Read the response through `herdr_agent`:

   ```json
   {"action":"read","target":"review-api","source":"recent-unwrapped","lines":200}
   ```

   Inspect evidence and actual edits before acceptance. Use `herdr_agent` for agent prompts, waits, reads, and keys. Use `herdr_pane` only for ordinary processes; use `wait_output` for tests, builds, servers, and watchers in main-agent-controlled panes.

## Recovery and cleanup

- `idle` and `done` mean ready to inspect, not verified success. Inspect `blocked` for required input; treat `unknown` as uncertain and recover state before proceeding.
- Use `herdr_agent wait` to await settlement and send corrections to the same worker. Resolve file ownership before replacing a worker; explain the replacement and blocker in the main thread.
- If increasing the read length cannot recover a full response, ask an editing-capable worker to write its report to an agreed temporary Markdown path and read it directly. For a read-only worker, request smaller numbered response chunks instead of granting write access.
- Preserve panes you did not create unless the user asks to close them. Close only your own finished panes when no further inspection is needed; closing a pane is not required for acceptance.

**Complete:** every worker's result is collected, evidence is checked, and outstanding failures or unrun checks are reported by the main agent.
