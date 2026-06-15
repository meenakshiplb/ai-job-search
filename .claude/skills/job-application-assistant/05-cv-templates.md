# CV Templates and Tailoring Guide

## Template: LaTeX moderncv (Banking Style)

All CVs use the moderncv LaTeX package with the "banking" style and "blue" color scheme.

**Output file:** `cv/main_<company>.tex`
**Compile with:** **lualatex** on MiKTeX/TeX Live.
**Master reference:** `cv/main_example.tex`

### Compile command
```bash
cd cv && lualatex -interaction=nonstopmode main_<company>.tex
```

Expected output: `Output written on main_<company>.pdf (2 pages, ...)`. Any other page count is a failure.

## Document Structure

```latex
\documentclass[11pt,a4paper,sans]{moderncv}
\moderncvstyle{banking}
\moderncvcolor{blue}

\renewcommand*{\firstnamestyle}[1]{{\fontsize{34}{36}\bfseries\upshape\color{color1}#1}}
\renewcommand*{\lastnamestyle}[1]{{\fontsize{34}{36}\bfseries\upshape\color{color1}#1}}
\renewcommand*{\sectionstyle}[1]{{\sectionfont\color{color1}#1}}

\usepackage[utf8]{inputenc}
\usepackage{hyperref}
\hypersetup{colorlinks=true, linkcolor=blue, filecolor=magenta, urlcolor=blue,
    pdftitle={Meenakshi - CV}, pdfpagemode=FullScreen}
\usepackage[scale=0.77]{geometry}
\usepackage{import}

\name{Meenakshi}{[Last Name]}
\address{Vienna, Austria}{}{}
\phone[mobile]{[Your Phone]}
\email{meenuplb@gmail.com}
\extrainfo{\href{[LinkedIn URL]}{LinkedIn}}

\begin{document}
\makecvtitle
% 1. Profile statement
% 2. Skills section
% 3. Professional Experience
% 4. Education
% 5. Languages
% 6. References
\end{document}
```

## Profile Statement Templates

**For Senior Java / Backend Engineering roles:**
> Senior software engineer with 10+ years of hands-on experience in Java backend development and REST API design. Proven track record at Broadcom delivering production systems within Agile/Scrum teams, including sprint facilitation, on-call operations, and cross-functional delivery. Combines strong engineering fundamentals with a collaborative, ownership-driven approach.

**For AI Engineer / ML transition roles:**
> Senior software engineer with 10+ years of Java and REST API experience, actively transitioning into AI engineering. Production background in delivering reliable backend systems; currently building applied ML skills in [add specific tools]. Brings engineering rigour, Agile delivery experience, and a practitioner's instinct for building things that work at scale.

**For Product Owner / Technical Lead roles:**
> Senior engineer with 10+ years in Java/REST development and strong Agile delivery ownership. Experienced in sprint planning, story grooming, bug triage, and standup facilitation — bridging engineering and product decision-making. Combines technical depth with communication skills that translate complex requirements into actionable engineering work.

## Section-by-Section Tailoring

### Core Competencies / Skills
Reorder and emphasize based on the role. Use bold category labels. 5-7 competencies, each explained with value-add.

### Professional Experience
- 4-6 bullets for most recent role, 3-4 for previous, 2-3 for older
- Emphasize measurable results: "Reduced X by Y%", "System adopted by Z teams"
- On-call/operational reliability bullets are differentiators — include them

### Handling No Formal CS Degree
Do NOT hide this. Instead:
- Never lie about having a degree
- Frame experience section to show depth and progression
- Add a line in the profile statement: "...built through 10+ years of applied engineering, not formal academic training" — this frames the narrative before a recruiter notices it

### Page Budget — Hard 2-Page Limit
| Section | Max budget |
|---------|-----------|
| Profile statement | 3-4 lines |
| Skills | 5 items, each 1-2 lines |
| Most recent role | 4-5 bullets |
| Previous role | 2-3 bullets |
| Older roles | 2 bullets each |
| Education | 2-3 entries |
| Languages | 1 line |
| References | "Available upon request." |

## Spacing inside itemize lists (important)
Do NOT place `\vspace{...}` between `\item` entries. Use `\vspace{3pt}` between `\cventry` blocks only.

## Compile-and-Inspect Loop (MANDATORY)
1. Run lualatex
2. Check page count: must be exactly 2
3. Read PDF via Read tool — check for orphaned `\cventry` titles
4. Fix with `\needspace{5\baselineskip}` before problematic entries
5. If spilling to page 3: use `\enlargethispage{2-3\baselineskip}` or cut content by relevance

## Recommended Section Order (for Java/Backend/AI roles)
1. Profile statement
2. Core Competencies / Skills
3. Professional Experience (reverse chronological)
4. Education
5. Languages
6. References
