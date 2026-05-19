---
name: create-pr-mr
description: Prepare and create pull requests or merge requests with clear summaries, test notes, and correct target branches. Use when the user asks to create, open, draft, update, or prepare a PR, pull request, MR, or merge request.
---

# Create PR or MR

## Quick Start

1. Inspect repo state: `git status --short`, `git branch --show-current`, `git remote -v`, and recent commits.
2. Identify the hosting tool:
   - GitHub: prefer `gh pr create`
   - GitLab: prefer `glab mr create`
   - Unknown or unavailable CLI: prepare the title/body and tell the user what could not be run.
3. Confirm the branch is pushed or push it when appropriate.
4. Create a concise PR/MR with:
   - Title matching the change, often Conventional Commit style.
   - Summary bullets focused on behavior.
   - Test or verification notes.
   - Risk, rollout, or follow-up notes when relevant.

## Before Creating

Check whether the branch already has an open review request with `gh pr view --json number,title,url,state` or `glab mr view`.

If a PR/MR already exists, update or report it instead of creating a duplicate.

Make sure local commits are ready with `git status --short` and `git log --oneline origin/HEAD..HEAD`.

If `origin/HEAD` is unavailable, inspect remotes and infer the default branch from repo conventions such as `main`, `master`, or `develop`.

## Branch and Push

Use the current branch unless the user requested a different one. Avoid creating PRs from protected default branches.

Push the branch non-interactively with `git push -u origin HEAD`.

If network access or credentials fail, stop and report the exact blocker. Do not invent a PR URL.

## PR/MR Body Template

Use this structure by default:

```md
## Summary
- ...
- ...

## Verification
- ...

## Notes
- ...
```

Omit `Notes` when there is nothing meaningful to say. Include screenshots or links only when they exist.

For bug fixes, mention the user-visible problem and the corrected behavior. For UI changes, include screenshots or state that screenshots were not captured. For migrations or operational changes, include rollout and rollback notes.

## GitHub

Create a PR with `gh pr create --base main --head current-branch --title "..." --body "..."`.

Use `--draft` when the user asks for a draft or when the change is intentionally not ready for review.

Useful follow-ups: `gh pr view --web`, `gh pr checks`, and `gh pr edit --title "..." --body "..."`.

## GitLab

Create an MR with `glab mr create --target-branch main --source-branch current-branch --title "..." --description "..."`.

Use draft status when the user asks for draft/WIP or the work is not ready.

Useful follow-ups: `glab mr view` and `glab mr update --title "..." --description "..."`.

## Review Hygiene

- State the PR/MR URL after creation.
- Mention any tests that were not run and why.
- Do not hide local uncommitted changes. If unrelated changes remain, say so.
- Do not force-push, rebase public branches, or retarget branches unless the user requested it.
- Keep the title and body factual; avoid marketing language.
