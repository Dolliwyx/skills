---
name: changelog
description: Create or update a changelog using Keep a Changelog. Use when asked to record notable changes, prepare a changelog for a release, or reconstruct release history.
---

# Changelog

Create or update `CHANGELOG.md` as a human-curated record based on [Keep a Changelog 2.0.0](https://keepachangelog.com/en/2.0.0/).

1. Find the project's existing changelog, release conventions, versioning scheme, tags, and repository remote. Respect the requested project or component scope and preserve existing history. If the change range or release details cannot be established reliably, ask rather than invent them.
2. Inspect the relevant diffs, release information, and current working changes as appropriate to the request. Identify every notable change for readers, including deprecations, removals, security fixes, and breaking changes. Treat commit messages as leads, not finished entries; combine related commits and omit internal noise. If creating a changelog without a requested history, start with `Unreleased` rather than implying past releases were covered.
3. Write concise entries describing the user-visible change and its reason where useful. Group them under `Added`, `Changed`, `Deprecated`, `Removed`, `Fixed`, or `Security`; omit empty categories. Put bug fixes under `Fixed`, intentional behavior changes under `Changed`, and vulnerabilities under `Security`, leading with the CVE when known. Mark breaking entries with `**Breaking:**`, identify the affected interface, and include a short upgrade hint or link to a migration guide. Give a planned removal version for deprecations when known.
4. Keep `Unreleased` first and releases newest first. Use `## [version] - YYYY-MM-DD` for dated releases and mark yanked releases with `[YANKED]`. For a requested release, move the relevant unreleased entries into the specified version and add a fresh `Unreleased` section. For projects without versions, use dated entries under `Unreleased`.
5. For a new file, start with `# Changelog`, a short statement that it records notable changes, a link to Keep a Changelog 2.0.0, and the project's actual versioning scheme if known. Add reference-style version links when the repository host and tags support reliable links: compare each release to its predecessor, the oldest to its tag, and `Unreleased` from the latest tag to `HEAD`. Update affected links on release. Do not guess URLs or tags.
6. Review the resulting file against the evidence: each entry is accurate, notable, correctly grouped, and not duplicated; existing releases remain intact; dates and links resolve to the intended versions. Flag uncertainties and ask the user to curate the draft before publication.
