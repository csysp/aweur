# Awesome Eurorack

## What This Is

A curated awesome-list of open source Eurorack modular synthesizer resources — hardware designs, firmware, software tools, and libraries hosted on GitHub, plus tutorials, communities, vendor docs, and specifications. Organized by module function (Oscillators, Filters, Sequencers, etc.) with type tags (HW/FW/SW) on each entry, following the official awesome-list specification.

## Core Value

A single, well-organized, community-maintained reference that makes it easy to discover open source Eurorack projects by what they do.

## Requirements

### Validated

(None yet — ship to validate)

### Active

- [ ] Curated README.md organized by module function with HW/FW/SW type tags
- [ ] Compliant with official awesome-list spec and awesome-lint
- [ ] Entry metadata (stars, last updated, license badges)
- [ ] Auto-generated Table of Contents
- [ ] Categories covering the full Eurorack ecosystem (Oscillators, Filters, Sequencers, Utilities, Effects, etc.)
- [ ] Resources section for tutorials, communities, specs, and vendor docs
- [ ] Structure ready for community contributions

### Out of Scope

- Static website or web frontend — pure Markdown, no generated site
- Pre-populated entries — structure first, entries added later
- CONTRIBUTING.md — deferred to v2
- CI/linting GitHub Actions — deferred to v2
- Commercial/closed-source module listings — open source focus only

## Context

- Eurorack is the dominant modular synthesizer format (3U height, +/-12V power, 3.5mm patch cables)
- The open source Eurorack community is active but fragmented across GitHub, forums, and personal sites
- Existing awesome-lists exist for synths broadly but none focused specifically on open source Eurorack repos
- The awesome-list ecosystem has a formal spec: curated content, consistent formatting, contribution guidelines, lint compliance
- Entry metadata (stars, last updated, license) helps users assess project health at a glance

## Constraints

- **Format**: Single README.md as the canonical document — awesome-list convention
- **Spec compliance**: Must pass awesome-lint for potential inclusion in the awesome registry
- **Content**: GitHub-hosted repos as primary entries, with a separate resources section for non-repo links

## Key Decisions

| Decision | Rationale | Outcome |
|----------|-----------|---------|
| Organize by function, not type | Users think "I need an oscillator" not "I need firmware" — function-first is more intuitive | — Pending |
| Type tags on entries (HW/FW/SW) | Preserves the hardware/firmware/software dimension without splitting categories | — Pending |
| Structure first, populate later | Get the scaffold right before filling with entries | — Pending |
| Official awesome-list compliance | Enables inclusion in the awesome registry, signals quality | — Pending |

## Evolution

This document evolves at phase transitions and milestone boundaries.

**After each phase transition** (via `/gsd-transition`):
1. Requirements invalidated? → Move to Out of Scope with reason
2. Requirements validated? → Move to Validated with phase reference
3. New requirements emerged? → Add to Active
4. Decisions to log? → Add to Key Decisions
5. "What This Is" still accurate? → Update if drifted

**After each milestone** (via `/gsd-complete-milestone`):
1. Full review of all sections
2. Core Value check — still the right priority?
3. Audit Out of Scope — reasons still valid?
4. Update Context with current state

---
*Last updated: 2026-04-19 after initialization*
