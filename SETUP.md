# Setup Guide — AI Job Search (Vienna Edition)

## Prerequisites

### 1. Claude Code CLI
Make sure you have Claude Code installed:
```bash
claude --version
```
If not: https://claude.ai/claude-code

### 2. LaTeX Distribution
Required to compile CV and cover letters.

**macOS:**
```bash
brew install --cask mactex
```

**Ubuntu/Debian:**
```bash
sudo apt-get install texlive-full
```

**Windows:** Install MiKTeX from https://miktex.org/

After installation, verify:
```bash
lualatex --version
xelatex --version
```

### 3. OpenFonts for Cover Letters
The cover letter template requires Lato + Raleway fonts. Get them by cloning the original repo:

```bash
git clone https://github.com/MadsLorentzen/ai-job-search /tmp/source-repo
cp -r /tmp/source-repo/cover_letters/OpenFonts/ cover_letters/OpenFonts/
rm -rf /tmp/source-repo
```

Without this step, the cover letter will not compile. The CV (LaTeX moderncv) does not need these fonts.

---

## Quickstart

### Step 1: Navigate to this folder
```bash
cd "/path/to/Job search/ai-job-search"
```

### Step 2: Launch Claude Code
```bash
claude
```

### Step 3: Run /setup to fill in your profile
```
/setup
```

This will interview you (or read your documents folder) and populate:
- Your full profile in `CLAUDE.md` and the 7 skill files
- Your CV template `cv/main_example.tex`
- Your search queries in `.claude/skills/job-scraper/search-queries.md`

> **Tip:** Drop your existing CV, LinkedIn export, or other documents in `documents/cv/` and `documents/linkedin/` before running `/setup`. Path A will read them automatically.

### Step 4: Search for jobs
```
/scrape
```

This searches Austrian and European job boards using your configured queries and presents results sorted by estimated fit.

### Step 5: Apply to a job
```
/apply https://karriere.at/job/123456
```

Or paste a job posting directly:
```
/apply [paste the full job description here]
```

This triggers the full drafter-reviewer workflow: fit evaluation, CV tailoring, cover letter drafting, reviewer critique, revision, PDF compilation, and verification checklist.

---

## File Structure

```
ai-job-search/
├── CLAUDE.md                          # Your profile + workflow rules
├── SETUP.md                           # This file
├── job_search_tracker.csv             # Application log
├── .claude/
│   ├── commands/
│   │   ├── apply.md                   # /apply workflow
│   │   ├── setup.md                   # /setup onboarding
│   │   └── scrape.md                  # /scrape job search
│   └── skills/
│       ├── job-application-assistant/ # Core application skill (7 files)
│       └── job-scraper/
│           └── search-queries.md      # Vienna/Europe search queries
├── cv/
│   ├── main_example.tex               # Master CV template (lualatex)
│   └── main_<company>.tex             # Generated per-application (by /apply)
├── cover_letters/
│   ├── cover.cls                      # Cover letter class (xelatex)
│   ├── OpenFonts/                     # Lato + Raleway fonts (see above)
│   └── cover_<company>_<role>.tex     # Generated per-application (by /apply)
├── documents/
│   ├── cv/                            # Drop your CV here for /setup Path A
│   └── linkedin/                      # Drop LinkedIn export here
└── job_scraper/
    ├── results.md                     # Search results log
    └── seen_jobs.md                   # Deduplication log
```

---

## Vienna Market Notes

### Salary Transparency
Austrian law requires job ads to disclose the **Kollektivvertrag (KV) minimum salary**. This is the legal floor — the actual offer is almost always negotiable above it. Use the disclosed KV minimum as a negotiation anchor, not a target.

### Language
Most international tech companies in Vienna (Dynatrace, Tricentis, N26, George/Erste Group, etc.) operate in English. English-language applications are standard and expected. German-language cover letters are only necessary for Austrian-only companies or public sector roles.

### Key Portals
- **karriere.at** — Austria's largest, use this first
- **stepstone.at** — Second most important
- **xing.com** — DACH professional network (important alongside LinkedIn)
- **kununu.com** — Austria's employer review platform (check before applying)
- **willhaben.at** — More SME-focused but worth checking

### Updating Search Queries
As your priorities evolve:
```
/setup --section search
```

This re-runs just the search configuration interview without touching your profile.
