# Project Research Summary

**Project:** Awesome Eurorack
**Domain:** Curated awesome-list for open source Eurorack modular synthesizer resources
**Researched:** 2026-04-19
**Confidence:** MEDIUM

## Executive Summary

Awesome Eurorack is a curated awesome-list -- a single-file Markdown project hosted on GitHub that catalogs open source Eurorack modular synthesizer resources. The awesome-list ecosystem is mature and highly opinionated: the sindresorhus/awesome spec dictates file structure, entry format, linting tools, and licensing (CC0-1.0). There is no application architecture to design; the "product" is a well-organized README.md. Experts build these by scaffolding the structure first, validating it against awesome-lint, then populating with manually vetted entries. The Eurorack domain adds a specific organizational challenge: entries must be categorized by module function (Oscillators, Filters, Sequencers) rather than by technology type, and each entry should carry inline type tags (HW/FW/SW) to preserve the hardware-firmware-software dimension.

The recommended approach is structure-first: establish the category taxonomy, lock down the entry format, pass awesome-lint with sample entries, then populate. The stack is minimal -- Markdown, awesome-lint, markdownlint-cli2, and GitHub Actions for CI. No build tools, no static site generators, no databases. The project's simplicity is its strength, but the awesome-list spec enforces many small rules (alphabetical ordering, description format, heading hierarchy) that are easy to violate and painful to fix retroactively across 100+ entries.

The primary risks are: (1) failing awesome-lint due to structural rules baked in early, (2) choosing a category taxonomy that fights how Eurorack users think, (3) scope drift into closed-source or non-Eurorack projects, and (4) publishing an empty scaffold that signals abandonment. All four risks are mitigated by getting the scaffold and seed entries right in Phase 1, running awesome-lint continuously, and defining explicit inclusion criteria before accepting any contributions.

## Key Findings

### Recommended Stack

The stack is intentionally minimal. This is a documentation project, not a software application.

**Core technologies:**
- **Markdown (GFM)**: Content format -- awesome-list convention, rendered natively by GitHub
- **awesome-lint**: Spec compliance linter -- the official and only tool for validating awesome-list structure
- **markdownlint-cli2**: Markdown style enforcement -- catches formatting issues awesome-lint does not cover
- **markdown-link-check**: Dead link detection -- essential for maintaining link integrity over time
- **GitHub Actions**: CI platform -- free for public repos, runs linters on PRs and scheduled link checks
- **CC0-1.0 License**: Required by the awesome-list specification, non-negotiable

No build tools, static site generators, databases, or backend services should be used. Pre-commit hooks should be avoided because they create friction for contributors.

### Expected Features

**Must have (table stakes):**
- Single README.md as canonical document with consistent entry format
- Table of Contents (auto-generated or manually maintained)
- Alphabetical ordering within sections
- CC0-1.0 LICENSE file
- Awesome badge linking to awesome.re
- Function-based categories matching Eurorack module taxonomy
- Descriptive entry text (one sentence per entry, ending with period)

**Should have (differentiators):**
- Inline type tags (HW/FW/SW) per entry -- critical for Eurorack domain where projects span hardware, firmware, and software
- Category descriptions explaining what each section covers
- Standards and Specifications section (Doepfer specs, power standards)
- Development tools section (KiCad libraries, panel generators)
- PCB/panel fabrication and component sourcing resources
- Beginner-friendly markers for well-documented, easy-to-build projects

**Defer (v2+):**
- GitHub stars and last-commit badges (require CI automation for maintenance)
- Per-entry license badges (useful but adds curation overhead)
- Module format details (HP width, SMD vs THT -- too much metadata)
- CONTRIBUTING.md and PR templates (explicitly deferred per PROJECT.md)
- Cross-references between categories (only meaningful once populated)

### Architecture Approach

The architecture is the README.md section hierarchy. Categories follow Eurorack signal flow: sound sources (Oscillators) through processing (Filters, VCAs) through modulation (LFOs, Sequencers) through effects to output, with infrastructure categories (MIDI, Power, Development Platforms) after signal-path categories, and Resources at the end. Maximum two levels of heading depth (Category and Subcategory). The entry format is `[Name](URL) \`TAG\` - Description.` with HW/FW/SW tags.

