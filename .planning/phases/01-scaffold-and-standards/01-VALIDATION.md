---
phase: 1
slug: scaffold-and-standards
status: draft
nyquist_compliant: false
wave_0_complete: false
created: 2026-04-19
---

# Phase 1 — Validation Strategy

> Per-phase validation contract for feedback sampling during execution.

---

## Test Infrastructure

| Property | Value |
|----------|-------|
| **Framework** | npx awesome-lint + npx markdownlint-cli2 (no test runner — linters are the test suite) |
| **Config file** | `.markdownlint-cli2.jsonc` (Wave 0 creates it) |
| **Quick run command** | `npx awesome-lint README.md` |
| **Full suite command** | `npx awesome-lint README.md && npx markdownlint-cli2 README.md` |
| **Estimated runtime** | ~10 seconds |

---

## Sampling Rate

- **After every task commit:** Run `npx awesome-lint README.md`
- **After every plan wave:** Run `npx awesome-lint README.md && npx markdownlint-cli2 README.md`
- **Before `/gsd-verify-work`:** Full suite must be green
- **Max feedback latency:** 10 seconds

---

## Per-Task Verification Map

| Task ID | Plan | Wave | Requirement | Threat Ref | Secure Behavior | Test Type | Automated Command | File Exists | Status |
|---------|------|------|-------------|------------|-----------------|-----------|-------------------|-------------|--------|
| 1-01-01 | 01 | 0 | STRC-01 | — | N/A | lint | `npx awesome-lint README.md` | ❌ W0 | ⬜ pending |
| 1-01-02 | 01 | 1 | STRC-02 | — | N/A | lint | `npx awesome-lint README.md` | ❌ W0 | ⬜ pending |
| 1-01-03 | 01 | 1 | STRC-03 | — | N/A | lint | `test -f LICENSE && head -1 LICENSE` | ❌ W0 | ⬜ pending |
| 1-01-04 | 01 | 1 | STRC-04 | — | N/A | lint | `npx awesome-lint README.md` | ❌ W0 | ⬜ pending |
| 1-01-05 | 01 | 1 | STRC-05 | — | N/A | lint | `npx awesome-lint README.md` | ❌ W0 | ⬜ pending |
| 1-01-06 | 01 | 1 | STRC-06 | — | N/A | manual | See manual verifications | ❌ W0 | ⬜ pending |
| 1-01-07 | 01 | 1 | STRC-07 | — | N/A | manual | See manual verifications | ❌ W0 | ⬜ pending |
| 1-01-08 | 01 | 2 | QUAL-03 | — | N/A | lint | `npx awesome-lint README.md && npx markdownlint-cli2 README.md` | ❌ W0 | ⬜ pending |

*Status: ⬜ pending · ✅ green · ❌ red · ⚠️ flaky*

---

## Wave 0 Requirements

- [ ] `README.md` — minimal skeleton to validate empty-section behavior (Assumption A1)
- [ ] `LICENSE` — CC0-1.0 text file
- [ ] `.markdownlint-cli2.jsonc` — config disabling MD013, MD033
- [ ] Run `npx awesome-lint README.md` against minimal skeleton to determine if empty sections fail

*Wave 0 resolves Assumption A1 before main scaffold work begins.*

---

## Manual-Only Verifications

| Behavior | Requirement | Why Manual | Test Instructions |
|----------|-------------|------------|-------------------|
| TOC links navigate to correct sections | STRC-02 | GitHub anchor rendering requires browser verification | Open README.md on GitHub (or local preview), click each TOC link, verify scroll target is correct section heading |
| Inclusion criteria section is clear and complete | STRC-06 | Content quality judgment — not automatable | Read inclusion criteria section: verify open source threshold (any public GitHub repo), partially open policy, archived repo policy, and Eurorack-primary scope are all documented |
| Entry format example is correct and demonstrates all tag types | STRC-07 | Format correctness beyond regex | Verify at least one example entry using `[Name](url) \`HW\` \`FW\` - Description.` pattern is present and syntactically correct |

---

## Validation Sign-Off

- [ ] All tasks have `<automated>` verify or Wave 0 dependencies
- [ ] Sampling continuity: no 3 consecutive tasks without automated verify
- [ ] Wave 0 covers all MISSING references
- [ ] No watch-mode flags
- [ ] Feedback latency < 10s
- [ ] `nyquist_compliant: true` set in frontmatter

**Approval:** pending
