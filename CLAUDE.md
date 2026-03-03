# CLAUDE.md — PhD Defense Presentation

## Writing Style Rules

**NEVER use em dashes (`---` or `—`).** Use commas, colons, semicolons, or periods instead. This applies to all LaTeX content, slide text, and any written output.

**No AI filler words.** Never use "notably," "crucially," "striking," "intriguingly," "furthermore," "moreover." These signal AI-generated text.

**No hedging.** Say "X predicts Y" not "X might suggest Y." You are defending your own work; speak with confidence.

**Precise framing.** Positive interaction = "premium," never "gap" or "penalty." Match claim to evidence exactly.

**Magnitudes over significance.** Report effect sizes ("0.35 SD"), not just "significant."

**No self-praise filler.** Avoid "novel," "unique," "first-of-its-kind" more than once in the entire presentation. Let the work speak.

**Style model:** Alesina, Carlana, La Ferrara, and Pinotti (2024, AER). Concise, evidence-driven, articulate. Every word earns its place, but the prose flows and builds an argument.

## Slide Design Principles

- Slides are **cues for the speaker**, not a script
- Short bullet points, not full sentences
- Keep text minimal; let visuals and tables do the work
- Do not overcrowd slides with text
- **Finding first, mechanism second**: lead with the result, then explain why
- Core results on main slides; robustness, alternative specs, additional outcomes in backup appendix

## Interaction Model Discipline

In `Y = β₁X + β₂Z + β₃(X×Z)`, main effects are conditional on the other variable = 0. Never describe β₁ as "the effect of X" without specifying "when Z=0."

## Project Overview

This is a Beamer LaTeX defense presentation for Ece Yagman's PhD thesis: "Socioemotional Skills in the Classroom: Measurement, Gender Dynamics, and Social Identity."

- **Main file:** `defense_presentation.tex`
- **Theme:** Boadilla + serif + HopBlue (#1A5C9A)
- **Repo:** `git@github.com:eceyagman/PhD.Defense.git`
- **Workflow:** User edits on Overleaf, Claude edits locally, GitHub syncs both directions

## Key Files

| File | Purpose |
|------|---------|
| `defense_presentation.tex` | Main presentation (46 slides + backup appendix) |
| `paperpile.bib` | Bibliography |
| `figures/` | All presentation figures |
| `tables/` | LaTeX tables for backup slides |

## Related Projects

- **RCT.Pentabilities** (`/Users/eceyagman/Library/CloudStorage/Dropbox/GitHub/RCT.Pentabilities/cat/`) — Stata code, analysis, source tables/figures
- **Obsidian Vault** (`/Users/eceyagman/Library/CloudStorage/Dropbox/Obsidian/Vault/`) — Notes, session logs, Q&A prep

## Session Memory

Session logs go to: `/Users/eceyagman/Library/CloudStorage/Dropbox/Obsidian/Vault/CC-Logs/`
