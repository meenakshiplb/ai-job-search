# /apply - Drafter-Reviewer Job Application Workflow

You are orchestrating a two-agent job application workflow. The job posting is provided below as `$ARGUMENTS` (either a URL or pasted text).

Follow these steps **exactly in order**. Do not skip steps.

**Token-efficiency rules:**
- Never re-Read a file already in your context from an earlier step.
- When dispatching the reviewer agent, pass draft content **inline in the agent prompt**.
- Run the full verification checklist exactly once, at the end (Step 6).
- Step 5 (compile and inspect PDFs) is mandatory and non-skippable.

---

## Step 0: Parse Input

- If `$ARGUMENTS` looks like a URL, use `WebFetch` to retrieve the job posting content.
- If it is pasted text, use it directly.
- Extract: **company name**, **role title**, **department** (if mentioned), **location**, and **language** of the posting.
- Store these for use throughout the workflow.

---

## Step 1: DRAFTER - Evaluate Fit

Read the evaluation framework:
- `.claude/skills/job-application-assistant/04-job-evaluation.md`
- `.claude/skills/job-application-assistant/01-candidate-profile.md`

Also research the company via WebSearch/WebFetch. Check:
- Company website (mission, products, recent news)
- kununu.com reviews (Austria-specific employer review platform — more relevant than Glassdoor for Austrian companies)
- LinkedIn for team size and recent hires

Evaluate the job posting against the candidate's profile using the framework. Present the evaluation to the user with:

1. **Skills match** — which required/preferred skills match vs. gaps
2. **Experience match** — how work history maps to the role
3. **Behavioral/culture match** — how behavioral profile fits
4. **Location/logistics** — Vienna or remote Europe?
5. **Career alignment** — does this advance the stated career goals?
6. **Overall fit score** and recommendation (strong fit / moderate fit / weak fit)

After presenting the evaluation, ask the user:
> "Should I proceed with drafting the CV and cover letter for this role?"

**If the user says no, stop here.** If yes, continue to Step 2.

---

## Step 2: DRAFTER - Draft CV + Cover Letter

You already have `01-candidate-profile.md` and `04-job-evaluation.md` in context from Step 1. **Do not re-read them.**

Read only the reference files you do not yet have:
- `.claude/skills/job-application-assistant/03-writing-style.md`
- `.claude/skills/job-application-assistant/05-cv-templates.md`
- `.claude/skills/job-application-assistant/06-cover-letter-templates.md`

Also read the most recent existing CV and cover letter files for concrete structural reference:
- Read any existing `cv/main_*.tex` file as a LaTeX template reference
- Read any existing `cover_letters/cover_*.tex` file as a template reference

### CV (`cv/main_<company>.tex`)
- Always in **English**
- Follow the moderncv/banking format from `05-cv-templates.md`
- Tailor the profile statement and experience bullets to the specific role
- Keep to 2 pages

### Cover Letter (`cover_letters/cover_<company>_<role>.tex`)
- **Match the language of the job posting** (for international tech companies in Vienna, English is always acceptable)
- Follow the structure from `06-cover-letter-templates.md`
- Use the `cover.cls` template
- Address to a named person if available, otherwise "Dear Hiring Manager"
- Keep to approximately one page

Write both files to disk. Keep the exact text of both drafts in working memory — you will pass them inline to the reviewer in Step 3.

---

## Step 3: REVIEWER - Research & Critique

Use the **Agent tool** to spawn a `general-purpose` reviewer agent. Pass the drafts **inline in the prompt**. Replace `<COMPANY>`, `<ROLE>`, and the draft placeholders with actual values.

