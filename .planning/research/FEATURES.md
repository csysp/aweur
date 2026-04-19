# Feature Landscape

**Domain:** Curated awesome-list for open source Eurorack modular synthesizer resources
**Researched:** 2026-04-19
**Confidence:** MEDIUM (based on training data -- web verification was unavailable)

## Table Stakes

Features users expect from any awesome-list. Missing any of these and the list feels broken, untrustworthy, or gets rejected from the awesome registry.

### Awesome-List Structural Requirements

| Feature | Why Expected | Complexity | Notes |
|---------|--------------|------------|-------|
| Single README.md as canonical document | Awesome-list convention; entire list lives in one file | Low | Non-negotiable for registry inclusion |
| Table of Contents | Required by awesome-lint; users need to jump to sections | Low | Auto-generated via markdown-toc or manually maintained |
| Consistent entry format | Every entry must follow same pattern: `[Name](url) - Description.` | Low | awesome-lint enforces trailing period, dash separator |
| Alphabetical ordering within sections | awesome-lint requirement; makes scanning predictable | Low | Must be maintained on every addition |
| License file (CC0-1.0) | Required for awesome registry submission | Low | CC0 is the standard for awesome-lists |
| Short list description at top | awesome-lint requires a subtitle/tagline under the heading | Low | One line explaining what the list covers |
| Awesome badge | Visual signal of awesome-list membership | Low | `[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)` |
| No dead links | Broken links erode trust; lint tools check this | Med | Needs periodic manual or CI-based validation |

### Content Organization

| Feature | Why Expected | Complexity | Notes |
|---------|--------------|------------|-------|
| Function-based categories | Users think "I need an oscillator" not "I need firmware" | Med | Core organizational principle per PROJECT.md |
| Descriptive entry text | Each link needs a 1-sentence description of what the project is/does | Med | Most time-consuming part of curation |
| Resources/meta section | Non-repo links (tutorials, specs, communities) need a home | Low | Separate from main project listings |

### Per-Entry Metadata

| Feature | Why Expected | Complexity | Notes |
|---------|--------------|------------|-------|
| Project name as link text | Standard awesome-list pattern | Low | — |
| URL to repository | The whole point of the list | Low | GitHub links primarily |
| One-line description | Users need to know what it is before clicking | Low | End with period per spec |

## Differentiators

Features that set this list apart from generic synth lists or scattered bookmarks. Not expected by awesome-list convention, but high value for the Eurorack domain.

### Type Tags (HW/FW/SW)

| Feature | Value Proposition | Complexity | Notes |
|---------|-------------------|------------|-------|
| Inline type tags per entry | Eurorack projects span hardware, firmware, and software; users need to know what they are getting without clicking through | Low | Use badges or inline markers like `[HW]` `[FW]` `[SW]` -- keeps function-first organization while preserving type dimension |

### Entry Enrichment

| Feature | Value Proposition | Complexity | Notes |
|---------|-------------------|------------|-------|
| License badge/tag per entry | Open source hardware has varied licensing (CERN-OHL, MIT, GPL); users need to know before investing time | Med | Could be inline text like `MIT` or a badge; manual maintenance burden |
| GitHub stars indicator | Signals project popularity and community traction | Med | Manual maintenance is painful; better suited for CI automation (deferred to v2) |
| Last-updated/activity indicator | Eurorack projects often go dormant; users need to assess project health | Med | Same as stars -- valuable but maintenance-heavy without automation |
| Module format details | HP width, panel format, through-hole vs SMD -- critical for builders | High | Not standard awesome-list metadata; could overload entries |

### Eurorack-Specific Sections

| Feature | Value Proposition | Complexity | Notes |
|---------|-------------------|------------|-------|
| Standards and Specifications section | Eurorack electrical specs, mechanical specs, power standards are essential reference | Low | Links to doepfer specs, voltage standards docs |
| PCB/Panel fabrication resources | Builders need to know where to get boards made | Low | Curated list of services and tutorials |
| Development tools section | KiCad libraries, panel generators, calibration tools specific to Eurorack | Low | Cross-cutting concern that does not fit module categories |
| BOM/sourcing resources | Where to buy components, especially specialized ones (potentiometers, jacks, ICs) | Low | High value for builders, low maintenance |

### Organizational Enhancements

| Feature | Value Proposition | Complexity | Notes |
|---------|-------------------|------------|-------|
| Category descriptions | Brief intro text per section explaining what the category covers | Low | Helps newcomers; not all awesome-lists do this |
| Cross-referencing notation | Some projects span categories (e.g., a sequencer with built-in quantizer); note where a project appears vs where it is primarily listed | Med | Avoid duplication; use "See also: [Category]" pattern |
| Beginner-friendly markers | Flag projects that are well-documented, easy to build, or have active community support | Low | High value for newcomers to DIY Eurorack |

## Anti-Features

Features to explicitly NOT build. These would hurt the list's quality, maintainability, or alignment with awesome-list conventions.

