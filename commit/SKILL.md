---
name: commit
description: Create Conventional Commits or draft commit messages with motivation-focused bodies.
---

## Scope

Create commits only when explicitly requested; message requests produce drafts. Inspect repository instructions, commit tooling, recent subjects, and staged/unstaged changes, including untracked files. Follow compatible repository conventions; ask about conflicts.

Include only changes belonging to the requested task; ask when ownership is unclear. Preserve unrelated changes and staging. Split clearly independent work into cohesive commits; ask when boundaries are ambiguous.

## Message

Use Conventional Commits: `type(scope)!: description`. Scope is optional; `!` marks breaking changes. Prefer repository types; otherwise use familiar types such as `feat`, `fix`, `docs`, `refactor`, `test`, and `chore`. Use `feat` for features and `fix` for bug fixes.

Prefer a subject of at most 50 characters, counting the prefix; exceed it when clarity requires. Separate subject, body, and footers with blank lines.

For nontrivial changes, explain the problem or motivation, then the chosen approach and meaningful consequences in separate paragraphs. One substantive paragraph is enough when there is only one genuine point. Ground rationale in available evidence; ask if essential motivation is missing. Avoid padding and diff narration.

Omit the body only for obvious, self-explanatory mechanical edits such as typos or formatting. A small behavioral diff is not trivial.

Mark breaking changes with `!` or a `BREAKING CHANGE: ...` footer describing the incompatibility and required migration. Preserve required trailers; use Conventional Commit footer syntax (`Token: value` or `Token #value`).

## Commit

Review the exact staged diff for each commit, ensuring its scope and message agree. Stage only authorized changes; never sweep unrelated staged content into a commit. If isolation would disturb unrelated staging, ask first. This skill adds no test-running requirement; honor repository requirements and report known failures.

Use plain commits and honor hooks. Amendments, history rewriting, hook bypasses, and pushes each require explicit authorization. On failure, stop and report rather than retrying with safeguards disabled.

After committing, verify the resulting commit and remaining status. Report commit hashes and subjects, plus any remaining changes or verification limits. For drafts, return only the proposed message.
