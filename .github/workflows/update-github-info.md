---
name: update-github-info
description: Draft website updates for Mona's GitHub Info site from official GitHub sources.
on:
  workflow_dispatch:
  schedule:
    - cron: '17 9 * * *'
safe-outputs:
  create-pull-request:
    title-prefix: "[mona] "
    draft: true
    fallback-as-issue: false
tools:
  edit:
  web-fetch:
network:
  allowed:
    - github.com
    - github.blog
    - awesome-copilot.github.com
engine:
  id: copilot
  version: "1.0.91"
  copilot-sdk: true
---

# Update Mona's GitHub Info website

Read `notes/mona-notes.md` before making changes.

Use these sources:
- `notes/mona-notes.md`
- GitHub Blog: https://github.blog/latest/
- GitHub Changelog: https://github.blog/changelog/
- Awesome Copilot workflows: https://awesome-copilot.github.com/workflows/

Use `web-fetch` to read https://awesome-copilot.github.com/workflows/ before writing updates.

Update `site/content/github-info.md` with concise, practical updates for readers. Include source context when content comes from the GitHub Blog or GitHub Changelog.

Read external public guidance with `web-fetch`. Read repository guidance or reference files with GitHub repository API tools instead of terminal, CLI, or sandboxed commands.

Open a pull request for Mona to review. Use a pull request title that mentions Mona or GitHub Info. Do not write directly to `main`; rely on `safe-outputs` with `create-pull-request`.