```
You are a hiring manager proxy reviewing a job application for a Senior Software Engineer role in Vienna, Austria.

## Your Tasks

### 1. Research the Company
Use WebSearch and WebFetch to research:
- The company's website, mission, and recent news
- The specific department or team (if mentioned in the posting)
- Any recent projects, press releases, or strategic initiatives relevant to the role
- kununu.com reviews (Austria's primary employer review platform)
- Company culture and values

### 2. Read Reference Materials (content-critique only)
Read these four files only:
- `.claude/skills/job-application-assistant/01-candidate-profile.md`
- `.claude/skills/job-application-assistant/02-behavioral-profile.md`
- `.claude/skills/job-application-assistant/03-writing-style.md`
- `.claude/skills/job-application-assistant/04-job-evaluation.md`

Do NOT read files 05 or 06.

### 3. Drafts to Review
<CV_DRAFT file="cv/main_<COMPANY>.tex">
<INSERT_CV_DRAFT_HERE>
</CV_DRAFT>

<COVER_LETTER_DRAFT file="cover_letters/cover_<COMPANY>_<ROLE>.tex">
<INSERT_COVER_LETTER_DRAFT_HERE>
</COVER_LETTER_DRAFT>

### 4. Job Posting
<JOB_POSTING>
<INSERT_JOB_POSTING_TEXT_HERE>
</JOB_POSTING>

### 5. Produce Feedback

Return your feedback in two parts:

**Part A — Structured edits (JSON array):**
```json
{
  "file": "cv/main_<COMPANY>.tex" | "cover_letters/cover_<COMPANY>_<ROLE>.tex",
  "old_string": "<exact text currently in the draft>",
  "new_string": "<replacement text>",
  "reason": "<one-line rationale>"
}
```

**Part B — Narrative suggestions (for judgment calls):**
- **Missed keywords/requirements**
- **Company/department-specific angles** (based on your research)
- **Action-oriented reframing** (passive or generic phrasing to fix)
- **Tone and style issues** (check against writing style guide AND behavioral profile)

**CRITICAL:** All suggestions must be grounded in actual profile data. Do NOT suggest fabricating skills or experience.
```

---

## Step 4: DRAFTER - Revise Based on Feedback

1. **Apply Part A (structured edits) directly with the Edit tool.** Skip any whose rationale would require fabricating content.
2. **Apply Part B (narrative suggestions)** using judgment:
   - **Missed keywords:** add where they fit naturally
   - **Company-specific angles:** weave reviewer's research into the cover letter — verify every company claim via WebFetch/WebSearch before including it
   - **Action-oriented reframing:** rewrite passive or generic phrasing
   - **Tone and style issues:** fix per the writing style guide (no em-dashes, no cliches, confident first-person active voice)
3. Do NOT incorporate any suggestion that would fabricate skills or experience.

---

## Step 5: DRAFTER - Compile & Inspect PDFs (MANDATORY)

### 5a. Compile
```bash
cd cv && lualatex -interaction=nonstopmode main_<company>.tex
cd ../cover_letters && xelatex -interaction=nonstopmode cover_<company>_<role>.tex
```

- CV uses **lualatex**
- Cover letter uses **xelatex** (cover.cls requires fontspec)

Fix any compile errors and re-compile until clean.

### 5b. Inspect layout

Read both PDFs via the Read tool and verify:

**CV:**
- [ ] Exactly 2 pages
- [ ] No orphaned `\cventry` titles
- [ ] No awkward whitespace gaps

**Cover letter:**
- [ ] Exactly 1 page
- [ ] Signature block visible
- [ ] Bullet list font matches body text (both Raleway-Medium)

### 5c. Iterate until clean
- **Orphaned CV entry title:** add `\needspace{5\baselineskip}` before the problematic `\cventry` (and `\usepackage{needspace}` in preamble)
- **CV spills to page 3:** cut by relevance-weighted scoring (see `05-cv-templates.md`)
- **Cover letter itemize font issue:** close `\lettercontent{}` before the list, wrap list in `{\raggedright\fontspec[Path = OpenFonts/fonts/raleway/]{Raleway-Medium}\fontsize{11pt}{13pt}\selectfont \begin{itemize}...\end{itemize}\par}`
- **Cover letter spills to 2 pages:** trim — first cut sentences that restate bullets; last resort: cut a bullet

### 5d. Clean up build artifacts
Delete `.aux`, `.log`, `.out` files after final clean compile.

---

## Step 6: Present Final Output

Run the full verification checklist from `CLAUDE.md`.

### Verification Checklist
Report pass/fail for each item (factual accuracy, targeting, consistency, quality).

### Key Tailoring Decisions
Summarize 3-5 key decisions made to tailor the application.

### Files Created
- `cv/main_<company>.tex` + `.pdf`
- `cover_letters/cover_<company>_<role>.tex` + `.pdf`

Tell the user: "Both files are ready. Open them to check the final output before submitting."

### Job Tracker
Ask the user if they want to log this application in `job_search_tracker.csv`. If yes, append a row with: date, company, sector, role, channel, status (Applied), fit_rating, cv_file, cover_letter_file.
