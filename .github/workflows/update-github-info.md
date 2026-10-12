---
name: update-github-info
description: Refresh Mona's GitHub Info content with recent official GitHub Blog and Changelog updates.
on:
  schedule: daily
  workflow_dispatch:

permissions:
  contents: read

engine:
  id: copilot
  copilot-sdk: true

tools:
  edit:
  web-fetch:

network:
  allowed:
    - copilot
    - github.blog
    - github.com

safe-outputs:
  create-pull-request:
---

# Update Mona's GitHub Info

Read `notes/mona-notes.md` and `site/content/github-info.md` before drafting changes.

Use `web-fetch` to read both official sources:

- https://github.blog/latest/
- https://github.blog/changelog/

Choose up to three recent, developer-relevant updates that fit Mona's practical editorial angle. Verify each title, date, and details against its source page. Update `site/content/github-info.md` in its existing style, preserving its stable editorial guidance and avoiding duplicate or stale update entries. Keep summaries short and practical, and include a direct source link for every update. Do not invent details or add an item if the source does not substantiate it.

Open one pull request for Mona to review the proposed content changes. The pull request should briefly summarize the updates and identify the GitHub Blog or Changelog sources. If there are no substantiated updates or no meaningful file changes, do not create an empty pull request.