**Major components:**
1. **README.md** -- The entire curated list: header, TOC, categories, entries, resources, footer
2. **LICENSE** -- CC0-1.0 (required by awesome spec, required for registry inclusion)
3. **CI workflows (v2)** -- awesome-lint on PRs, markdown-link-check on weekly schedule
4. **CONTRIBUTING.md (v2)** -- Entry criteria, format guide, PR workflow

### Critical Pitfalls

1. **Failing awesome-lint on structural rules** -- Run awesome-lint from day one, before adding content. Small formatting rules (description periods, dash separators, no articles) are strictly enforced and painful to fix across many entries.
2. **Category taxonomy fights the domain** -- Use function-first categories (Oscillators, Filters, etc.), not technology-first (KiCad, Arduino). Cap at 8-12 top-level sections. Validate against how ModularGrid and forums organize modules.
3. **Scope drift into closed source** -- Define "open source" explicitly with concrete criteria: OSI/OSHWA-compatible license, source files available, buildable by third parties. Do this before any contributions.
4. **Empty scaffold syndrome** -- Do not publish with empty categories. Combine structure and seed entries (2-3 per category) into the same phase. An empty list signals abandonment and kills contributions.
5. **Link rot over time** -- Eurorack hardware projects have higher abandonment rates than software. Plan for quarterly link checks and scheduled CI validation.

## Implications for Roadmap

Based on research, suggested phase structure:

### Phase 1: Scaffold and Format Validation

**Rationale:** awesome-lint rules are strict and structural. Getting the skeleton right before adding content prevents costly reformatting later. All four research files converge on this as the critical first step.
**Delivers:** README.md with header (title, description, awesome badge), TOC, all category headings, entry format specification, and LICENSE file. Passes awesome-lint with zero entries.
**Addresses:** Awesome-list structural requirements (table stakes), category taxonomy, entry format spec, type tag design (HW/FW/SW), scope/inclusion criteria definition
**Avoids:** Pitfall 1 (awesome-lint failures baked into structure), Pitfall 2 (bad category taxonomy), Pitfall 3 (undefined scope), Pitfall 8 (over-engineered tags)

### Phase 2: Seed Content Population

**Rationale:** An empty scaffold is useless and signals abandonment. Seed entries validate the format in practice, set the quality bar for future contributors, and make the list immediately useful. FEATURES.md and PITFALLS.md both emphasize that structure and initial population should be treated as inseparable.
**Delivers:** 2-5 entries per major category using real open source Eurorack projects (Mutable Instruments, Ornament and Crime, Befaco, etc.). Populated Resources section with foundational references (Doepfer specs, community links). All entries pass awesome-lint.
**Addresses:** Per-entry metadata (table stakes), descriptive entry text, Standards/Specifications section, Resources sections
**Avoids:** Pitfall 5 (empty scaffold syndrome), Pitfall 7 (useless descriptions), Pitfall 10 (Eurorack scope ambiguity, resolved by example)

### Phase 3: CI and Linting Automation

**Rationale:** Once content exists, automated quality enforcement becomes valuable. Link checking is especially important for hardware projects where repos go dormant or get renamed.
**Delivers:** GitHub Actions workflows for awesome-lint (on PRs), markdownlint-cli2 (on PRs), and markdown-link-check (weekly schedule). markdownlint configuration file.
**Addresses:** Dead link detection (table stakes), format enforcement at scale
**Avoids:** Pitfall 1 (ongoing lint compliance), Pitfall 4 (link rot)

### Phase 4: Contribution Infrastructure

**Rationale:** Before publicizing the list or seeking external contributions, contribution guidelines and quality gates must exist. Without them, the first external PRs will introduce formatting inconsistencies and scope violations.
**Delivers:** CONTRIBUTING.md with entry criteria, format guide, and inclusion rules. PR template with quality checklist. Code of conduct.
**Addresses:** Contribution quality control, awesome registry requirements (needs CONTRIBUTING.md and code of conduct for submission)
**Avoids:** Pitfall 9 (no contribution barrier), Pitfall 6 (registry rejection for missing files)

### Phase 5: Registry Submission Preparation

