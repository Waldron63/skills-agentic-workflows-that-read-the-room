---
name: update-github-info
on:
  schedule:
    - cron: "0 9 * * *"
  workflow_dispatch:
permissions:
  contents: read
engine: 
    id: copilot
    model: gpt-5.4
tools:
  github:
    toolsets: [repos]
  web-fetch: {}
  edit: {}
network:
  allowed:
    - github.blog
    - github.com
    - awesome-copilot.github.com
safe-outputs:
  create-pull-request:
    title-prefix: "[mona] "
    draft: true
---

# Update GitHub Info

Keep Mona's GitHub Info content current and practical for developers.

1. Read `notes/mona-notes.md` before doing any research or edits.
2. Use the web-fetch tool to read these official public sources:
   - https://github.blog/latest/
   - https://github.blog/changelog/
  - https://awesome-copilot.github.com/workflows/
3. Use GitHub repository API tools to read repository guidance and reference files, including `site/content/github-info.md`. Do not use terminal, the GitHub CLI, or sandboxed shell commands to read repository files.
4. Select relevant recent GitHub Blog, Changelog, or Awesome Copilot workflow updates, keeping summaries short and practical. Mention the official source for every update you add.
5. Update only `site/content/github-info.md` with accurate, concise content that fits Mona's editorial angle. Do not modify generated files or unrelated content.
6. Review the resulting changes for accuracy, source links, and consistency with the notes.
7. Use the `create_pull_request` safe output to open a pull request containing the proposed update for Mona to review. Do not push directly to the default branch.