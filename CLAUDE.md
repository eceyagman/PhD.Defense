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

## RCT Design Details (from Paper 1, March 2026 version)

Source: "Teaching Practices, Behavioral Change, and Socio-Emotional Skill Formation" (Calsamiglia, De Giorgi, Navarro-Sola, Salvati, Yagman). Preliminary and incomplete, do not distribute. Presented at TrygFonden's Child Research Seminar (Aarhus), March 12, 2026.

### Intervention
- **Pentabilities:** Structured pedagogy for SEL. Trains and mentors teachers to embed SEL into daily instruction.
- Two core principles: (1) observable behaviors as proxies for latent skills, (2) evidence-based feedback (formative assessment)
- 35 target behaviors across 5 domains (Responsibility, Cooperation, Autonomy and Initiative, Emotional Management, Thinking Abilities)
- Operationalized via structured pedagogical cycles: plan activities targeting behaviors, observe/record via digital tools, provide feedback using dashboard, set goals for next cycle
- No new academic content, no additional instructional time, no changes to formal assessment
- Components: initial 8h training workshop (4h remote, 4h in-person), monthly 1-on-1 mentoring, 2 group sessions, digital platform access
- Training/mentoring delivered by Empieza por Educar (Teach for All), not involved in outcome measurement
- Components are bundled (not independently randomized), designed to be mutually reinforcing

### Experimental Design
- **Design:** Clustered RCT, 2022-2023 academic year, Catalonia (Spain)
- **Unit of randomization:** School-grade cluster (within school)
- **Schools:** 40 public and state-assisted secondary schools (39 in final analysis sample)
- **Requirement:** Each school contributes at least 2 grade levels (at least 1 treatment, 1 control)
- **Teacher constraint:** Teachers required to teach in only one participating grade (prevents cross-arm contamination)
- **Participation:** Voluntary at school and teacher levels. Teachers opted in by applying to implement.
- **Estimand:** Intention-to-treat (ITT) effect of assignment, regardless of realized take-up

### Recruitment and Sample Selection
- Recruited June-September 2022 via public outreach (newsletters, municipal/local education networks, referrals)
- Targeted schools serving socio-economically disadvantaged populations
- School eligibility also shaped by methodological needs (at least 2 grades, non-overlapping teacher sets)
- Teachers selected classrooms where they taught at least 3h/week, in a single subject or across multiple subjects

### Randomization and Stratification
- Random assignment conducted **after baseline data collection**, in late November 2022
- **Stratified by school disadvantage level**: four categories from an administrative composite index used by the Catalan education authority as a proxy for school-level socioeconomic disadvantage (footnote 7)
- Within each school, treatment randomly assigned among eligible grade clusters
- Treatment status disclosed to each school only after baseline data collection was finalized in that school

**Strata distribution (from treatment_assignment.csv):**

| Complexity (Catalan) | English | Schools | Control grades | Treatment grades | Total grades |
|---|---|---|---|---|---|
| Mitjana baixa | Low-Mid | 12 | 12 | 14 | 26 |
| Mitjana alta | High-Mid | 11 | 11 | 11 | 22 |
| Alta | High | 13 | 14 | 15 | 29 |
| Molt alta | Very High | 4 | 4 | 4 | 8 |
| **Total** | | **40** | **41** | **44** | **85** |

Distribution skews toward higher disadvantage (recruitment targeted disadvantaged schools). Every stratum has both T and C grades. School FE absorb strata FE because disadvantage category is school-level.

### Timeline
- **June-Sept 2022:** School recruitment
- **Nov 2022 - Jan 2023:** Baseline data collection (student/teacher surveys, in-class observations). Continued through January for some schools, but all collected prior to treatment disclosure.
- **Late November 2022:** Randomization conducted
- **December 2022:** Treatment teachers begin training
- **End of January 2023:** Initial training workshops completed
- **Jan/Feb - June 2023:** Program implementation (staggered start due to logistics)
- **Jan - May 2023:** External classroom observations (repeated, 4-6 visits per class)
- **March - April 2023:** Midline data
- **May - June 2023:** Endline data collection (surveys, standardized group activity, admin records)
- Control teachers offered training after end of study period

