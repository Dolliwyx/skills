# Skills

Personal agent skills, plus an inventory of external skills installed locally.

## Skills in this repo

| Skill | Description |
| --- | --- |
| [`architect`](architect/SKILL.md) | Design or review repository-grounded software architecture, with an explicit approval gate before implementation. |
| [`bug-investigation`](bug-investigation/SKILL.md) | Investigate a bug with evidence, then request approval before applying the smallest justified fix. |
| [`bug-prevention`](bug-prevention/SKILL.md) | Explicitly invoked analysis of a software bug or agent failure, followed by the smallest verified prevention change. |
| [`changelog`](changelog/SKILL.md) | Create or update a changelog using Keep a Changelog. Use when asked to record notable changes, prepare a changelog for a release, or reconstruct release history. |
| [`commit`](commit/SKILL.md) | Create Conventional Commits or draft commit messages with motivation-focused bodies. |
| [`create-subagents`](create-subagents/SKILL.md) | Create or configure custom agents for pi-subagents, including updates to existing agents and overrides of bundled agents. |
| [`dolli-mode`](dolli-mode/SKILL.md) | Ground the task in code, clarify decisions, confirm intent visually, then implement and verify with bounded delegation when useful. |
| [`implement`](implement/SKILL.md) | Execute the session's existing plan by delegating independent work to leaf subagents, integrating changes, and verifying the result. |
| [`implementation-notes`](implementation-notes/SKILL.md) | Maintains a running repo-root implementation-notes.html file that records how implementation decisions interpret, clarify, or diverge from a spec. Use when the user explicitly asks for implementation notes, maintaining implementation-notes.html, tracking decisions, capturing spec deviations, recording tradeoffs, or keeping running notes while implementing. |
| [`meeting-notes`](meeting-notes/SKILL.md) | Generate structured meeting notes from agendas, transcripts, rough notes, or meeting summaries. Use when the user asks to create, organize, clean up, or format meeting notes. |
| [`obsidian-writing`](obsidian-writing/SKILL.md) | Write and maintain notes in the user's local Obsidian vault. Use when a task targets an Obsidian note, daily note, vault task, property, tag, wikilink, or folder. |
| [`ponytail`](ponytail/SKILL.md) | Runs a terse pre-code minimalism check -- delete, stdlib, native platform, installed dependency, one-liner, then minimum custom code. Use when writing code, planning implementation, reviewing code, reducing code, or when user says ponytail. |
| [`writing-tickets`](writing-tickets/SKILL.md) | Draft or refine bugs, feature suggestions, and chores with concise prose and useful visuals. Confirm the draft and destination before publishing. |

## Deprecated skills

- [`create-pr-mr`](deprecated/create-pr-mr/SKILL.md): superseded by the external [`visual-pr`](https://www.skills.sh/humanlayer/skills/visual-pr) skill.
- [`shortcut-updates`](deprecated/shortcut-updates/SKILL.md): archived Shortcut update skill.
- [`support-relay`](deprecated/support-relay/SKILL.md): superseded by the external [`bro`](https://www.skills.sh/backnotprop/bro/bro) skill.
- [`google-developer-docs-style`](deprecated/google-developer-docs-style/SKILL.md): superseded by the external `technical-writing` skill from [`cursor/plugins`](https://github.com/cursor/plugins).
- [`fan-out`](deprecated/fan-out/SKILL.md): superseded by `implement` for executing an existing session plan.
- [`herdr-delegation`](deprecated/herdr-delegation/SKILL.md): archived delegation skill.

## External skills

These are installed in `~/.agents/skills/` and maintained outside this repository.

| Source | Skills |
| --- | --- |
| [`cursor/plugins`](https://github.com/cursor/plugins) | `blast-radius`, `deslop`, `technical-writing`, `thermo-nuclear-code-quality-review`, `unslop` |
| [`backnotprop/bro`](https://github.com/backnotprop/bro) | `bro`, `facts` |
| [`anthropics/skills`](https://github.com/anthropics/skills) | `docx`, `frontend-design`, `pdf`, `pptx`, `xlsx` |
| [`mattpocock/skills`](https://github.com/mattpocock/skills) | `domain-modeling`, `grill-me`, `grill-with-docs`, `grilling`, `handoff`, `improve-codebase-architecture`, `prototype`, `retro`, `to-spec`, `wayfinder`, `writing-for-agents` |
| [`openai/skills`](https://github.com/openai/skills) | `hatch-pet` |
| [`pbakaus/impeccable`](https://github.com/pbakaus/impeccable) | `impeccable` |
| [`humanlayer/skills`](https://github.com/humanlayer/skills) | `show-me`, `visual-pr` |

### Codex-only skills

These are installed in `~/.codex/skills/` and listed here as external skills. Their installation metadata does not record an upstream source.

| Skill | Installed path |
| --- | --- |
| `doc` | `~/.codex/skills/doc` |
| `slides` | `~/.codex/skills/slides` |
| `spreadsheet` | `~/.codex/skills/spreadsheet` |
