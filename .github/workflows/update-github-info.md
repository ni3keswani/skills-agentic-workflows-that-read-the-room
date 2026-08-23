---
name: update-github-info
description: Draft concise GitHub Info website updates from official GitHub sources.
on:
  schedule:
    - cron: daily
  workflow_dispatch:

permissions: read-all

network:
  allowed:
    - github.blog
    - github.com
    - awesome-copilot.github.com

tools:
  edit:
  web-fetch:
  github:
    toolsets:
      - repos

safe-outputs:
  create-pull-request:
    title-prefix: "[mona] "
    draft: true
    max: 1
---

# Update GitHub Info

Read `notes/mona-notes.md` before drafting any changes.

Use `web-fetch` to read:

- https://github.blog/latest/
- https://github.blog/changelog/
- https://awesome-copilot.github.com/workflows/

Also include Awesome Copilot workflows as an official source:

- https://awesome-copilot.github.com/workflows/

Use the GitHub repository API read tools from the `repos` toolset to read repository guidance and reference files. Do not use terminal, CLI, or sandboxed commands for repository reads.

Update `site/content/github-info.md` with concise, practical updates that help developers learn GitHub faster. Attribute information from the GitHub Blog or GitHub Changelog to its source, and preserve the existing editorial structure.

Open a pull request for Mona to review. Do not write directly to `main`; propose the change through the `create-pull-request` safe output.