### Sample Numbers
- **Initial randomized sample:** 88 school-grade clusters, 4,763 students
- **Measurement sample:** 80 grades, 148 classrooms (budget constraint: outcome data on pre-specified subset of classroom groups within each cluster, selected before revealing treatment)
- **Analysis sample:** 2,068 students (40 T clusters: 69 classrooms, 1,015 students; 40 C clusters: 72 classrooms, 1,053 students)
- **Teachers:** 116 surveyed (68% female, 43% BA, 46% MA, experience ranges widely)
- **Students:** Ages 11-17, concentrated 12-14. 87% born in Spain, 61% both caregivers born in Spain
- Per grade: 2.7 classrooms on average (s.d. = 0.9), 2.3 participating teachers

### Consent and Attrition
- Parental consent required for individual-level survey and behavioral observations
- Consent collected prior to randomization for large majority
- No statistically significant difference in consent rates across treatment arms
- Attrition after consent (survey non-response, student absence) is low and balanced
- Balance tests among consented students show no systematic differences

### Identification and Estimation
- ANCOVA framework: y_igs = alpha + beta*T_gs + gamma*y_igs0 + delta_s + eta_g + lambda^w + v_k*x^k_igs0 + epsilon_igs
- School FE (delta_s), strata FE (eta_g, by school disadvantage level), week-of-measurement FE (lambda^w)
- Pre-specified individual socio-demographic covariates + baseline variables with imbalance
- Observer FE for all external-observer-based outcomes
- SEs clustered at school-grade level (unit of randomization)
- MHT corrections: sharpened FDR q-values within pre-specified outcome families
- Teacher outcomes analyzed at teacher level; student perception outcomes aggregated to teacher level

### Spillover
- Design limits but does not eliminate spillover: randomization at grade-within-school, teachers teach only one grade
- Core intervention components (platform, mentoring, training) accessible only to treated teachers
- Informal teacher interactions within school cannot be ruled out
- Any remaining spillovers would attenuate ITT estimates toward zero (conservative)

### Data Sources
1. **Student/teacher surveys:** Administered by external survey firm using tablets (Catalan or Spanish). Baseline, midline, endline.
2. **Classroom observations (CO):** Trained external observers (hired by Empieza por Educar), blind to treatment, identical protocols in T and C. 35 behaviors rated. Repeated Jan-May 2023.
3. **Standardized group activity (FA):** One-hour endline group task outside regular classroom. External observers rate 20 behaviors on 5-point scale. Students also do self- and peer-assessments.
4. **Administrative records:** Attendance (21/40 schools) and term grades (31/40 schools). Incomplete coverage.
5. **TROS (Teacher Roles Observation Schedule):** External observers record teacher-student interactions at 5-min intervals. 6 outcomes across 3 dimensions: instructional organization, interaction style, regulation of learning/behavior.
6. **Teacher time use:** Self-reported weekly hours on instructional activities.
7. **Implementation data (T only):** EdTech logs, mentoring reports.

### Outcome Construction
- Domain-specific indices: unweighted mean of standardized components (standardized to control group mean and SD at baseline when available, endline otherwise)
- Indices re-standardized to mean zero, unit variance in control group
- Primary outcomes: behavior-based measures from external observations (CO and FA)
- Secondary outcomes: BESSI survey, admin records, teacher practices

### Key Heterogeneity Dimension
- SES heterogeneity pre-specified in PAP (funder: Spanish Ministry of Social Inclusion)
- Household-level SES index from student survey data (captures within-school variation)
- Three groups in Figure 1: "SES index: 1-6," "SES index: 7," "SES index: 8"
- Two complementary dimensions also pre-specified: (1) school-level disadvantage indicators (administrative), (2) caregiver immigration background

## Core Findings (for accuracy when editing slides)