**Rationale:** The awesome registry has specific requirements beyond content quality: 30+ days of repo history, meaningful star count, complete supporting files. This phase is about readiness, not content.
**Delivers:** Repo meets all awesome registry submission criteria. PR submitted to sindresorhus/awesome.
**Addresses:** Awesome registry inclusion
**Avoids:** Pitfall 6 (rejected for non-content reasons)

### Phase Ordering Rationale

- Phases 1-2 are tightly coupled and could be treated as a single phase. The split exists because format validation (lint-passing skeleton) should happen before committing to populating 15 categories.
- Phase 3 (CI) depends on content existing to lint and links existing to check. It must follow Phase 2.
- Phase 4 (contributions) depends on CI being in place to enforce standards on external PRs.
- Phase 5 (registry) has a hard prerequisite of 30+ days repo history and sufficient content/stars, making it naturally last.

### Research Flags

Phases likely needing deeper research during planning:
- **Phase 2:** Needs discovery research to identify the best open source Eurorack projects for seeding. The curator must verify repos still exist, have proper licenses, and are genuinely open source. This cannot be done from training data alone.
- **Phase 5:** The awesome registry submission checklist should be verified against the current spec before attempting submission.

Phases with standard patterns (skip research-phase):
- **Phase 1:** awesome-list scaffold structure is well-documented and stable. The template is clear.
- **Phase 3:** GitHub Actions workflow patterns for linting are standard and unlikely to have changed.
- **Phase 4:** CONTRIBUTING.md and PR template patterns are well-established across the awesome-list ecosystem.

## Confidence Assessment

| Area | Confidence | Notes |
|------|------------|-------|
| Stack | MEDIUM-HIGH | awesome-lint and GitHub Actions are stable and canonical. Exact npm version numbers need verification. |
| Features | MEDIUM-HIGH | Awesome-list conventions are mature and well-documented. Eurorack domain taxonomy is stable. |
| Architecture | MEDIUM-HIGH | Single-file Markdown architecture is extremely well-established. Entry format conventions are standard. |
| Pitfalls | MEDIUM | Pitfalls are based on common awesome-list failure modes and Eurorack ecosystem knowledge. Specific awesome-lint rule details may have evolved. |

**Overall confidence:** MEDIUM-HIGH

The awesome-list ecosystem is one of the most stable and well-documented project types. The Eurorack domain is mature with well-established functional taxonomy. The main uncertainty is whether specific awesome-lint rules or registry submission requirements have changed since the training data cutoff.

### Gaps to Address

- **Current awesome-lint rules**: Verify against the live sindresorhus/awesome repository before starting Phase 1. Rules may have been added or modified.
- **npm package versions**: All version numbers (awesome-lint, markdownlint-cli2, markdown-link-check) should be verified via `npm view [package] version` before use.
- **Node.js LTS version**: Node 20 LTS support ends April 2026. Node 22 LTS may be the current recommendation. Verify before setting up CI.
- **Open source Eurorack project discovery**: Phase 2 requires identifying real projects. Training data cannot confirm current repo status (archived, renamed, deleted). Live research needed.
- **Awesome registry submission requirements**: The PR template and minimum requirements (stars, repo age, content volume) should be checked before Phase 5.

## Sources

### Primary (HIGH confidence)
- Eurorack functional taxonomy (Doepfer A-100 standard, modular synthesis conventions) -- stable domain knowledge
- Awesome-list structural conventions (sindresorhus/awesome guidelines) -- mature ecosystem, stable since 2014

### Secondary (MEDIUM confidence)
- awesome-lint tool behavior and rules -- based on training data, specific rules may have updated
- npm package recommendations (markdownlint-cli2, markdown-link-check) -- version numbers unverified
- GitHub Actions workflow patterns -- standard patterns, unlikely to have changed significantly
- Open source hardware licensing patterns (CERN-OHL, MIT, GPL) -- well-documented standards

### Tertiary (LOW confidence)
- Awesome registry submission thresholds (star count, repo age) -- community consensus, not formally specified
- Relative popularity of link-checking tools (markdown-link-check vs lychee) -- may have shifted

---
*Research completed: 2026-04-19*
*Ready for roadmap: yes*
