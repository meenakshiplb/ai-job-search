# Job Application Assistant

**name:** job-application-assistant
**description:** Assists with job applications: evaluating job postings, tailoring CVs, writing cover letters, and preparing for interviews. Triggers on keywords like: job posting, job application, CV, cover letter, resume, interview prep, job fit, career, application, apply
**allowed-tools:** Read, Glob, Grep, WebFetch, WebSearch, Edit, Write, AskUserQuestion

---

## Workflow

When the user provides a job posting (URL or text), follow this workflow:

### Step 1: Research & Evaluate Fit
- Fetch the job posting content (use WebFetch for URLs)
- Analyze the posting for required competencies, keywords, and priorities
- Research the company (website, LinkedIn, mission, recent news, kununu reviews)
- Score the posting against the candidate's profile using the framework in `04-job-evaluation.md`
- Present the evaluation table and verdict
- Ask the user if they want to proceed with an application

### Step 2: Tailor CV
- Read the most relevant existing CV variant from `cv/` as a starting point
- Follow the guidelines in `05-cv-templates.md`
- Create `cv/main_<company>.tex` with tailored content
- Adjust: profile statement, skills section, experience bullet emphasis, section order

### Step 3: Write Cover Letter
- Follow the writing style rules in `03-writing-style.md` (critical: no em-dashes, no cliches)
- Follow the template structure in `06-cover-letter-templates.md`
- Create `cover_letters/cover_<company>_<role>.tex`
- Language: match the job posting language (English for international tech companies is always acceptable in Vienna)

### Step 4: Interview Preparation
- Follow the framework in `07-interview-prep.md`
- Prepare STAR-format answers for likely questions
- Identify role-specific talking points
- Draft questions the candidate should ask the interviewer

---

## Reference Files

| File | Purpose |
|------|---------|
| `01-candidate-profile.md` | Education, experience, skills |
| `02-behavioral-profile.md` | Behavioral strengths and preferences |
| `03-writing-style.md` | Tone, structure, do's and don'ts |
| `04-job-evaluation.md` | Scoring framework for job fit |
| `05-cv-templates.md` | LaTeX CV structure and tailoring rules |
| `06-cover-letter-templates.md` | LaTeX cover letter structure |
| `07-interview-prep.md` | STAR examples, tough questions, roleplay guidelines |

---

## Quick Commands

- "Evaluate this job posting" — Step 1 only
- "Write a CV for [company]" — Step 2 only
- "Write a cover letter for [role] at [company]" — Step 3 only
- "Help me prepare for an interview at [company]" — Step 4 only
- "What jobs should I look for?" — Career strategy discussion
