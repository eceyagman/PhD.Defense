# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Writing Style Rules

**NEVER use em dashes (`---`).** Use commas, colons, semicolons, or periods instead. This applies to all LaTeX content, slide text, and any written output.

## Project Overview

Beamer LaTeX defense presentation for Ece Yagman's PhD thesis: "Socioemotional Skills in the Classroom: Measurement, Gender Dynamics, and Social Identity."

- **Main file:** `defense_presentation.tex`
- **Theme:** Boadilla + serif + HopBlue (#1A5C9A)
- **Repo:** `git@github.com:eceyagman/PhD.Defense.git`
- **Workflow:** User edits on Overleaf, Claude edits locally, GitHub syncs both directions

## Build

```bash
# Compile (requires pdflatex + bibtex; Overleaf handles this automatically)
pdflatex defense_presentation.tex
bibtex defense_presentation
pdflatex defense_presentation.tex
pdflatex defense_presentation.tex
```

## Slide Design Principles

- Slides are **cues for the speaker**, not a script
- Short bullet points, not full sentences
- Keep text minimal; let visuals and tables do the work
- Do not overcrowd slides with text

## Presentation Architecture

| Section | Slides | Content |
|---------|--------|---------|
| Introduction | 2–9 | Big picture → This thesis → Three chapters → Program → Five domains → RCT → Data |
| Chapter 1 | 10–16 | Treatment effects on classroom environment and student outcomes |
| Chapter 2 | 17–29 | Gender gaps in self-evaluation and peer evaluation (FF premium) |
| Chapter 3 | 30–39 | In-group favoritism and treatment effects on bias |
| Conclusion | 40–46 | Summary, contributions, policy, limitations, future work |
| Backup | appendix | Full tables, robustness, friendship mediation, attrition funnel, balance |

Bridge slides (16 and 29) connect chapters into a single argument about the evaluative environment.

## Key Files

| File | Purpose |
|------|---------|
| `defense_presentation.tex` | Main presentation (46 slides + backup appendix) |
| `paperpile.bib` | Bibliography (Paperpile export) |
| `figures/` | Presentation figures |
| `tables/` | LaTeX tables for backup slides |

## Citation Keys

Paperpile uses `AuthorYear-xx` format (e.g., `Heckman2012-nt`, `Steinberg2014-pe`). **Always verify keys exist in `paperpile.bib` before using them.** Common mistake: inventing keys like `kautz2014fostering` when the actual key is `Kautz2014-tm`.

## Custom LaTeX Commands

| Command | Usage |
|---------|-------|
| `\hlcoef{text}` | Highlight coefficients in HopBlue bold |
| `\pill{text}` | Rounded "pill" tag (e.g., "New since submitted version") |
| `\fadecolor{slide#}{text}` | Gray text that appears on specified slide |
| `\sym{stars}` | Significance stars in math/text mode |

## Core Findings (for accuracy when editing slides)

- **Ch.1:** Program transforms classroom environment (−42% discipline, +0.13–0.20 SD teacher perception). No short-run effects on SES or academics.
- **Ch.2 Self-eval:** Females underrate themselves, especially Emotional Management (−0.30 to −0.47 SD) and Thinking (−0.24 SD), conditional on ability.
- **Ch.2 Peer-eval:** Female-female premium β₃ = +0.24 to +0.43 SD. Male peers are gender-neutral. Female peers are strict toward males. This is a **POSITIVE** interaction, never describe as a penalty.
- **Ch.3:** Treatment compresses FF premium, significantly in Cooperation (FA: β₇ = −0.18*). Effects strongest in low-diversity classrooms.

## Sync Protocol

1. `git pull origin main` before starting edits (Overleaf may have changes)
2. Edit locally, verify changes
3. Show proposed edits to user before committing
4. `git push origin main` syncs back to Overleaf

## Related Projects

- **RCT.Pentabilities** (`/Users/eceyagman/Library/CloudStorage/Dropbox/GitHub/RCT.Pentabilities/cat/`) — Stata code, analysis, source tables/figures
- **Obsidian Vault** (`/Users/eceyagman/Library/CloudStorage/Dropbox/Obsidian/Vault/`) — Notes, session logs, Q&A prep

## Obsidian Vault Files

| File | Path | Purpose |
|------|------|---------|
| PhD Defense Presentation | `Inbox/PhD Defense Presentation.md` | Full slide-by-slide plan (46 slides, timing, visual cues). Source blueprint for `defense_presentation.tex` |
| PhD Defense Q&A Prep | `Inbox/PhD Defense Q&A Prep.md` | 34 prepared questions: 19 from external evaluator (Dr. Aurino), 15 jury, 4 cross-cutting themes |
| PhD Defense Prep | `Inbox/PhD Defense Prep.md` | Navigation hub linking to the presentation plan and Q&A prep |
| PhD project dashboard | `Projects/PhD.md` | High-level project dashboard linking all three papers and defense materials |

### Session Logs (CC-Logs)

| Date | File | Content |
|------|------|---------|
| 2026-02-20 | `2026-02-20-PhD-defense-prep.md` | Initial defense prep: 38 evaluator points mapped, Q&A created, slide plan drafted |
| 2026-02-25 | `2026-02-25-gender-defense-recovery.md` | Friendship integration into gender paper, defense backup slides prep |
| 2026-02-27 | `2026-02-27-defense-presentation.md` | Full 46-slide Beamer .tex created from MD plan |

## Session Memory

Session logs go to: `/Users/eceyagman/Library/CloudStorage/Dropbox/Obsidian/Vault/CC-Logs/`