| Anti-Feature | Why Avoid | What to Do Instead |
|--------------|-----------|-------------------|
| Commercial/closed-source listings | Dilutes the open source focus; becomes a product catalog instead of a resource list | Keep strict to open source repos; commercial vendors only in a "where to buy components" resources section |
| Web frontend / static site | Adds build complexity, diverges from awesome-list convention, creates maintenance burden | Stay pure Markdown in README.md; the GitHub rendering is the UI |
| Ratings or reviews | Subjective, creates drama, impossible to maintain fairly | Let GitHub stars speak; curate for quality instead of rating |
| Exhaustive metadata tables | Turning each entry into a spec sheet kills scannability | Keep entries to one line; link to the project for details |
| Duplicate entries across categories | Inflates the list, creates sync problems, confuses users | Primary listing in one category; "See also" cross-references if truly needed |
| Auto-populated content (scrapers) | Defeats the purpose of curation; quality drops | Every entry is manually vetted and described |
| Discussion/comments in the list | README is not a forum | Point to GitHub Discussions or Issues for conversation |
| Version pinning | Repos evolve; pinning versions creates staleness | Link to main repo, not specific releases |
| Nested sub-sub-categories | Over-categorization makes navigation harder, not easier | Keep hierarchy to two levels max (Category > entries) |
| Pre-populated entries before structure is validated | Structure-first per PROJECT.md; filling entries into a bad structure wastes effort | Scaffold categories and format, validate with awesome-lint, then populate |

## Eurorack Module Categories

The primary organizational structure. Based on standard Eurorack functional taxonomy.

### Core Module Functions (Mandatory Categories)

| Category | What It Covers | Expected Volume |
|----------|---------------|-----------------|
| Oscillators (VCO/DCO) | Analog and digital oscillator designs, wavetable engines | High -- most popular DIY category |
| Filters (VCF) | Low-pass, high-pass, band-pass, multimode filter designs | High |
| Amplifiers (VCA) | Voltage-controlled amplifiers, linear and exponential | Medium |
| Envelopes (EG) | ADSR, AD, function generators, envelope followers | Medium |
| LFOs | Low-frequency oscillators, modulation sources | Medium |
| Sequencers | Step sequencers, generative sequencers, MIDI-to-CV | High -- very active open source area |
| Effects | Delay, reverb, distortion, chorus, granular processors | High |
| Utilities | Mixers, multiples, attenuators, offset generators, logic | High -- broad category |
| MIDI/CV Interfaces | MIDI-to-CV, USB-MIDI, CV-to-MIDI converters | Medium |
| Clock/Timing | Clock generators, clock dividers, clock multipliers, reset/run | Medium |
| Quantizers | Pitch quantizers, scale selectors | Low-Medium |
| Random/Noise | Noise sources, sample-and-hold, random voltage generators | Low-Medium |
| Mixers | Audio and CV mixers, crossfaders, matrix mixers | Medium |
| Power Supplies | Bus boards, PSU designs, power distribution | Low but essential |
| Output/Input | Audio output modules, headphone amps, line-level interfaces | Low-Medium |

### Resources Sections (Non-Module Content)

| Section | What It Covers |
|---------|---------------|
| Standards and Specifications | Eurorack electrical standard, Doepfer specs, power specs |
| Development Tools | KiCad Eurorack libraries, panel design tools, firmware frameworks |
| PCB and Panel Fabrication | Fabrication services, tutorials on ordering PCBs and panels |
| Component Sourcing | Where to buy Eurorack-specific components (jacks, knobs, pots) |
| Tutorials and Guides | How to design Eurorack modules, getting started guides |
| Communities | Forums, Discord servers, subreddits, mailing lists |
| Books and Publications | Relevant books on synth design, electronics |

## Feature Dependencies

```
License file (CC0) ─── required before ──> awesome registry submission
Table of Contents ──── required before ──> any content (keeps navigation working)
Category structure ─── required before ──> entry population
Entry format spec ──── required before ──> entry population
awesome-lint pass ──── required before ──> awesome registry submission
awesome-lint pass ──── depends on ──────> alphabetical ordering + entry format + ToC + license
Type tags (HW/FW/SW) ─ depends on ──────> entry format spec (tags must be part of the format)
Cross-references ───── depends on ──────> multiple categories populated
Beginner markers ───── depends on ──────> entries existing to evaluate
Stars/activity data ── depends on ──────> CI automation (v2) or manual effort
```

## MVP Recommendation

Prioritize (in order):

1. **Category scaffold** -- Define all module function categories and resource sections with brief descriptions. This is the structural backbone.
2. **Entry format specification** -- Lock down the exact format: `[Name](url) - Description. [HW] [FW] [SW]` with consistent rules for tags.
3. **Awesome-list compliance skeleton** -- License (CC0), badge, tagline, Table of Contents, alphabetical ordering convention. Must pass awesome-lint with empty categories.
4. **Standards and Specifications section** -- Populate this first because it is small, stable, and immediately useful to anyone landing on the list.
5. **Type tags (HW/FW/SW)** -- Integrate into the entry format from day one. Retrofitting tags later is painful.

Defer:

- **Stars/activity badges**: Manual maintenance is unsustainable. Defer to v2 when CI automation (GitHub Actions) is in scope.
- **License per entry**: Useful but adds curation overhead. Can be added incrementally as entries are vetted.
- **Module format details (HP, SMD/THT)**: Too much metadata for the list format. Projects should document this themselves.
- **Beginner-friendly markers**: Requires enough entries to meaningfully compare. Add after initial population.
- **CONTRIBUTING.md**: Explicitly deferred per PROJECT.md.
- **Cross-references**: Only meaningful once multiple categories have entries.

## Sources

- Awesome-list official guidelines (sindresorhus/awesome repository): awesome.md, create-list.md -- MEDIUM confidence (based on training data, unable to verify current version)
- awesome-lint validation rules -- MEDIUM confidence (training data)
- Eurorack functional taxonomy based on Doepfer module categorization and standard modular synth terminology -- HIGH confidence (domain knowledge is stable and well-established)
- Open source hardware licensing patterns (CERN-OHL, MIT, GPL) -- HIGH confidence (well-documented standards)
