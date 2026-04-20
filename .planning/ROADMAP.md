# Roadmap: Awesome Eurorack

## Overview

This roadmap delivers a curated awesome-list of open source Eurorack modular synthesizer resources. The journey starts with establishing the README scaffold, lint compliance, and entry format standards, then populates signal-path module categories with seed entries, adds infrastructure categories and resource sections, and finishes with a quality validation pass across all content. The result is a lint-passing, well-organized, immediately useful awesome-list ready for community contributions.

## Phases

**Phase Numbering:**
- Integer phases (1, 2, 3): Planned milestone work
- Decimal phases (2.1, 2.2): Urgent insertions (marked with INSERTED)

Decimal phases appear between their surrounding integers in numeric order.

- [ ] **Phase 1: Scaffold and Standards** - README skeleton, LICENSE, TOC, entry format, lint compliance, and inclusion criteria
- [ ] **Phase 2: Signal Path Categories** - Core audio module categories (Oscillators through Effects) with 2-5 seed entries each
- [ ] **Phase 3: Infrastructure and Resources** - Utility, interface, and power categories plus development tools, specs, tutorials, and community sections
- [ ] **Phase 4: Content Quality and Final Polish** - Link verification, description polish, and full lint validation across all entries

## Phase Details

### Phase 1: Scaffold and Standards
**Goal**: Users can view a structurally complete, lint-passing README with clear organization and defined entry format, ready to receive curated entries
**Depends on**: Nothing (first phase)
**Requirements**: STRC-01, STRC-02, STRC-03, STRC-04, STRC-05, STRC-06, STRC-07, QUAL-03
**Success Criteria** (what must be TRUE):
  1. README.md passes awesome-lint with zero errors
  2. Table of Contents links to every category section and navigates correctly
  3. LICENSE file contains CC0-1.0 text in the repository root
  4. Entry format (`[Name](url) \`TAG\` - Description.`) is documented and demonstrated with at least one example entry
  5. Inclusion criteria section clearly defines what qualifies as "open source" and "Eurorack"
**Plans**: 2 plans

Plans:
- [ ] 01-01-PLAN.md — README scaffold: minimal lint validation (Assumption A1), full 14-section README with doctoc TOC, Awesome badge, intro, and example entry
- [ ] 01-02-PLAN.md — License and quality gate: CC0-1.0 LICENSE file, markdownlint config, inclusion criteria prose, full two-linter pass

### Phase 2: Signal Path Categories
**Goal**: Users can browse core audio module categories and discover real open source Eurorack projects organized by function
**Depends on**: Phase 1
**Requirements**: MCAT-01, MCAT-02, MCAT-03, MCAT-04, MCAT-05, MCAT-06, MCAT-07
**Success Criteria** (what must be TRUE):
  1. Each of the 7 signal-path categories (Oscillators, Filters, VCAs, Envelopes, Sequencers, Modulation, Effects) contains 2-5 real open source Eurorack project entries
  2. Every entry has a working URL, correct HW/FW/SW type tag, and description ending with a period
  3. Entries within each category are alphabetically ordered
  4. README.md continues to pass awesome-lint after all entries are added
**Plans**: TBD

### Phase 3: Infrastructure and Resources
**Goal**: Users can find utility modules, digital interfaces, power solutions, development tools, standards documentation, learning materials, and community links
**Depends on**: Phase 2
**Requirements**: MCAT-08, MCAT-09, MCAT-10, RSRC-01, RSRC-02, RSRC-03, RSRC-04
**Success Criteria** (what must be TRUE):
  1. Utilities, MIDI/USB/Digital Interfaces, and Power Supplies/Cases categories each contain 2-5 seed entries with correct format and type tags
  2. Development Tools and Libraries section links to real tools (KiCad libraries, panel generators, etc.)
  3. Standards and Specifications section includes foundational references (Doepfer A-100 spec, power standards)
  4. Learning Resources and Communities sections each contain relevant, accessible links
  5. README.md continues to pass awesome-lint after all additions
**Plans**: TBD

### Phase 4: Content Quality and Final Polish
**Goal**: Every entry in the list is verified, polished, and the complete document meets publication quality standards
**Depends on**: Phase 3
**Requirements**: QUAL-01, QUAL-02
**Success Criteria** (what must be TRUE):
  1. Every entry URL has been checked and resolves to an accessible page
  2. Every entry description is concise, accurate, and ends with a period
  3. README.md passes awesome-lint with zero errors in its final, fully-populated state
  4. The list reads coherently from top to bottom as a browsable reference document
**Plans**: TBD

## Progress

**Execution Order:**
Phases execute in numeric order: 1 -> 2 -> 3 -> 4

| Phase | Plans Complete | Status | Completed |
|-------|----------------|--------|-----------|
| 1. Scaffold and Standards | 0/2 | Not started | - |
| 2. Signal Path Categories | 0/0 | Not started | - |
| 3. Infrastructure and Resources | 0/0 | Not started | - |
| 4. Content Quality and Final Polish | 0/0 | Not started | - |
