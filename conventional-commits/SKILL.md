---
name: conventional-commits
description: Create git commits using Conventional Commits with scoped, reviewable changes. Use when the user asks to commit changes, make a conventional commit, write a commit message, or prepare staged changes for commit.
---

# Conventional Commits

## Quick Start

1. Inspect the worktree: `git status --short`, `git diff --stat`, `git diff`, and `git diff --staged`.
2. Identify which changes belong to the requested commit.
3. Stage only relevant files or hunks.
4. Write a Conventional Commit message:
   - `type(scope): summary`
   - Body when context, motivation, or risk notes matter.
   - Footer for breaking changes or issue references.
5. Commit non-interactively with `git commit -m "type(scope): summary"` and extra `-m` paragraphs when needed.

## Commit Message Rules

Use lowercase type names. Prefer:

- `feat`: user-facing or product capability
- `fix`: bug fix
- `docs`: documentation only
- `style`: formatting only, no behavior change
- `refactor`: code restructuring without behavior change
- `perf`: performance improvement
- `test`: tests only
- `build`: build system or dependency changes
- `ci`: CI configuration
- `chore`: maintenance that does not fit above
- `revert`: revert a previous commit

Use a scope when it clarifies ownership or affected area, such as `api`, `ui`, `auth`, `deps`, `docs`, or a package name. Omit scope when it would be vague.

Keep the summary imperative, specific, and under about 72 characters. Do not end it with punctuation.

Examples: `feat(auth): add passkey registration`, `fix(api): reject expired invite tokens`, `docs: document local setup`.

## Safety Workflow

Before staging or committing:

- Check for unrelated user changes and leave them untouched.
- If the worktree contains unrelated edits in files needed for the commit, inspect carefully and stage only the relevant hunks.
- Never run destructive git commands such as `git reset --hard` or `git checkout --` unless the user explicitly requested them.
- If pre-commit hooks modify files, inspect the resulting diff before attempting another commit.

## Staging Guidance

Use file staging for cleanly related files: `git add path/to/file`.

Use patch staging when relevant and unrelated edits share a file: `git add -p path/to/file`.

After staging, verify with `git diff --staged --stat` and `git diff --staged`.

## Commit Body

Add a body when the summary alone does not explain the change:

```sh
git commit \
  -m "fix(cache): prevent stale workspace reads" \
  -m "Invalidate cached workspace metadata when the selected account changes." \
```

## Breaking Changes

Use `!` and a footer for breaking changes:

```text
feat(api)!: rename token exchange endpoint

BREAKING CHANGE: /token/exchange is replaced by /oauth/token.
```

Only mark a breaking change when callers, users, stored data, or deployment expectations must change.
