# Technology Stack

**Project:** Awesome Eurorack (open source Eurorack awesome-list)
**Researched:** 2026-04-19

**Note on sources:** WebSearch, WebFetch, and Bash were unavailable during this research session. All recommendations are based on training data (cutoff May 2025). The awesome-list ecosystem is mature and stable, so recommendations are likely current, but exact version numbers should be verified before use. Confidence levels reflect this limitation.

## Recommended Stack

### Core Format

| Technology | Version | Purpose | Why |
|------------|---------|---------|-----|
| Markdown (CommonMark/GFM) | N/A | List content format | Awesome-list convention -- single README.md. GitHub Flavored Markdown is the standard because GitHub renders it natively with full feature support (tables, badges, TOC anchors). |
| Git + GitHub | N/A | Hosting, collaboration, CI | Awesome-lists live on GitHub by convention. The entire awesome ecosystem (registry, lint tools, discovery) assumes GitHub hosting. |

### Linting and Validation

| Technology | Version | Purpose | Why |
|------------|---------|---------|-----|
| awesome-lint | ^1.0.0 | Awesome-list spec compliance | **The** official linter from sindresorhus/awesome. Required for inclusion in the awesome registry. Checks list structure, formatting rules, link formatting, alphabetical ordering, badge presence, and more. Use this -- no alternatives exist. |
| markdownlint-cli2 | ^0.14.0 | General Markdown style enforcement | Catches Markdown formatting issues awesome-lint does not (trailing spaces, consistent heading style, line length). Prefer markdownlint-cli2 over markdownlint-cli -- it is the actively maintained successor with better config file support (.markdownlint-cli2.jsonc). |
| markdown-link-check | ^3.12.0 | Dead link detection | Validates all URLs in the README still resolve. Essential for a curated list -- dead links erode trust. Run on schedule (weekly) not just on PR, since links rot over time. |

### CI / GitHub Actions

| Technology | Version | Purpose | Why |
|------------|---------|---------|-----|
| GitHub Actions | N/A | CI platform | Free for public repos. Native to GitHub. Every major awesome-list uses it. |
| actions/checkout | v4 | Repo checkout in CI | Standard action, required by all workflows. |
| actions/setup-node | v4 | Node.js environment for linters | awesome-lint and markdownlint-cli2 require Node.js. Use Node 20 LTS. |

### Automation (deferred per PROJECT.md but documented for v2)

| Technology | Version | Purpose | Why |
|------------|---------|---------|-----|
| awesome-bot / custom script | N/A | Link validation on schedule | Scheduled GitHub Action (cron) to catch link rot weekly. markdown-link-check wrapped in a workflow. |
| TOC generator (markdown-toc or doctoc) | latest | Auto-generate Table of Contents | doctoc (~1.0) or markdown-toc are both viable. doctoc is simpler for awesome-lists: `doctoc README.md --github`. Inserts/updates TOC between markers. Run as pre-commit or CI check. |

### Repository Scaffolding

| File | Purpose | Why |
|------|---------|-----|
| README.md | The list itself | Awesome-list convention: everything in one file. |
| LICENSE | Legal clarity | CC0-1.0 is the awesome-list standard license. Required by the awesome spec. |
| .github/workflows/lint.yml | CI workflow | Runs awesome-lint + markdownlint on PRs and pushes. |
| .github/workflows/links.yml | Scheduled link checking | Weekly cron job running markdown-link-check. |
| .markdownlint-cli2.jsonc | markdownlint config | Disable rules that conflict with awesome-list conventions (e.g., MD013 line length, MD033 inline HTML for badges). |
| .github/pull_request_template.md | PR quality | Checklist for contributors (link works, description present, correct category). |
| CONTRIBUTING.md | Contribution guidelines | Deferred to v2 per PROJECT.md, but required for awesome registry submission. |
| code-of-conduct.md | Community standards | Required by awesome spec for registry inclusion. Contributor Covenant is the standard choice. |

## Configuration Details

### awesome-lint
No config file needed -- it reads the README.md directly and enforces the awesome spec. Run via:
```bash
npx awesome-lint
```

Key rules it enforces:
- List items must have descriptions
- Items must link to HTTPS URLs
- No trailing slashes on URLs
- Alphabetical ordering within sections (configurable)
- Required sections: license badge, TOC
- Proper heading hierarchy

### markdownlint-cli2 Configuration (.markdownlint-cli2.jsonc)
```jsonc
{
  "config": {
    "MD013": false,       // Line length -- awesome-list entries are naturally long
    "MD033": false,       // Inline HTML -- needed for badges/shields
    "MD034": false,       // Bare URLs -- sometimes used in resource sections
    "MD041": false        // First line heading -- awesome-lint handles this
  }
}
```

