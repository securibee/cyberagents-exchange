---
name: "TEST - Nomination Flow Check (DO NOT MERGE)"
author: "securibee"
github_url: "https://github.com/securibee/monologue-to-obsidian"
description: "Test listing used to verify the prefilled cross-fork pull request flow. Not a real submission."
license: "MIT"
tier: "contributed"
tags: ["test", "internal", "flow-verification"]
integrations: ["Anthropic"]
date_added: 2026-08-26
contribution_agreement_date: 2026-08-26T15:00:00Z
visibility: example
works_with_tenable_hexa_mcp: false
compatible_platforms: ["Claude Code"]
invocation: "/flow-test"
---

> **This is a test listing. Do not merge it and do not review it as a submission.**
> It exists only to verify the mechanics of a proposed submission flow, and it is marked
> `visibility: example` so it never appears in browse, the leaderboard, or the home page
> even if it is merged by accident. Close the pull request and delete the branch once the
> flow check is recorded.

## What it does

Nothing. This file is dummy data for a mechanism test.

The test asks one question: can a GitHub account with no write access to
`tenable/cyberagents-exchange` open a pull request whose head branch lives in a *different*
account's fork, using only GitHub's documented compare query parameters
(`quick_pull`, `title`, `body`, `template`)? If it can, a maintainer can draft a complete
listing on an author's behalf and reduce that author's entire contribution to clicking one
link, checking the Contribution Agreement box, and pressing "Create pull request".

The frontmatter above is real in the sense that it passes `validator.py` schema validation
for the `skills/` directory - every required field is present and every controlled-vocabulary
value is legal. That matters, because the point is to watch the flow behave exactly as it
would for a genuine nomination, including a green CI check.

## How it works

The drafting maintainer pushes this file to a branch in their own fork of the content
repository, then sends the stand-in author a compare URL of the form:

```
https://github.com/tenable/cyberagents-exchange/compare/main...<maintainer>:<branch>?quick_pull=1&title=...&body=...
```

The author opens it while signed in to their own account. Everything after that is
observation: whether the page renders, whether the title and body arrive prefilled, whether
the "Create pull request" button is enabled for an account that cannot push to the base
repository, and whether the resulting pull request is attributed to the author who clicked
rather than the maintainer who wrote the commit.

The linked `github_url` points at a real, public, MIT-licensed repository owned by the same
account named in `author`, so the metadata is internally consistent. It is not a Claude Code
skill, so this listing would correctly fail the human congruence review in Phase 3 of the
contributing checklist - which is the right outcome for a file that must never be merged.
