---
phase: 02-signal-path-categories
plan: 01
subsystem: content
tags: [eurorack, awesome-list, markdown, mutable-instruments, open-hardware]

requires:
  - phase: 01-scaffold-and-standards
    provides: README.md scaffold with 14 category headings, entry format, lint config

provides:
  - All 7 signal-path categories populated with 2-5 real verified entries each
  - 22 total verified entries across Oscillators, Filters, VCAs, Envelopes, Sequencers, Modulation, Effects

affects: [03-additional-categories, future-content-phases]

tech-stack:
  added: []
  patterns:
    - "Entry format: [Name](url) `TAG` - Description not starting with A/An/The, ending with period."
    - "Tags HW/FW/SW in that order, space-separated when multiple"
    - "Sections alphabetically sorted by display name"
    - "awesome-lint rejects descriptions starting with numbers when tags precede dash — use letter-first descriptions"

key-files:
  created: []
  modified:
    - README.md

key-decisions:
  - "Moved Zlosynth Achordion from Filters to Oscillators — it is a chord oscillator, not a filter"
  - "Removed Winterbloom Sol from VCAs — it is a MIDI-CV converter, belongs in Phase 3 MIDI section"
  - "Replaced Allen Synthesis account-level entry in Envelopes with BleepSound Basic ADSR — more specific and correctly categorized"
  - "Used BleepSound KiCad-based HW repos for Filters/VCAs/Envelopes to provide non-Mutable diversity"
  - "awesome-lint awesome-list-item rule rejects descriptions starting with digits (e.g. '4HP...') when tags precede the dash — rephrased to start with capital letter"
  - "Kept Erica Synths DIY account-level entry in Modulation — verified it includes LFO and CV generator modules"

patterns-established:
  - "Description must start with a capital letter, not a digit, when tags precede the dash separator"
  - "Use specific Mutable Instruments subdirectory URLs (tree/master/module) not the top-level repo"

requirements-completed:
  - MCAT-01
  - MCAT-02
  - MCAT-03
  - MCAT-04
  - MCAT-05
  - MCAT-06
  - MCAT-07

duration: 30min
completed: 2026-04-20
---

# Phase 2 Plan 1: Signal-Path Categories Summary

**Seven signal-path categories populated with 22 verified open-source Eurorack entries from Mutable Instruments, BleepSound, Clatters, Zlosynth, Monome, Erica Synths, and others — both linters exit 0.**

## Performance

- **Duration:** ~30 min
- **Started:** 2026-04-20T01:20:00Z
- **Completed:** 2026-04-20T01:49:29Z
- **Tasks:** 2 of 2
- **Files modified:** 1 (README.md)

## Accomplishments

- Populated all 7 signal-path categories (Oscillators, Filters, VCAs, Envelopes, Sequencers, Modulation, Effects) with 2-5 real verified entries each
- Verified all 22 URLs via HTTP and GitHub API before adding — every repo returns 200, has accessible source files
- Both `npx awesome-lint README.md` and `npx markdownlint-cli2 README.md` exit 0
- Correctly reclassified Phase 1 placeholder entries (Achordion moved to Oscillators; Sol removed from VCAs)
- Discovered and applied awesome-lint rule: descriptions preceded by backtick tags must not start with a digit

## Entry Counts per Category

| Category | Count | Entries |
|----------|-------|---------|
| Oscillators | 5 | Clatters Sibilla, MI Braids, MI Plaits, MI Rings, Zlosynth Achordion |
| Filters | 3 | BleepSound MS20 VCF, MI Ripples, MI Shelves |
| VCAs | 2 | BleepSound Basic VCA, MI Veils |
| Envelopes / Function Generators | 3 | BleepSound Basic ADSR, MI Peaks, MI Stages |
| Sequencers | 3 | Monome Teletype, Pangrus BPD, TruthTable |
| Modulation | 3 | Erica Synths DIY, MI Tides, Rheslip Quad LFO |
| Effects | 3 | Emeb RP2040 Audio, Kxmx Bluemchen, Modularev Nemesis |
| **Total** | **22** | |

## Phase 1 Placeholder Changes

