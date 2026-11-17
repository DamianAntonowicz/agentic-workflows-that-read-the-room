---
name: update-github-info
description: Keep the GitHub Info website current from Mona's notes and official GitHub sources
on:
  schedule: daily
  workflow_dispatch:
permissions:
  contents: read
  copilot-requests: write
strict: true
engine:
  id: copilot
  copilot-sdk: true
network:
  allowed:
    - github.blog
    - github.com
tools:
  edit:
  web-fetch:
safe-outputs:
  create-pull-request:
    title-prefix: "[github-info] "
    draft: true
    allowed-files:
      - "site/content/github-info.md"
    excluded-files:
      - ".github/workflows/*.lock.yml"
    if-no-changes: "warn"
---

# Update GitHub Info

Update `site/content/github-info.md` for Mona using only the repository notes and the two official public sources below.

## Sources

1. Read and follow `notes/mona-notes.md`.
2. Fetch `https://github.blog/latest/`.
3. Fetch `https://github.blog/changelog/`.

## Task

- Reconcile the current file with the latest useful GitHub Blog and GitHub Changelog information.
- Preserve Mona's established editorial angle, practical tone, and source-attribution requirements.
- Update only `site/content/github-info.md`.
- Keep summaries short and practical.
- Mention the source URL or a clear source name whenever a change comes from the GitHub Blog or GitHub Changelog.
- Do not remove editorial context unless new source evidence makes it inaccurate.
- Do not add unsupported claims, speculative dates, or personal commentary.
- Do not include promotional or unrelated content.
- If there is no meaningful, verified update, do not change the file and report no visible changes.

## Pull request

Open a pull request for Mona to review after making a meaningful update.

- Explain which official sources informed the update.
- Include concise source links in the pull request.
- Keep the PR focused on `site/content/github-info.md`.
- Do not write directly to `main`.
- Do not compile this workflow or generate or modify a `.lock.yml` file.
