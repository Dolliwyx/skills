# Skills

Personal agent skills, plus an inventory of external skills installed locally.

## Skills in this repo

| Skill | Description |
| --- | --- |
| [`conventional-commits`](conventional-commits/SKILL.md) | Create git commits using Conventional Commits with scoped, reviewable changes. Use when the user asks to commit changes, make a conventional commit, write a commit message, or prepare staged changes for commit. |
| [`create-pr-mr`](create-pr-mr/SKILL.md) | Prepare and create pull requests or merge requests with clear change summaries, affected files, and correct target branches. Use when the user asks to create, open, draft, update, or prepare a PR, pull request, MR, or merge request. |
| [`create-subagents`](create-subagents/SKILL.md) | Create or configure custom agents for pi-subagents, including updates to existing agents and overrides of bundled agents. |
| [`dolli-mode`](dolli-mode/SKILL.md) | Ground the task in code, clarify decisions, confirm intent visually, then implement and verify with bounded delegation when useful. |
| [`google-developer-docs-style`](google-developer-docs-style/SKILL.md) | Write or edit developer documentation according to the Google developer documentation style guide. Use for tutorials, how-to guides, concepts, API or CLI references, README files, and documentation style reviews when Google style is requested or established for the project. |
| [`implement`](implement/SKILL.md) | Execute the session's existing plan by delegating independent work to leaf subagents, integrating changes, and verifying the result. |
| [`implementation-notes`](implementation-notes/SKILL.md) | Maintains a running repo-root implementation-notes.html file that records how implementation decisions interpret, clarify, or diverge from a spec. Use when the user explicitly asks for implementation notes, maintaining implementation-notes.html, tracking decisions, capturing spec deviations, recording tradeoffs, or keeping running notes while implementing. |
| [`meeting-notes`](meeting-notes/SKILL.md) | Generate structured meeting notes from agendas, transcripts, rough notes, or meeting summaries. Use when the user asks to create, organize, clean up, or format meeting notes. |
| [`obsidian-writing`](obsidian-writing/SKILL.md) | Write and maintain notes in the user's local Obsidian vault. Use when a task targets an Obsidian note, daily note, vault task, property, tag, wikilink, or folder. |
| [`ponytail`](ponytail/SKILL.md) | Runs a terse pre-code minimalism check -- delete, stdlib, native platform, installed dependency, one-liner, then minimum custom code. Use when writing code, planning implementation, reviewing code, reducing code, or when user says ponytail. |
| [`shortcut-updates`](shortcut-updates/SKILL.md) | Gets concise Shortcut story updates grouped for review. Use when user asks for Shortcut updates, unfinished stories, owned stories, story status summaries, or last updates/activity on Shortcut tickets. |
| [`support-relay`](support-relay/SKILL.md) | Rewrite a technical braindump into a clear message for the support team. |

## Deprecated skills

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
