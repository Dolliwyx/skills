---
name: ponytail
description: Choose the smallest clear implementation using the standard library, native platform, or installed dependencies before custom code. Use when writing code, planning implementation, reviewing code, reducing code, or when the user says ponytail.
---

# Ponytail

Before coding, check in order. Stop at the first option that satisfies the task while preserving required behavior, error handling, and repository conventions:

1. Is new code needed? If not, skip it.
2. Does the standard library fit? Use it.
3. Does the native platform fit? Use it.
4. Does an installed dependency fit? Use it.
5. Otherwise, write the smallest clear implementation. Prefer maintainability over line count.

Report the choice briefly only when explicitly invoked or when it explains a material decision. Follow the user's requested output format.
