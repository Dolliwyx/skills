# Google developer documentation review checklist

Use only the sections that apply. For edge cases, follow the linked live guide rather than extending this checklist from memory.

## Structure and task flow

- State the reader's goal, outcome, or key point early.
- Use descriptive, unique headings in sentence case and a logical heading hierarchy.
- Put prerequisites and required context before the task that needs them.
- Put conditions, locations, and goals before instructions.
- Keep paragraphs short, front-load distinguishing information, and use lists to improve scanning.
- Use numbered lists for sequences, bullets for unordered items, and description lists for paired terms and explanations.
- Prefer one recommended path. Move alternatives into separate sections only when readers need them.

References: [Headings and titles](https://developers.google.com/style/headings), [Paragraphs](https://developers.google.com/style/paragraph-structure), [Lists](https://developers.google.com/style/lists), and [Procedures](https://developers.google.com/style/procedures).

## Voice and language

- Write in a conversational, friendly, respectful tone without slang or forced humor.
- Address the reader as _you_. Use active voice, present tense, and standard American English.
- Prefer short, direct sentences and familiar words. Define unfamiliar abbreviations on first use.
- Use consistent terms for the same concept. Check uncertain usage in the [word list](https://developers.google.com/style/word-list).
- Use inclusive, literal language that works across cultures and translates cleanly.
- Remove filler, jargon, clichés, culture-specific references, excessive claims, and unsupported promises.
- Replace phrases such as _please note_, _at this time_, _let's_, _simply_, _easy_, and _quickly_ with direct information.
- Use exclamation marks sparingly.

References: [Voice and tone](https://developers.google.com/style/tone), [Active voice](https://developers.google.com/style/voice), [Second person](https://developers.google.com/style/person), [Present tense](https://developers.google.com/style/tense), [Global audience](https://developers.google.com/style/translation), and [Inclusive documentation](https://developers.google.com/style/inclusive-documentation).

## Procedures

- Introduce a multi-step procedure only when the introduction adds context.
- Start each step with an imperative verb and keep one meaningful action per step.
- Use a bullet for a single-step procedure and numbers for a sequence.
- Write `Optional:` at the start of an optional step.
- State where the action occurs before the action; state a goal before the action that achieves it.
- Put a result or justification after the action.
- Keep the path uninterrupted and include only the steps needed to complete the task.

Reference: [Procedures](https://developers.google.com/style/procedures).

## Links and formatting

- Write descriptive link text that makes sense out of context; avoid _click here_ and bare URLs when a label is useful.
- Use sentence case for titles and headings and the serial comma in a list of three or more items.
- Format UI labels in **bold**.
- Format filenames, code elements, commands, user input, and placeholders in `code font`; use fenced blocks for samples.
- Use italics sparingly for introduced terms, words as words, or necessary emphasis.
- Reserve underlining for links. Use _and_ instead of `&` except when reproducing a name or UI label.
- Use unambiguous dates.

References: [Cross-references](https://developers.google.com/style/cross-references), [Text-formatting summary](https://developers.google.com/style/text-formatting), [Capitalization](https://developers.google.com/style/capitalization), and [Dates and times](https://developers.google.com/style/dates-times).

## Code, commands, and reference material

- Keep examples minimal, relevant, internally consistent, and safe to copy.
- Prefer runnable command examples with only the arguments needed for the documented task.
- Explain placeholders immediately after the sample and use consistent placeholder values.
- Link to complete command or API reference instead of duplicating every option in task documentation.
- Show output only when readers need it to proceed or verify success; distinguish input from output.
- Verify code, commands, identifiers, links, and stated results when the environment permits.

References: [Code samples](https://developers.google.com/style/code-samples), [Code in text](https://developers.google.com/style/code-in-text), [Command-line syntax](https://developers.google.com/style/code-syntax), [Placeholders](https://developers.google.com/style/placeholders), and [API reference comments](https://developers.google.com/style/api-reference-comments).

## Accessibility and global readability

- Use semantic headings, lists, tables, and HTML elements.
- Provide meaningful alt text for informative images and empty alt text for decorative images. Include essential information as text.
- Make link text meaningful when read alone.
- Do not rely only on color, position, size, icons, images, sound, or punctuation to convey meaning.
- Refer to controls by their visible or accessible label, not by location or appearance.
- Avoid directional references such as _above_, _below_, or _on the right_; use _preceding_, _following_, or a named section.
- Introduce tables and interactive elements before they appear. Use tables only when rows and columns clarify relationships.
- Keep sentences concise; aim for fewer than 26 words when practical.

References: [Accessible documentation](https://developers.google.com/style/accessibility), [Images](https://developers.google.com/style/images), and [Tables](https://developers.google.com/style/tables).

## Final checks

- Project-specific guidance takes precedence.
- The document is technically accurate and uses one term per concept.
- Every heading and paragraph contributes to the reader's task.
- Procedures have a clear starting state and verifiable outcome.
- Links, examples, and cross-references are valid where they can be checked.
- Any departure from the guide improves clarity for this audience and remains consistent.

This checklist summarizes guidance from the [Google developer documentation style guide](https://developers.google.com/style), which is licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). It is not an official Google publication.
