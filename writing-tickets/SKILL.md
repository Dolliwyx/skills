---
name: writing-tickets
description: Draft or refine bug reports, feature suggestions, and chore or refactor tickets. Use when asked to write or improve a Jira ticket, GitHub issue, or similar work item. Publish only after confirming the draft and destination.
---

# Writing tickets

Turn notes, a conversation, or an existing ticket into a concise, self-contained title and body. Scale detail to the work: a small chore may need only a paragraph and a completion condition.

## 1. Ground the ticket

Identify the intended work, ticket type, and reader from the request. Follow applicable project templates and terminology. For an existing ticket, preserve relevant facts and scope unless the user asks to change them.

Use supplied evidence first. Read relevant code, linked context, or tracker records when a missing fact could change the draft. Keep investigation proportional to the ticket; drafting does not authorize implementation or state-changing experiments.

Ask when a missing answer changes the requested behavior, scope, or destination. Otherwise, keep useful unknowns explicit. Separate observed facts, reported behavior, hypotheses, and proposed solutions. Preserve tentative suggestions as suggestions. Use only supported impact, reproduction claims, priorities, estimates, owners, and deadlines. Remove secrets and unnecessary personal data from quoted evidence.

This step is complete when the problem or intended change is clear enough to draft without inventing requirements. An intake ticket can be useful while its cause or solution remains unknown.

## 2. Write the handoff

Read the prose guidance in the installed `technical-writing` skill. Read the visual guidance in the installed `show-me` skill when a visual would help. Locate these skills through the harness's skill inventory or installed skill directories. Use their guidance as reference, not as a request to execute their unrelated workflows. If a reference is unavailable, disclose that briefly outside the ticket and apply the baseline below.

**Prose:** use plain words, active voice, precise code and UI names, and clear conditions. Cut filler. Keep terminology consistent and each sentence unambiguous. Apply sentence-level guidance rather than forcing the ticket into one Diátaxis mode.

Write a specific title that names the problem or intended change. In the body, lead with what matters and why. Include the following content when relevant, using only the headings the work needs:

| Type | Useful content |
| --- | --- |
| Bug | Observed and expected behavior, impact, reproduction steps or available evidence, relevant environment, and an observable correction. Label untested reproduction steps and suspected causes. |
| Feature suggestion | User problem, intended benefit, proposed behavior, scope boundaries, and observable success. Keep unresolved product decisions visible. |
| Chore or refactor | Current maintenance cost or risk, intended change, behavior that must stay unchanged, and how to verify the result. |

Make acceptance criteria observable outcomes, not a speculative implementation checklist. Include them when the expected outcome is sufficiently defined. For exploratory work, state what question the investigation must answer or what finding it must deliver. Add implementation notes only for real constraints or clearly labeled proposals. Link supporting detail instead of pasting investigation logs.

**Visuals:** choose the smallest view that explains something the prose leaves hard to follow:

- Before-and-after sketches for behavior changes.
- Call trees or flows for interactions and ordering.
- Shallow file or component trees for responsibility changes.
- Pseudocode for rules or branching logic.

Put the visual beside the text it supports. Prefer fenced text or `diff` for portability. Use Mermaid only when the destination supports it. Label proposed shapes as proposed; show current behavior only when supported by evidence. Create richer artifacts only when requested, and publish attachments only with approval.

This step is complete when a reader can identify the problem or change, its boundaries, remaining unknowns, and how completion would be recognized. Omit empty sections and details that do not help that handoff.

## 3. Review and return the draft

Check the title and body against the source material. Confirm that the draft preserves uncertainty, contains no unsupported promises or metadata, and uses a visual only when it adds clarity. Keep independent work items separate; propose a split when one ticket would hide distinct outcomes rather than silently expanding the request.

Return the copy-ready title and body. Keep clarification questions, reference limitations, and publication discussion outside the ticket. For a draft-only request, stop here.

## 4. Confirm before publishing

For a creation or update request, show the final draft and ask for approval of both the content and destination before any remote write. An initial request to create a ticket is not approval of a draft the user has not seen. Approval of a specific displayed draft and destination satisfies this gate; ask again if either materially changes.

Resolve the tracker, project or repository, and target issue for an update. Use available authorized tracker tools; inspect their supported operations rather than embedding assumptions about Jira or GitHub commands. Apply only approved changes and preserve unrelated fields. Do not infer labels, assignments, scheduling, or workflow transitions from approval of the text.

Verify the saved title, body, and destination, then return the actual ticket URL or identifier. If publication or verification fails, retain the draft and report the blocker and any known remote change. Inspect the destination before retrying an uncertain creation so a retry does not create a duplicate. Never claim publication without a confirmed result.
