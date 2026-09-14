# Model routing

Use provider `openai-codex` and exact model IDs. Honor explicit user model and reasoning choices; otherwise use this routing:

| Model ID | Best-fit assignment | Starting reasoning |
| --- | --- | --- |
| `gpt-5.6-sol` | Complex implementation, ambiguous debugging, cross-cutting changes, security-sensitive review | Medium; high for difficult edge cases |
| `gpt-5.6-terra` | Default worker: bounded features, tests, exploration, straightforward fixes and review | Medium; low for readily checked work |
| `gpt-5.6-luna` | Extraction, classification, mechanical edits, repetitive transformations with explicit rules and cheap checks | Low |

These task assignments are local recommendations inferred from OpenAI's positioning, not measured repository benchmarks. Choose by ambiguity and consequences rather than file count. Use the least expensive tier whose output can be reliably checked; escalate uncertain or failed work through the main agent. Reserve xhigh/max for unusually difficult reasoning, not routine dispatch. The main agent retains integration and acceptance.

## Launch checks

Run `pi --offline --no-extensions --list-models openai-codex` to resolve the installed catalog. All three IDs were present when this reference was written. Confirm the selected pair and supported reasoning setting in the current harness before dispatch; a catalog entry does not prove account access or a successful request.

For Pi, pass `--provider openai-codex --model <exact-id> --thinking <level>`. For internal subagents, pass `openai-codex/<exact-id>` and the harness's explicit reasoning option. If either control is unavailable, report the limitation and request a routing decision instead of silently substituting defaults.

The API pages list none through max for GPT-5.6. Pi uses its own reasoning vocabulary; use supported Pi settings rather than passing API `none` literally. API context windows, tools, and pricing are not guarantees for the Codex subscription route; use the installed provider metadata and current account limits.

## Sources

- [GPT-5.6 Sol](https://developers.openai.com/api/docs/models/gpt-5.6-sol): flagship for complex professional work.
- [GPT-5.6 Terra](https://developers.openai.com/api/docs/models/gpt-5.6-terra): intelligence/cost balance, corresponding roughly to the earlier mini tier.
- [GPT-5.6 Luna](https://developers.openai.com/api/docs/models/gpt-5.6-luna): cost-sensitive, high-volume workloads, corresponding roughly to the earlier nano tier.
