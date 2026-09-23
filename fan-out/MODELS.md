# Model routing

Use provider `openai-codex` and exact model IDs. Honor explicit user model and reasoning choices; otherwise use this routing:

| Model ID | Best-fit assignment | Starting reasoning |
| --- | --- | --- |
| `gpt-6-luna` | Default worker: bounded features, tests, exploration, straightforward fixes and review, mechanical transformations | Max |
| `gpt-6-sol` | Harder assignments: complex implementation, ambiguous debugging, cross-cutting changes, security-sensitive review | Medium; high for difficult edge cases |

These are local routing preferences, not measured repository benchmarks. Default to `gpt-6-luna` with `max` thinking; choose `gpt-6-sol` for harder assignments based on ambiguity and consequences rather than file count. Escalate uncertain or failed work through the main agent, which retains integration and acceptance.

## Launch checks

Run `pi --offline --no-extensions --list-models openai-codex` to resolve the installed catalog. Confirm the selected pair and supported reasoning setting in the current harness before dispatch; a catalog entry does not prove account access or a successful request.

For Pi, pass `--provider openai-codex --model <exact-id> --thinking <level>`. For internal subagents, pass `openai-codex/<exact-id>` and the harness's explicit reasoning option. If either control is unavailable, report the limitation and request a routing decision instead of silently substituting defaults.

Use supported Pi reasoning settings. API context windows, tools, and pricing are not guarantees for the Codex subscription route; use the installed provider metadata and current account limits.
