# Domain Pitfalls

**Domain:** Curated awesome-list for open source Eurorack resources
**Researched:** 2026-04-19
**Overall Confidence:** MEDIUM (based on training data; web verification unavailable)

## Critical Pitfalls

Mistakes that cause rejection from the awesome registry, loss of community trust, or require structural rewrites.

### Pitfall 1: Failing awesome-lint on Structural Rules

**What goes wrong:** The list fails `awesome-lint` on rules that seem trivial but are strictly enforced: missing ToC, wrong heading hierarchy, list items not alphabetically sorted within sections, descriptions not ending with periods, or descriptions starting with articles ("A", "An", "The").

**Why it happens:** The awesome-list spec has many small formatting rules that are not obvious from looking at other lists. Authors write naturally instead of conforming to machine-checkable rules.

**Consequences:** Cannot be submitted to the awesome registry. Fixing after 100+ entries are added means tedious reformatting.

**Prevention:**
- Install `awesome-lint` as a dev dependency from day one and run it on every change.
- Write 3-5 sample entries in the real format BEFORE building the full scaffold. Lint them. Learn the rules on a small surface.
- Key rules to internalize early:
  - List items: `- [Name](url) - Description ending with period.` (note: dash separator, not colon)
  - Descriptions must NOT start with "A", "An", "The", or redundant prefixes like "A module that..."
  - Alphabetical ordering within each section
  - ToC must be auto-generated and match headings exactly
  - No trailing whitespace, no empty sections
  - The repo must have a LICENSE file (not just license headers)
  - The repo needs a proper README with project description before the list

**Detection:** Run `npx awesome-lint` after every structural change. If it passes with 0 entries, the scaffold is sound.

**Phase relevance:** Phase 1 (scaffold). Get this right before any content goes in.

---

### Pitfall 2: Categorization That Fights the Domain

**What goes wrong:** Categories are organized around technical implementation details (e.g., "KiCad Projects", "Arduino Firmware", "Pure Data Patches") instead of user intent (e.g., "Oscillators", "Filters", "Sequencers"). Or conversely, categories are too granular ("Wavetable Oscillators", "Subtractive Oscillators", "FM Oscillators") creating lots of near-empty sections.

**Why it happens:** The curator thinks like a developer (by technology) or an expert (hyper-specific taxonomy) instead of like the target user who thinks "I need a filter module."

**Consequences:** Users cannot find what they need. Restructuring after entries exist creates broken links if anyone has bookmarked specific sections. The list feels academic rather than useful.

**Prevention:**
- Use function-first categories (Oscillators, Filters, Envelopes/LFOs, Sequencers, Effects, Utilities, Mixers/VCAs, MIDI/CV, Power/Cases) -- the project already plans this.
- Cap initial categories at 8-12 top-level sections. Subcategories only when a section exceeds ~15 entries.
- Add type tags (HW/FW/SW) as inline markers, not as separate category trees.
- Study how ModularGrid, Muffwiggler/ModWiggler, and the Eurorack Wikipedia page organize modules -- these reflect community mental models.

**Detection:** If you have more than 3 empty categories after initial population, the taxonomy is too granular. If entries constantly feel like they could go in 2+ categories, the taxonomy is wrong.

**Phase relevance:** Phase 1 (scaffold design). Changing categories later is a rewrite.

---

### Pitfall 3: Scope Drift Into Closed Source and Commercial

**What goes wrong:** The list starts as "open source Eurorack" but gradually accepts entries that are: partially open source (schematics but proprietary firmware), "source available" but not truly open licensed, commercial products with open documentation, or projects using restrictive non-commercial licenses that do not meet OSI/OSHWA definitions.

**Why it happens:** The Eurorack ecosystem has a gray area. Many builders share schematics but keep firmware closed. Some projects use Creative Commons NonCommercial licenses. Contributors submit their favorite projects regardless of license. Rejecting popular projects feels exclusionary.

**Consequences:** The list loses its identity. Users cannot trust that listed projects are actually buildable/forkable. Arguments about what counts as "open source" fragment the community.