| Entry | Phase 1 Category | Action | Reason |
|-------|-----------------|--------|--------|
| Mutable Instruments Braids | Oscillators | KEPT | Correctly categorized |
| Zlosynth Achordion | Filters | MOVED to Oscillators | Chord oscillator, not a filter |
| Winterbloom Sol | VCAs | REMOVED | MIDI-CV converter; belongs in Phase 3 MIDI/Digital Interfaces |
| Allen Synthesis (account) | Envelopes | REPLACED | Account-level entry too broad; replaced with BleepSound Basic ADSR |
| Monome Teletype | Sequencers | KEPT | Correctly categorized |
| Erica Synths DIY | Modulation | KEPT | Verified account includes LFO/CV modules |
| Modularev Nemesis | Effects | KEPT | Correctly categorized reverb module |

## Task Commits

1. **Task 1: Research and classify candidate repos** - (no commit — research only, documented in task)
2. **Task 2: Rewrite all 7 signal-path sections** - `a657483` (feat)

## Files Modified

- `README.md` - All 7 signal-path sections replaced/expanded with verified entries

## Lint Verification

```
$ npx awesome-lint README.md
- Linting
✔ Linting
(exit 0)

$ npx markdownlint-cli2 README.md
markdownlint-cli2 v0.22.0 (markdownlint v0.40.0)
Finding: README.md
Linting: 1 file(s)
Summary: 0 error(s)
(exit 0)
```

## Decisions Made

- Moved Zlosynth Achordion from Filters to Oscillators — it is a chord-crafting wavetable oscillator, not a filter
- Removed Winterbloom Sol from VCAs — it is a MIDI-CV converter, belongs in Phase 3
- Replaced Allen Synthesis account-level entry in Envelopes with BleepSound Basic ADSR for specificity
- Used BleepSound KiCad-based `HW`-only repos to provide non-Mutable Instruments diversity in Filters/VCAs/Envelopes
- Rephrased descriptions starting with numbers (e.g. "4HP Eurorack...") to start with capital letters — awesome-lint's `awesome-list-item` rule rejects digit-leading descriptions when backtick tags precede the dash separator

## Deviations from Plan

### Auto-fixed Issues

**1. [Rule 1 - Bug] awesome-lint rejects descriptions starting with digits after backtick tags**
- **Found during:** Task 2 (lint verification)
- **Issue:** awesome-lint `awesome-list-item` rule line 233 checks `/ - [A-Z]/` for the fallback when description prefix is `inlineCode` (backtick tag). Entries "10HP digital..." and "4HP Eurorack..." failed because `1` and `4` are not `[A-Z]`
- **Fix:** Rephrased Clatters Sibilla from "10HP digital stereo oscillator..." to "Digital stereo oscillator..." and Kxmx Bluemchen from "4HP Eurorack effects..." to "Eurorack effects module..."
- **Files modified:** README.md
- **Verification:** Both linters exit 0 after fix
- **Committed in:** a657483

---

**Total deviations:** 1 auto-fixed (Rule 1 - Bug)
**Impact on plan:** Minor description rephrasing. No scope creep, no content accuracy lost.

## Issues Encountered

None beyond the awesome-lint digit-leading description issue (documented as deviation above).

## MCAT Requirements Status

| Requirement | Category | Status |
|-------------|----------|--------|
| MCAT-01 | Oscillators (2-5 entries) | Complete — 5 entries |
| MCAT-02 | Filters (2-5 entries) | Complete — 3 entries |
| MCAT-03 | VCAs (2-5 entries) | Complete — 2 entries |
| MCAT-04 | Envelopes (2-5 entries) | Complete — 3 entries |
| MCAT-05 | Sequencers (2-5 entries) | Complete — 3 entries |
| MCAT-06 | Modulation (2-5 entries) | Complete — 3 entries |
| MCAT-07 | Effects (2-5 entries) | Complete — 3 entries |

## User Setup Required

None — no external service configuration required.

## Next Phase Readiness

- All 7 signal-path categories are populated and lint-passing
- Ready for Phase 2 Plan 2 (additional categories: Utilities, MIDI/Digital Interfaces, Power) or Phase 3
- No blockers

---
*Phase: 02-signal-path-categories*
*Completed: 2026-04-20*