### GitHub Actions Workflow (lint.yml)
```yaml
name: Lint
on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  lint:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: 20
      - run: npx awesome-lint
      - run: npx markdownlint-cli2 "README.md"
```

### GitHub Actions Workflow (links.yml)
```yaml
name: Check Links
on:
  schedule:
    - cron: '0 0 * * 0'  # Weekly on Sunday
  workflow_dispatch:       # Manual trigger

jobs:
  check-links:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - run: npx markdown-link-check README.md --config .markdown-link-check.json
```

## Alternatives Considered

| Category | Recommended | Alternative | Why Not |
|----------|-------------|-------------|---------|
| Markdown linter | markdownlint-cli2 | markdownlint-cli | markdownlint-cli is the older CLI. markdownlint-cli2 has better config, glob support, and is the actively maintained version. |
| Markdown linter | markdownlint-cli2 | remark-lint | remark-lint is powerful but heavier (requires remark ecosystem plugins). Overkill for an awesome-list where awesome-lint handles the spec-specific rules. |
| TOC generator | doctoc | markdown-toc | Both work. doctoc is slightly more popular in the awesome-list ecosystem and has simpler CLI usage. Either is fine. |
| Link checker | markdown-link-check | lychee | lychee (Rust) is faster but requires separate installation. markdown-link-check runs via npx with zero install, which is simpler for CI. For a single README.md, speed is irrelevant. |
| Link checker | markdown-link-check | awesome-bot | awesome-bot (Ruby) was the original tool but is less maintained. markdown-link-check is Node-based (consistent with the rest of the stack) and more actively maintained. |
| License | CC0-1.0 | MIT / Apache-2.0 | Awesome-list convention is CC0. The spec requires it. A curated list is not code -- public domain dedication is appropriate and expected. |
| CI platform | GitHub Actions | CircleCI / Travis CI | GitHub Actions is free, native, and what every awesome-list uses. No reason to add external CI. |
| Static site | None | mkdocs / docusaurus | Explicitly out of scope per PROJECT.md. Awesome-lists are GitHub-rendered Markdown. Adding a site generator adds complexity with no value for a curated list. |
| Badge service | Shields.io | Badgen | Shields.io is the de facto standard. Larger variety of badges, better GitHub integration, widely recognized format. |

## What NOT to Use

| Tool/Approach | Why Not |
|---------------|---------|
| Static site generators (Jekyll, Hugo, etc.) | Out of scope. Awesome-lists are pure Markdown. A site adds maintenance burden and violates convention. |
| Database or JSON data files | Over-engineering. The content IS the Markdown. Generating README from data files adds complexity with no benefit at this scale. |
| Custom build scripts | Awesome-lists should be hand-editable Markdown. Build steps create friction for contributors. |
| Pre-commit hooks (husky, lint-staged) | Contributors should not need Node.js locally. CI catches issues. Pre-commit hooks discourage contributions. |
| Monorepo tools (nx, turborepo) | Single file project. Absurd overhead. |
| Any backend or API | This is a static Markdown file. No server needed. |

## Installation

```bash
# No install needed for CI (uses npx)
# For local development/testing:

# Validate awesome-list spec compliance
npx awesome-lint

# Check Markdown style
npx markdownlint-cli2 "README.md"

# Check for dead links
npx markdown-link-check README.md

# Generate/update TOC
npx doctoc README.md --github
```

## Confidence Assessment

| Recommendation | Confidence | Notes |
|----------------|------------|-------|
| awesome-lint as primary linter | HIGH | This is the official tool. No alternatives. Stable for years. |
| markdownlint-cli2 over markdownlint-cli | MEDIUM | Actively maintained successor, but verify current version -- could not check npm registry. |
| markdown-link-check | MEDIUM | Standard tool, but verify version number. lychee is gaining traction and may have surpassed it by 2026. |
| GitHub Actions workflow patterns | HIGH | Standard patterns, unlikely to have changed. actions/checkout@v4 and actions/setup-node@v4 are current. |
| CC0-1.0 license | HIGH | Awesome spec requirement. Will not change. |
| doctoc for TOC | MEDIUM | Works well but verify it is still maintained. markdown-toc is equally valid. |
| Node 20 LTS | MEDIUM | Node 20 LTS is supported through April 2026. Node 22 LTS may be preferred by now -- verify. |
| Shields.io for badges | HIGH | De facto standard, massive adoption, unlikely to be displaced. |

## Sources

- Training data knowledge of sindresorhus/awesome ecosystem (cutoff May 2025)
- Unable to verify with live sources (WebSearch, WebFetch, Bash all unavailable)
- All version numbers should be verified before use via `npm view [package] version`
