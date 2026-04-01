# Nokta — Community-Driven mobile.md

> 1 file, 0 human review. CI decides.

## What?

`mobile.md` is the Karpathy-style spec file for the Nokta mobile app. This file serves as a complete specification from which AI agents (Claude Code / Codex) can build the application from scratch.

**Humans write the spec, machines write the code.**

## How It Works?

```
Pick a section
    ↓
Open a branch: section/04-data-contracts
    ↓
Write the relevant section in mobile.md
    ↓
Open a PR
    ↓
CI scores automatically (0-100)
    ↓
Score ≥ current score on main → ✅ Auto-merge
Score < current score on main → ❌ Auto-reject
    ↓
Fix, push, try again
```

**No human review. The metric decides. Score never drops.**

## Quick Start

```bash
# 1. Fork or clone the repo
git clone https://github.com/seyyah/nokta.git
cd nokta

# 2. Create a branch (choose your section number)
git checkout -b section/04-data-contracts

# 3. Open mobile.md, find your section, write it
# Each section has <!-- COMMENT --> instructions inside

# 4. Check your score (optional, local test)
pip install pyyaml
python scripts/section_score.py --section 4

# 5. Commit + push
git add mobile.md
git commit -m "feat(section-04): add data contracts"
git push origin section/04-data-contracts

# 6. Open a PR on GitHub → CI runs automatically → wait for result
```

## Section List

| # | Section | Contents |
|---|---------|----------|
| 0 | IMMUTABLE INFRA | List of files that must not be modified |
| 1 | IDENTITY | ✅ Already complete — use as reference |
| 2 | SETUP PROTOCOL | Setup steps from zero to running app |
| 3 | NON-GOALS | What will not be built in v0.1 |
| 4 | DATA CONTRACTS | TypeScript interfaces and storage schema |
| 5 | SCREEN & FEATURE SPEC | 3 screens, UX flow, component list |
| 6 | UI CONFIG | Local JSON-driven UI config system |
| 7 | LLM CONTRACT | Mock LLM, prompt template, golden transcripts |
| 8 | OBJECTIVE FUNCTION | Hard gates + single scalar metric |
| 9 | THE RATCHET LOOP | PR → CI → measure → keep/revert cycle |
| 10 | CONTRIBUTION PROTOCOL | Branch, commit, PR rules |
| 11 | ARCHITECTURAL INVARIANTS | Code structure rules |
| 12 | TESTING PHILOSOPHY | Test standards and anti-patterns |

## Scoring

Each section has a checklist (`checklists/section_XX.yml`). CI reads this checklist and evaluates the section:

- **Structural checks:** Are required headings present? Is the minimum word count met?
- **Content checks:** Are specific concepts/patterns present? (e.g. TypeScript code block, JSON schema)
- **Each check carries a weight.** Scored out of 100 points.

**Scoring rule:** Your score cannot drop below the current score on the main branch. Equal or higher means you merge.

### Test Locally

```bash
# Single section
python scripts/section_score.py --section 4

# All sections
python scripts/section_score.py --all

# CI-formatted output
python scripts/section_score.py --all --ci-comment
```

## Rules

1. **Only edit `mobile.md`.** Do not edit checklist YAMLs, the CI workflow, or scripts — these are IMMUTABLE INFRA.
2. **Section 1 (IDENTITY) is already complete.** Use it as a reference and follow its format.
3. **Multiple people can write the same section.** The highest score gets merged.
4. **Delete TODO placeholders.** As long as `> TODO:` lines remain, the section score stays low.
5. **AI tools are welcome** — vibe-writing is fine. But you still need to pass the checklist.
6. **English or Turkish** — both are supported by the checklist.

## FAQ

**Q: What if someone else is writing the same section?**
First to merge wins. The next PR must beat that score. Ratchet.

**Q: My PR was rejected — what should I do?**
Read the CI comment — it will show which checklist items failed. Fix them, push, and CI runs again.

**Q: Section 1 is already complete — can I improve it?**
Yes — but you need to beat its current score (100/100). Delete content and the score drops; you'll be rejected.

**Q: Can I contribute to multiple sections?**
Yes — each in its own branch + its own PR.