### Ch.1 Results (Paper 1)
- **Average effects on SES:** Close to zero across all 5 domains in both FA and CO settings. None significant after MHT.
- **SES gradient:** Clear monotonic gradient: effects largest for disadvantaged students (0.1-0.5 SD), declining with SES advantage, close to zero or negative for high-SES. Most pronounced for autonomy and responsibility. Most remain significant after MHT.
- **Baseline skills heterogeneity:** Similar pattern by baseline social engagement and emotional management.
- **Individual behaviors:** Effects not driven by single behavior. Concentrated in emotional regulation, interaction/participation, and task engagement. Higher-order reflective/abstract thinking slightly negative.
- **BESSI (survey):** Innovation +0.094 SD*** (only significant domain). Social engagement +0.039*. Self-management, cooperation, emotional management: null.
- **Instructional practices (TROS):** More whole-class instruction (+12pp), more interactive style (+7.8pp**), less correcting student behavior (-8.1pp**). No change in content-focused instruction, motivational support, or student agency encouragement.
- **Practice heterogeneity by classroom SES:** High-disadvantage classrooms: shift instructional mode (less content-focused, more interactive). Low-disadvantage classrooms: shift regulation (more student agency +13.2pp, more motivational support +18.1pp, less correction -17.5pp).
- **Student perceptions:** Treated students report improved practices (+0.16 SD**). Gains concentrated among disadvantaged students (individualized attention, whole-class effort).
- **Teacher time use:** Only significant change: less time addressing disciplinary issues (-0.64h/week**). No change in total time or other activities.
- **Downstream academics:** No average effects. Low-SES: fewer absences (-2.3 days, ~17% reduction), no grade change. High-SES: GPA +0.075 SD**, attendance weakly declines (unjustified absences). Interaction Treated x Low SES significant for both GPA (-0.10**) and absences (-3.84***).
- **Ch.2 Self-eval:** Females underrate themselves, especially Emotional Management (−0.30 to −0.47 SD) and Thinking (−0.24 SD), conditional on ability.
- **Ch.2 Peer-eval:** Female-female premium β₃ = +0.24 to +0.43 SD. Male peers are gender-neutral. Female peers are strict toward males. This is a **POSITIVE** interaction, never describe as a penalty.
- **Ch.3:** Treatment compresses FF premium, significantly in Cooperation (FA: β₇ = −0.18*). Effects strongest in low-diversity classrooms.

## Coauthor Presentation Flow (inspiration for defense slides)

The TrygFonden presentation (March 2026) uses this structure, useful as reference for slide flow:
1. Motivation: Teachers shape skills beyond achievement, but how? (identification issue)
2. Research question + measurement challenge
3. This paper: Clustered RCT + multi-method measurement
4. Findings preview (3 bullets: null averages/heterogeneity, instructional practices, asymmetric downstream)
5. Contributions to literature (3 margins)
6. **Section divider:** Program description and experimental design
7. Pentabilities program (structured pedagogy, 2 principles, professional development)
8. Targets observable behaviors (35 behaviors x 5 domains)
9. Evidence-based feedback cycle (plan, observe, feedback)
10. EdTech integration (mobile app, dashboard screenshots)
11. Experimental design slide (sample frame, randomization details)
12. Outcomes and data sources (outputs vs inputs)
13. Sample characteristics (schools, teachers, students, balance)
14. Econometric specification (ANCOVA equation)
15. **Section divider:** Impacts on SES formation
16. Results slides with tables and figures

## Sync Protocol

1. `git pull origin main` before starting edits (Overleaf may have changes)
2. Edit locally, verify changes
3. Show proposed edits to user before committing
4. `git push origin main` syncs back to Overleaf

## Directory Structure

- **Output (this repo):** `/Users/eceyagman/Library/CloudStorage/Dropbox/GitHub/PhD.Defense/` — Beamer .tex, final figures/tables, bib. All presentation edits happen here.
- **Input:** `/Users/eceyagman/Library/CloudStorage/Dropbox/GitHub/RCT.Pentabilities/cat/` — Stata do-files, source figures, source tables, papers, previous presentations. Read from here for coefficients, analysis logic, and raw materials.
- **Obsidian Vault:** `/Users/eceyagman/Library/CloudStorage/Dropbox/Obsidian/Vault/` — Notes, session logs, Q&A prep

When generating new figures or tables, output goes to `PhD.Defense/figures/` or `PhD.Defense/tables/`. When looking up coefficients, do-file logic, or source materials, read from `RCT.Pentabilities/cat/`.

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