**Prevention:**
- Define "open source" explicitly in the README or CONTRIBUTING.md: require an OSI-approved or OSHWA-compatible license for HW entries, and an OSI-approved license for SW/FW entries.
- Create a clear inclusion checklist: source files available (not just PDFs of schematics), buildable by a third party, license file present in repo.
- For gray-area projects (e.g., open hardware + closed firmware), either exclude or create a clearly labeled "Partially Open" subsection.
- Add license badges to every entry so the status is transparent.

**Detection:** If you find yourself writing "sort of open source" or debating whether a project counts, the inclusion criteria are too vague.

**Phase relevance:** Phase 1 (define rules) and ongoing (enforce during contributions).

---

### Pitfall 4: Link Rot Destroying the List Over Time

**What goes wrong:** GitHub repos get deleted, archived, or renamed. Personal sites hosting schematics go offline. Forum threads referenced in Resources sections disappear. Within 12-18 months, 10-20% of links in a hardware-focused list can break.

**Why it happens:** Open source hardware projects have higher abandonment rates than software. Individual makers move on, lose interest, or switch platforms. GitHub repos get renamed when users change their username. Forum platforms shut down (the Muffwiggler-to-ModWiggler migration broke thousands of links).

**Consequences:** Broken links signal an unmaintained list. Users lose trust. The awesome registry can delist for quality issues.

**Prevention:**
- Add metadata indicating last-updated date or last-commit date for each entry. Stale repos (2+ years no commits) should be flagged, not necessarily removed.
- Plan a quarterly link-check cadence. Tools like `awesome-lint` check some links; supplement with `markdown-link-check` or `lychee` in CI.
- For critical non-GitHub resources (forum posts, blog articles), note the Wayback Machine URL as a fallback.
- Prefer linking to GitHub repos over personal websites -- GitHub is more durable.
- When a project is archived/abandoned but still valuable, move it to an "Archived/Historical" section rather than deleting.

**Detection:** Any PR that adds entries but no one has checked existing links in 3+ months is a warning sign.

**Phase relevance:** Phase 2 (CI/linting) and ongoing maintenance.

---

### Pitfall 5: Empty Scaffold Syndrome

**What goes wrong:** The list is published with a beautiful category structure but zero or near-zero entries. It looks like an abandoned template. No one contributes to an empty list because there is no demonstrated curation standard.

**Why it happens:** The project decides "structure first, populate later" (which this project explicitly plans). This is fine as an internal milestone but fatal if published prematurely.

**Consequences:** First impressions matter on GitHub. A list with 12 categories and 2 entries looks abandoned. Stars and contributions will not come. The awesome registry will reject lists with insufficient content.

