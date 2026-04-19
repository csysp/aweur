# Architecture Patterns

**Domain:** Awesome-list (curated open source Eurorack resources)
**Researched:** 2026-04-19

## Recommended Architecture

An awesome-list is a single-file documentation project. The "architecture" is the README.md structure, entry format conventions, and supporting files. There is no application runtime -- the entire product is a Markdown document consumed on GitHub.

### File Tree

```
awesome-eurorack/
  README.md              # The list itself (canonical document)
  CONTRIBUTING.md        # Contribution guidelines (deferred to v2 per PROJECT.md)
  code-of-conduct.md     # Community standards (optional, deferred)
  .github/
    pull_request_template.md  # PR template (deferred to v2)
  media/
    logo.svg             # Optional project logo/badge
  LICENSE                # CC0 1.0 Universal (awesome-list standard)
```

**Build order implication:** README.md and LICENSE are the only files needed for v1. Everything else is v2.

### Component Boundaries

| Component | Responsibility | Communicates With |
|-----------|---------------|-------------------|
| README.md | The entire curated list -- TOC, categories, entries, resources | Users via GitHub rendering |
| LICENSE | Legal framework (CC0-1.0 required by awesome spec) | GitHub license detection |
| CONTRIBUTING.md (v2) | Defines entry criteria, formatting rules, PR workflow | Contributors via GitHub |
| awesome-lint CI (v2) | Validates README format compliance | GitHub Actions, README.md |

### README.md Section Hierarchy

This is the core architecture. The awesome-list spec dictates a specific ordering.

```
# Awesome Eurorack

[Description paragraph]
[Awesome badge + shields/badges]

## Contents                    <-- Auto-generated TOC

## [Category 1]               <-- Functional categories
  ### [Subcategory 1a]         <-- Optional subcategories
  - entries...
  ### [Subcategory 1b]
  - entries...

## [Category 2]
  - entries...

...

## Resources                   <-- Non-repo links section
  ### Tutorials
  ### Communities
  ### Specifications

## Contributing                <-- Link to CONTRIBUTING.md

## License                     <-- CC0 badge
```

**Critical spec requirements (MEDIUM confidence -- based on well-established conventions, but unable to verify against current spec docs):**

1. List title must be `# Awesome [Topic]` (not "Awesome List of...")
2. Short description immediately after the title
3. Table of Contents section required
4. Alphabetical ordering within each category
5. Each entry must have a link and description
6. No dead links
7. Consistent formatting throughout
8. CC0-1.0 license required for awesome-list registry inclusion
9. At least 30 items to be considered for the official awesome registry (but we can launch with fewer for our own purposes)

### Data Flow

```
Contributor discovers a project
  --> Opens PR adding entry to README.md (v2 workflow)
  --> awesome-lint validates format (v2 CI)
  --> Maintainer reviews for quality/relevance
  --> Merge to main
  --> GitHub renders updated README.md
  --> Users browse on GitHub
```

For v1 (structure-first, per PROJECT.md), the flow is simpler: maintainer authors the scaffold directly.

## Entry Format Convention

This is the most critical architectural decision -- it defines how every single item in the list looks.

### Recommended Entry Format

```markdown
- [Project Name](https://github.com/user/repo) `HW` `FW` - Brief description of what the module does.
```

**Format rules:**

| Element | Convention | Example |
|---------|-----------|---------|
| Link | `[Name](URL)` -- project name as display text | `[Braids](https://github.com/pichenettes/eurorack)` |
| Type tags | Inline code backtick tags after link | `` `HW` `` `` `FW` `` `` `SW` `` |
| Description | Dash-separated, sentence case, ends with period | `- Digital macro-oscillator with many synthesis models.` |
| Metadata badges (optional) | Shield.io badges for stars, license, last commit | `![Stars](https://img.shields.io/github/stars/user/repo)` |

### Type Tag Taxonomy

Per PROJECT.md, entries are tagged by type to preserve the HW/FW/SW dimension:

| Tag | Meaning | Example |
|-----|---------|---------|
| `HW` | Hardware design (schematics, PCB layouts, panel files) | KiCad/Eagle project files |
| `FW` | Firmware (embedded code running on the module) | C/C++ for STM32, AVR, Daisy |
| `SW` | Software tool (desktop/web apps, libraries, utilities) | Calibration tools, patch editors |
| `DOC` | Documentation, guides, specifications | Build guides, Eurorack spec docs |

Most Mutable Instruments-style repos will carry both `HW` and `FW` tags. This is fine and expected.

### Metadata Badges (Optional Enhancement)

