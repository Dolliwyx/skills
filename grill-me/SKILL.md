---
name: grill-me
description: Interview the user relentlessly about a plan or design until reaching shared understanding, resolving each branch of the decision tree. Use when user wants to stress-test a plan, get grilled on their design, or mentions "grill me".
---

Interview me relentlessly about every aspect of this plan until we reach a shared understanding. Walk down each branch of the design tree, resolving dependencies between decisions one-by-one. For each question, provide your recommended answer.

Use the `request_user_input` tool for questions whenever it is available. Ask multiple questions at once when the next decisions are independent enough to answer together; otherwise ask one question at a time. Keep each question short, include a recommended option when choices are useful, and continue grilling based on the user's answers until the decision tree is resolved.

If `request_user_input` is unavailable, ask questions in normal chat. In that case, ask multiple questions at once when possible; otherwise ask one at a time.

If a question can be answered by exploring the codebase, explore the codebase instead.
