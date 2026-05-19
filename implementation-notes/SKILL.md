---
name: implementation-notes
description: Maintains a running repo-root implementation-notes.html file that records how implementation decisions interpret, clarify, or diverge from a spec. Use when the user explicitly asks for implementation notes, maintaining implementation-notes.html, tracking decisions, capturing spec deviations, recording tradeoffs, or keeping running notes while implementing.
---

# Implementation Notes

## Purpose

Maintain `implementation-notes.html` at the repository root while working. The file is a lightweight audit trail for implementation context the user should know about: design decisions, intentional deviations, tradeoffs, and open questions.

Use this skill only when explicitly requested by the user. Do not activate it just because a task involves implementation.

## Operating Rules

1. Locate the repository root before editing notes. If the root is ambiguous, use the current working directory and state that assumption.
2. Create `implementation-notes.html` at the repo root if it does not exist.
3. If the file exists, preserve prior entries and append a new task entry. Do not rewrite or normalize old entries except to repair malformed HTML required to append safely.
4. Update the file at meaningful checkpoints, especially after discovering a decision, deviation, tradeoff, or open question.
5. If a question affects correctness, stop and ask the user. Use the notes file only for non-blocking uncertainty.
6. Omit secrets, credentials, tokens, private personal data, and sensitive config values.
7. Mention in the final response that `implementation-notes.html` was updated.

## Entry Format

Each task entry should be timestamped and include these sections:

- Summary
- Design decisions
- Deviations
- Tradeoffs
- Open questions

Keep entries concise. Include relevant file paths, ticket names, spec sections, or short anchors where useful. If a section has nothing noteworthy, include a brief sentence such as "No intentional deviations recorded."

## HTML Guidance

Use readable static HTML with simple embedded CSS when creating the file. Prefer semantic structure:

```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Implementation Notes</title>
  <style>
    body { font-family: system-ui, sans-serif; line-height: 1.5; margin: 2rem; max-width: 960px; }
    article { border-top: 1px solid #ddd; padding-top: 1rem; margin-top: 1.5rem; }
    h1, h2, h3 { line-height: 1.2; }
    code { background: #f5f5f5; padding: 0.1rem 0.25rem; border-radius: 3px; }
  </style>
</head>
<body>
  <h1>Implementation Notes</h1>
  <article>
    <h2>Task title or summary</h2>
    <p><time datetime="YYYY-MM-DD">YYYY-MM-DD</time></p>
    <h3>Summary</h3>
    <p>What changed and why this note exists.</p>
    <h3>Design decisions</h3>
    <ul><li>Decision with concise rationale and optional file/spec reference.</li></ul>
    <h3>Deviations</h3>
    <ul><li>No intentional deviations recorded.</li></ul>
    <h3>Tradeoffs</h3>
    <ul><li>Alternative considered and why the chosen approach won.</li></ul>
    <h3>Open questions</h3>
    <ul><li>Non-blocking question or "No open questions recorded."</li></ul>
  </article>
</body>
</html>
```

When appending to an existing file, match its established structure if it is clear. Otherwise append a compatible `<article>` before `</body>`.

## Checkpoint Discipline

At each significant checkpoint, decide whether the notes need an update:

- Did the implementation interpret ambiguous spec language?
- Did it intentionally depart from the spec?
- Was a meaningful alternative rejected?
- Is there a non-blocking question the user should revisit?

If none apply, record a short entry at the end saying the skill was active and no noteworthy decisions, deviations, tradeoffs, or open questions were found.