Per PROJECT.md requirement for "stars, last updated, license badges":

```markdown
- [Project Name](URL) `HW` `FW` - Description. ![Stars](https://img.shields.io/github/stars/user/repo?style=flat-square) ![Last Commit](https://img.shields.io/github/last-commit/user/repo?style=flat-square)
```

**Architectural concern:** Badges add visual noise and make entries harder to scan. Many successful awesome-lists omit them. Consider deferring badges to v2 or making them a separate table format rather than inline.

**Recommendation:** Start v1 without badges. The entry format `[Name](URL) \`TAG\` - Description.` is clean and scannable. Badges can be added later without restructuring.

## Category Architecture for Eurorack Domain

Categories map to Eurorack module functions. Users think "I need an oscillator" -- categories should match that mental model.

### Recommended Category Hierarchy

```markdown
## Contents

- [Oscillators](#oscillators)
- [Filters](#filters)
- [Envelopes and VCAs](#envelopes-and-vcas)
- [LFOs and Modulation](#lfos-and-modulation)
- [Sequencers and Clocks](#sequencers-and-clocks)
- [Effects](#effects)
- [Mixers and Utilities](#mixers-and-utilities)
- [MIDI and USB](#midi-and-usb)
- [Power and Cases](#power-and-cases)
- [Development Platforms](#development-platforms)
- [Libraries and Frameworks](#libraries-and-frameworks)
- [Resources](#resources)
```

### Category Definitions

| Category | What belongs here | Notes |
|----------|------------------|-------|
| Oscillators | VCOs, digital oscillators, wavetable, FM, additive | Largest category likely |
| Filters | VCFs, LPF, HPF, BPF, multimode, state-variable | |
| Envelopes and VCAs | ADSR, AR, function generators, VCAs | Combined because they often appear together |
| LFOs and Modulation | LFOs, sample-and-hold, random, waveshapers | Modulation sources |
| Sequencers and Clocks | Step sequencers, generative, clock dividers/multipliers | |
| Effects | Delay, reverb, chorus, distortion, granular | |
| Mixers and Utilities | Mixers, mults, attenuators, logic, switches | Catch-all for utility modules |
| MIDI and USB | MIDI-to-CV, USB host/device, protocol bridges | Interface modules |
| Power and Cases | PSU designs, bus boards, case designs | Infrastructure |
| Development Platforms | Daisy, Teensy Audio, ESP32 platforms for Eurorack | Boards/platforms for building modules |
| Libraries and Frameworks | DSP libraries, hardware abstraction, UI frameworks | Code libraries, not modules |
| Resources | Tutorials, communities, specs, vendor docs | Non-repo links (subcategorized) |

### Resources Subcategories

```markdown
## Resources

### Tutorials and Guides
### Communities
### Specifications and Standards
### Vendors with Open Source Projects
```

### Category Ordering Rationale

Order follows signal flow in a typical Eurorack patch: sound source (Oscillators) through processing (Filters, VCAs) through modulation (LFOs, Sequencers) through effects to output. Infrastructure categories (MIDI, Power, Dev Platforms) come after signal-path categories. Resources at the end per awesome-list convention.

## Patterns to Follow

### Pattern 1: Alphabetical Within Categories
**What:** All entries within a category sorted alphabetically by project name.
**When:** Always -- this is an awesome-list spec requirement.
**Why:** Prevents implicit ranking. Makes scanning predictable.

### Pattern 2: One Project Per Line
**What:** Each entry is a single list item, no nested sub-items per entry.
**When:** Always.
**Why:** Maintains scanability. Descriptions should be concise enough to fit one line.

```markdown
## Oscillators

- [Braids](https://github.com/pichenettes/eurorack) `HW` `FW` - Digital macro-oscillator with many synthesis models.
- [Plaits](https://github.com/pichenettes/eurorack) `HW` `FW` - Next-generation macro-oscillator, successor to Braids.
```

### Pattern 3: Monorepo Handling
**What:** Some open source Eurorack projects (notably Mutable Instruments) host multiple modules in one repository.
**When:** A single repo contains multiple distinct modules.
**How:** List each module as a separate entry, all pointing to the same repo URL but with different anchors or path suffixes where possible. Add a note in the description.

```markdown
- [Braids](https://github.com/pichenettes/eurorack/tree/master/braids) `HW` `FW` - Digital macro-oscillator with many synthesis models. Part of the Mutable Instruments collection.
```