**Prevention:**
- Do NOT publicize/submit the list until it has at least 3-5 entries per category (the awesome-list spec suggests a minimum viable content bar, though the exact threshold has varied).
- Treat scaffold creation and initial population as the same phase, not separate milestones.
- Seed each category with 2-3 well-known projects personally verified by the maintainer. Examples: Mutable Instruments (Emilie Gillet's repos are the gold standard of open source Eurorack), Ornament and Crime, Befaco open hardware designs.
- The initial seed demonstrates the entry format, quality bar, and scope to future contributors.

**Detection:** If the README is pushed to `main` and has any section with `## Category Name` followed by nothing, the list is not ready for public eyes.

**Phase relevance:** Phase 1 must include initial population, not just structure.

---

## Moderate Pitfalls

### Pitfall 6: Ignoring the awesome-list PR Submission Checklist

**What goes wrong:** The maintainer builds a great list, submits a PR to `sindresorhus/awesome`, and gets rejected for non-content reasons: repo is too new (needs 30+ days of history), not enough stars, missing code of conduct, wrong badge format, or the PR description does not follow the template.

**Prevention:**
- Read the `pull_request_template.md` in the awesome repo BEFORE starting work. Design around those requirements.
- The repo must exist for 30+ days before submission.
- Must have a meaningful number of stars (community consensus suggests 50+ though this is not formally specified).
- Must include: LICENSE, code-of-conduct.md (or use GitHub default), contributing.md.
- The awesome badge must link back to the awesome registry.
- Do not submit until organically ready; premature submission burns your one chance at a first impression.

**Phase relevance:** Late phase -- only relevant when actually submitting to the registry.

---

### Pitfall 7: Entry Descriptions That Are Useless

**What goes wrong:** Entries have descriptions like "A Eurorack oscillator module" or "Digital synth firmware" -- they describe the category, not the project. Every entry in the Oscillators section says "oscillator" and the user learns nothing.

**Prevention:**
- Descriptions should answer: "What makes THIS project different from others in this category?"
- Good: "Macro-oscillator with 16 synthesis algorithms, based on the Mutable Instruments Braids platform."
- Bad: "An open source digital oscillator module."
- Enforce a minimum description quality in contribution guidelines. Descriptions should mention the distinguishing feature, the platform/MCU if relevant for hardware, or the key capability.
- Keep descriptions to one sentence (awesome-lint enforces this).

**Detection:** Read all descriptions in a section. If you cannot distinguish entries without clicking the links, descriptions are too generic.

**Phase relevance:** Phase 1 (set the standard with seed entries) and ongoing.

---

### Pitfall 8: Tag System Overengineering

**What goes wrong:** The type-tag system (HW/FW/SW) expands to include: platform tags (STM32, AVR, Teensy, Daisy, RPi Pico), format tags (KiCad, Eagle, Gerber), skill-level tags, BOM-available tags, panel-included tags. The entry format becomes a wall of badges that is hard to read and harder to maintain.

**Prevention:**
- Start with exactly three tags: HW, FW, SW. These are orthogonal and universally applicable.
- Resist adding more tag dimensions until there are 50+ entries and a clear user need.
- If platform/MCU information is important, put it in the description text, not in a badge system.
- Badges (shields.io) for stars, last-commit, and license are standard and useful. Custom badge taxonomies are not.

**Detection:** If the entry format line exceeds ~120 characters before the description, it is over-tagged.

**Phase relevance:** Phase 1 (format design).

---

### Pitfall 9: No Contribution Barrier = Quality Collapse

**What goes wrong:** Without CONTRIBUTING.md or PR templates, well-meaning contributors add entries that: link to repos with no license, have no description, duplicate existing entries, add personal projects with 0 stars, or use inconsistent formatting.

**Prevention:**
- Even though CONTRIBUTING.md is deferred to v2, plan for it. At minimum, add a one-line note in the README: "Contributions welcome -- please read [contributing guidelines](contributing.md) first."
- Define minimum quality criteria for entries: repo must have a license, must have meaningful content (not just an empty README), must be related to Eurorack specifically (not general synth/DSP).
- Use a PR template that asks: "Is this project open source licensed? Have you verified the link works? Does the description follow the format?"

**Detection:** First external PR that adds a low-quality entry means contribution guidelines are overdue.

**Phase relevance:** Phase 2 (community readiness), but plan the criteria in Phase 1.

---

### Pitfall 10: Eurorack-Specific Ambiguity

**What goes wrong:** Entries include projects that are: general DIY synth but not Eurorack format, Eurorack-adjacent (e.g., Kosmo format, Serge), modular synth software with no hardware component, or general DSP libraries that could theoretically be used in Eurorack.

**Prevention:**
- Define "Eurorack" explicitly: 3U (128.5mm) height, horizontal pitch measured in HP, +/-12V power standard, 3.5mm (1/8") patch cables, Doepfer-compatible power headers.
- Software entries must specifically target or interface with Eurorack hardware (e.g., VCV Rack modules that mirror real hardware, calibration tools, firmware for Eurorack-format modules).
- Create a "Related Formats" section if you want to acknowledge adjacent ecosystems (Kosmo, Buchla, 5U) without polluting the main list.
- General-purpose DSP libraries belong only if they are packaged for or widely used in Eurorack firmware (e.g., the Mutable Instruments DSP library).

**Detection:** If a contributor asks "does X count as Eurorack?" and you hesitate, the boundary is not clear enough.

**Phase relevance:** Phase 1 (scope definition in README).

---

## Minor Pitfalls

### Pitfall 11: Alphabetical Ordering Conflicts

**What goes wrong:** awesome-lint enforces alphabetical ordering within sections, but some entries have names that are hard to alphabetize (projects with special characters, numbers, or names that differ from their repo names). Maintainers alphabetize by repo name but display a different project name.

**Prevention:**
- Alphabetize by the display name (what appears in the link text), not the URL.
- Decide upfront: display the project's self-chosen name, not the GitHub repo slug. "Ornament & Crime" not "ornament-and-crime".
- For entries starting with numbers or symbols, place them at the top or bottom of the section consistently.

**Phase relevance:** Phase 1 (format decisions).

---

### Pitfall 12: Neglecting the Resources Section

**What goes wrong:** All effort goes into repo entries. The Resources section (tutorials, communities, specs, vendor docs) is an afterthought with 2-3 generic links. But for Eurorack, resources are critical: the Doepfer A-100 technical spec, Kristian Blaabjerg's Eurorack DIY guide, the LMNC (Look Mum No Computer) community, ModWiggler forums.

**Prevention:**
- Treat Resources as a first-class section with its own subcategories: Standards/Specifications, Tutorials/Guides, Communities/Forums, Vendor Documentation, PCB/Component Suppliers.
- Seed it with the foundational references that every Eurorack DIY builder needs.

**Phase relevance:** Phase 1 (structure and initial population).

---

### Pitfall 13: Ignoring Project Health Signals

**What goes wrong:** The list includes repos that have not been updated in 5+ years, have unresolved critical issues, or have been explicitly abandoned by maintainers. Users build hardware based on abandoned firmware and get stuck.

**Prevention:**
- Include last-commit-date badges (shields.io dynamic badges can do this).
- Flag or section-separate projects with no activity in 2+ years. Label as "Archived" or "Inactive" rather than removing -- the hardware designs may still be valid even if firmware is stale.
- For hardware projects specifically, staleness is less concerning (a good PCB design from 2018 is still a good PCB design). For firmware, staleness matters more (dependency rot, MCU availability).

**Phase relevance:** Phase 1 (badge design) and ongoing maintenance.

---

## Phase-Specific Warnings

| Phase Topic | Likely Pitfall | Mitigation |
|-------------|---------------|------------|
| Scaffold/Structure (Phase 1) | Empty scaffold published too early | Combine structure + seed entries into one phase; do not push to main until categories have content |
| Scaffold/Structure (Phase 1) | Category taxonomy fights user mental model | Use function-first categories; validate against how ModularGrid and forums organize modules |
| Scaffold/Structure (Phase 1) | awesome-lint failures baked into structure | Run awesome-lint on first 3 entries before building full scaffold |
| Format/Entries (Phase 1) | Over-engineered tag/badge system | Start with HW/FW/SW only; resist adding dimensions until 50+ entries |
| Format/Entries (Phase 1) | Generic entry descriptions | Write exemplary seed entries that set the quality bar |
| Scope Definition (Phase 1) | Ambiguous open-source and Eurorack boundaries | Write explicit inclusion criteria in README before accepting contributions |
| CI/Automation (Phase 2) | No link checking leads to silent rot | Add markdown-link-check or lychee to CI pipeline |
| Community (Phase 2) | First contributions are low quality | Ship CONTRIBUTING.md and PR template before publicizing |
| Registry Submission (Late) | Rejected for non-content reasons | Review the awesome PR template requirements 30+ days before submitting |
| Ongoing Maintenance | Scope creep into non-Eurorack or closed-source | Revisit inclusion criteria quarterly; document rejection reasons for transparency |

## Sources

- Awesome list specification and guidelines: `github.com/sindresorhus/awesome` (training data, not live-verified -- MEDIUM confidence)
- awesome-lint tool behavior: `github.com/sindresorhus/awesome-lint` (training data -- MEDIUM confidence)
- Eurorack ecosystem knowledge: Doepfer A-100 standard, Mutable Instruments open source repos, ModularGrid taxonomy (training data -- HIGH confidence for domain facts, MEDIUM for current repo status)
- Open source hardware curation challenges: general ecosystem knowledge (MEDIUM confidence)

**Note:** Web search and fetch tools were unavailable during this research session. All findings are based on training data. The awesome-list spec and lint rules should be verified against the current repository before implementation, as these requirements evolve over time.
