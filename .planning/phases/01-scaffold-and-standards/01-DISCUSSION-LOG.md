# Phase 1: Scaffold and Standards - Discussion Log

> **Audit trail only.** Do not use as input to planning, research, or execution agents.
> Decisions are captured in CONTEXT.md — this log preserves the alternatives considered.

**Date:** 2026-04-19
**Phase:** 01-scaffold-and-standards
**Areas discussed:** Tag format, Category ordering, Inclusion criteria, Intro paragraph

---

## Tag Format

| Option | Description | Selected |
|--------|-------------|----------|
| Backtick code spans | `[Name](url) \`HW\` - Description.` | ✓ |
| Bold text | `[Name](url) **HW** - Description.` | |
| Plain brackets | `[Name](url) [HW] - Description.` | |

**User's choice:** Backtick code spans
**Notes:** Clean, renders as code, unlikely to conflict with awesome-lint

---

| Option | Description | Selected |
|--------|-------------|----------|
| All applicable tags | `\`HW\` \`FW\`` for dual-type projects | ✓ |
| Primary tag only | Pick most relevant | |
| Combined tag | `\`HW/FW\`` | |

**User's choice:** All applicable tags
**Notes:** Accurate, lets users filter by type

---

| Option | Description | Selected |
|--------|-------------|----------|
| HW/FW/SW only | Three tags only | ✓ |
| Add DOC tag | For documentation resources | |
| You decide | Claude's discretion | |

**User's choice:** HW/FW/SW only
**Notes:** Keep it minimal

---

## Category Ordering

| Option | Description | Selected |
|--------|-------------|----------|
| Signal flow order | Oscillators → Filters → VCAs... | ✓ |
| Alphabetical | Envelopes, Effects, Filters... | |
| By project count | Most-populated first | |

**User's choice:** Signal flow order
**Notes:** Mirrors how a patch is built, matches user mental model

---

| Option | Description | Selected |
|--------|-------------|----------|
| Names look good | Keep current names | ✓ |
| Rename some | Adjust names | |
| Add a category | Add missing function | |

**User's choice:** Names look good
**Notes:** Current category names accepted as-is

---

| Option | Description | Selected |
|--------|-------------|----------|
| After all module categories | Resources at end | |
| Interleaved | Dev Tools near modules, Communities at end | ✓ |
| Before module categories | Resources first | |

**User's choice:** Interleaved
**Notes:** Exact placement of each resource section left to Claude's discretion during planning

---

## Inclusion Criteria

| Option | Description | Selected |
|--------|-------------|----------|
| OSI-approved license required | Clear standard | |
| Any public source | Public repo counts | ✓ |
| Case by case | Flexible | |

**User's choice:** Any public source
**Notes:** More inclusive approach; project just needs publicly accessible source files

---

| Option | Description | Selected |
|--------|-------------|----------|
| Include if hardware files open | PCB/schematic public = include | ✓ |
| All files must be open | Hardware + firmware + software | |
| List with note | Include with partial tag | |

**User's choice:** Include if hardware files open
**Notes:** Hardware openness is the harder part to achieve

---

| Option | Description | Selected |
|--------|-------------|----------|
| Yes, include archived | Label as archived | ✓ |
| Active only | Recent commits only | |
| You decide | Claude's judgment | |

**User's choice:** Include archived
**Notes:** Historical projects remain valuable references

---

| Option | Description | Selected |
|--------|-------------|----------|
| Eurorack-compatible is enough | Works in Eurorack = include | |
| Eurorack-primary only | Designed for Eurorack specifically | ✓ |

**User's choice:** Eurorack-primary only
**Notes:** Must be designed for Eurorack (3U, ±12V, 3.5mm)

---

## Intro Paragraph

| Option | Description | Selected |
|--------|-------------|----------|
| Brief and factual | 1-2 sentences, assume reader knows Eurorack | |
| Welcoming and descriptive | 3-4 sentences, introduces Eurorack | ✓ |
| You decide | Claude's discretion | |

**User's choice:** Welcoming and descriptive
**Notes:** Welcomes newcomers to the format as well as experienced builders

---

| Option | Description | Selected |
|--------|-------------|----------|
| Yes, Awesome badge | Standard practice | ✓ |
| No | Keep minimal | |

**User's choice:** Yes
**Notes:** Required practice for awesome-list registry targeting

---

## Claude's Discretion

- Exact wording of intro paragraph and inclusion criteria section
- Interleaved placement of resource sections within TOC
- Whether to include a legend/key for HW/FW/SW tags

## Deferred Ideas

None — discussion stayed within Phase 1 scope.