### Pattern 4: Consistent Description Style
**What:** Descriptions are sentence fragments starting with a capital letter, ending with a period.
**When:** Every entry.
**Example:** `- Digital macro-oscillator with many synthesis models.`
**Not:** `- digital macro-oscillator with many synthesis models` (no capital, no period)
**Not:** `- A digital macro-oscillator...` (don't start with articles A/An/The)

## Anti-Patterns to Avoid

### Anti-Pattern 1: Category Proliferation
**What:** Creating too many narrow categories (e.g., separate "VCO", "Digital Oscillator", "Wavetable" categories).
**Why bad:** Fragments the list, makes browsing harder, many categories end up with 1-2 entries.
**Instead:** Use broader functional categories. An oscillator is an oscillator regardless of synthesis method. Use description text to convey specifics.

### Anti-Pattern 2: Inline Metadata Overload
**What:** Cramming stars, license, last commit, language, and other badges into each entry.
**Why bad:** Visual noise destroys scanability -- the primary value of a curated list.
**Instead:** Keep entries clean. If metadata is truly desired, consider a separate machine-readable format (JSON/YAML) that generates badges, or defer to v2.

### Anti-Pattern 3: Nested Subcategories Deeper Than Two Levels
**What:** `## Category > ### Subcategory > #### Sub-subcategory`
**Why bad:** Breaks TOC generation, makes navigation confusing, usually means categories need rethinking.
**Instead:** Maximum two levels: `## Category` and `### Subcategory`. If you need a third level, merge or split differently.

### Anti-Pattern 4: Non-Alphabetical "Featured" Ordering
**What:** Putting popular/favorite projects at the top of a category.
**Why bad:** Violates awesome-list convention. Creates implicit endorsement. Causes contributor friction ("why isn't my project at the top?").
**Instead:** Strict alphabetical. Let descriptions and the curation itself signal quality.

### Anti-Pattern 5: Dead or Abandoned Projects Without Context
**What:** Listing repos with no commits in 3+ years without noting their status.
**Why bad:** Users waste time evaluating dead projects.
**Instead:** Either curate out truly dead projects, or add a note: `(archived)` or `(unmaintained)`.

## Build Order

Based on awesome-list conventions and PROJECT.md requirements, the recommended build order is:

### Phase 1: Scaffold
1. **LICENSE** -- CC0-1.0 (copy the standard text, takes 30 seconds)
2. **README.md header** -- Title, description, awesome badge
3. **README.md TOC** -- Contents section with all category anchors
4. **README.md categories** -- All `## Category` and `### Subcategory` headings with empty sections
5. **README.md footer** -- Contributing link placeholder, License section

**Rationale:** Get the full skeleton in place first. This validates the category taxonomy and section hierarchy before any entries are added.

### Phase 2: Entry Format and Sample Content
1. **Define entry format** in a comment or in CONTRIBUTING.md placeholder
2. **Add 2-3 sample entries** per major category to validate the format looks right
3. **Test rendering** on GitHub to ensure TOC links, badges, and formatting work

**Rationale:** A few real entries prove the format works before committing to populating everything.

### Phase 3: Population (out of scope per PROJECT.md)
1. Systematically discover and add entries
2. Verify all links work
3. Alphabetize within categories

### Phase 4: Contribution Infrastructure (v2 per PROJECT.md)
1. CONTRIBUTING.md with entry criteria and format guide
2. PR template
3. awesome-lint GitHub Action
4. Link-checking CI

## Scalability Considerations

| Concern | At 30 entries | At 100 entries | At 500+ entries |
|---------|---------------|----------------|-----------------|
| Navigation | TOC sufficient | TOC sufficient, consider section descriptions | May need a companion search tool or website |
| Category balance | Some categories empty | Most categories populated | May need subcategories |
| Maintenance | Solo maintainer fine | Solo maintainer fine | Need multiple maintainers, clear ownership |
| Link rot | Manual checking fine | Semi-automated checks needed | CI-based link checking essential |
| Format drift | Easy to enforce manually | Review burden increases | Linting CI becomes essential |

## Sources

- Awesome-list conventions based on the sindresorhus/awesome repository guidelines (MEDIUM confidence -- well-established conventions stable since 2014, but unable to verify against current spec docs due to web access limitations)
- Eurorack domain knowledge from training data (HIGH confidence for module function taxonomy -- Eurorack categories are well-established in the modular synthesis community)
- Entry format conventions derived from analysis of popular awesome-lists in training data (MEDIUM confidence -- format conventions are stable but specific lint rules may have updated)

**Key uncertainty:** The exact current awesome-lint rules and awesome-list submission checklist could not be verified. Before submitting to the awesome registry, the maintainer should manually review the current requirements at `https://github.com/sindresorhus/awesome`.
