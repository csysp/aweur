<!-- GSD:project-start source:PROJECT.md -->
## Project

**Awesome Eurorack**

A curated awesome-list of open source Eurorack modular synthesizer resources — hardware designs, firmware, software tools, and libraries hosted on GitHub, plus tutorials, communities, vendor docs, and specifications. Organized by module function (Oscillators, Filters, Sequencers, etc.) with type tags (HW/FW/SW) on each entry, following the official awesome-list specification.

**Core Value:** A single, well-organized, community-maintained reference that makes it easy to discover open source Eurorack projects by what they do.

### Constraints

- **Format**: Single README.md as the canonical document — awesome-list convention
- **Spec compliance**: Must pass awesome-lint for potential inclusion in the awesome registry
- **Content**: GitHub-hosted repos as primary entries, with a separate resources section for non-repo links
<!-- GSD:project-end -->

<!-- GSD:stack-start source:research/STACK.md -->
## Technology Stack

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
- List items must have descriptions
- Items must link to HTTPS URLs
- No trailing slashes on URLs
- Alphabetical ordering within sections (configurable)
- Required sections: license badge, TOC
- Proper heading hierarchy
### markdownlint-cli2 Configuration (.markdownlint-cli2.jsonc)
### GitHub Actions Workflow (lint.yml)
### GitHub Actions Workflow (links.yml)
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
# No install needed for CI (uses npx)
# For local development/testing:
# Validate awesome-list spec compliance
# Check Markdown style
# Check for dead links
# Generate/update TOC
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
<!-- GSD:stack-end -->

<!-- GSD:conventions-start source:CONVENTIONS.md -->
## Conventions

Conventions not yet established. Will populate as patterns emerge during development.
<!-- GSD:conventions-end -->

<!-- GSD:architecture-start source:ARCHITECTURE.md -->
## Architecture

Architecture not yet mapped. Follow existing patterns found in the codebase.
<!-- GSD:architecture-end -->

<!-- GSD:skills-start source:skills/ -->
## Project Skills

No project skills found. Add skills to any of: `.claude/skills/`, `.agents/skills/`, `.cursor/skills/`, or `.github/skills/` with a `SKILL.md` index file.
<!-- GSD:skills-end -->

<!-- GSD:workflow-start source:GSD defaults -->
## GSD Workflow Enforcement

Before using Edit, Write, or other file-changing tools, start work through a GSD command so planning artifacts and execution context stay in sync.

Use these entry points:
- `/gsd-quick` for small fixes, doc updates, and ad-hoc tasks
- `/gsd-debug` for investigation and bug fixing
- `/gsd-execute-phase` for planned phase work

Do not make direct repo edits outside a GSD workflow unless the user explicitly asks to bypass it.
<!-- GSD:workflow-end -->



<!-- GSD:profile-start -->
## Developer Profile

> Profile not yet configured. Run `/gsd-profile-user` to generate your developer profile.
> This section is managed by `generate-claude-profile` -- do not edit manually.
<!-- GSD:profile-end -->
