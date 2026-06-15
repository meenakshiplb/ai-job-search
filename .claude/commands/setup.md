# /setup - Profile Onboarding

You are running the onboarding setup for the AI Job Search framework. Your goal is to collect Meenakshi's professional information and populate all profile files so the `/apply` and `/scrape` workflows work out of the box.

---

## Step 0: Welcome & Choose Path

If `$ARGUMENTS` contains `--section <name>`, skip directly to that section in Path C. Do not run the path-selection prompt.

Otherwise, scan the `documents/` folder. Use Glob with `documents/**/*` and count files per subfolder.

Welcome the user with three paths:

> **Welcome! Let's set up your job search profile.**
>
> This fills in your candidate profile, behavioral summary, CV templates, and search queries so `/apply` and `/scrape` work out of the box.
>
> [If documents/ has files]: I can see files in your `documents/` folder. Three ways to start:
>
> **Path A: Read my documents folder** (recommended if you have your CV/LinkedIn there) — I'll read everything, cross-reference, and build your profile from real source materials.
>
> **Path B: Single CV import** — Paste or @-mention your CV. I'll extract it and ask follow-up questions.
>
> **Path C: Interview mode** — I'll walk you through questions section by section. Good for starting from scratch.

Wait for the user's choice.

---

## Path A: Documents Folder

### Step A1: Inventory
Glob `documents/**/*`. Print what was found per subfolder.

### Step A2: Read Existing Skill Files
Read all 7 skill files in parallel before extracting anything.

### Step A3: Parse Documents
Read each document. For CVs: extract name, contact, education, roles, skills, achievements. For LinkedIn: extract About section, experience, recommendations.

### Step A4: Cross-Reference Check
Check for inconsistencies across documents. Present and resolve before continuing.

### Step A5–A6: Build and Confirm Change Sets
Present proposed additions and conflicts. Apply confirmed changes with Edit.

### Step A7: Write Confirmed Changes and Fill Gaps
Apply edits. Then ask follow-up questions for:
- Career goals and target role types
- What energizes vs. drains
- Deal-breakers and must-haves
- Salary expectations (optional — but note Austria has mandatory KV minimum disclosure in job ads, so benchmarking is easier here)
- Location constraints (Vienna only, or open to remote Europe?)
- German language level (important for the Austrian market)
- Job search configuration (see Path C Section 9)

---

## Path B: Single CV Import

1. Read the document thoroughly.
2. Extract all structured information.
3. Present summary of what was extracted.
4. Ask follow-up questions for gaps.
5. Proceed to Step 3 (file generation).

---

## Path C: Interview Mode

### Section 1: Identity & Contact
- Full name, address in Vienna
- Phone, email, LinkedIn URL
- Languages spoken (with proficiency — especially German level: A1/A2/B1/B2/C1?)
- Current employment status and timeline (when does layoff take effect?)

### Section 2: Education
- Any degrees, diplomas, or formal education
- If no CS degree: what was your field? What institution?
- Certifications (online courses, professional certs — list with dates)
- Note: no formal CS degree is already pre-noted in the profile. This section adds specifics.

### Section 3: Professional Experience
For each role (most recent first):
- Job title, company, dates, location
- Key responsibilities (3-5 bullets)
- Key achievements — specific numbers, systems built, impact
- Technologies/tools used (frameworks, databases, cloud, tooling)
- What you facilitated, led, or owned specifically in Agile ceremonies

### Section 4: Technical Skills
- Java: which version? Which frameworks? (Spring Boot, Hibernate, etc.)
- REST APIs: what tooling? (Swagger/OpenAPI, Postman, etc.)
- Databases, messaging, cloud platforms
- CI/CD, testing, monitoring tools
- AI/ML: what are you currently studying? What tools/frameworks?

### Section 5: Behavioral Profile
Ask:
- "What work environments do you thrive in?"
- "What drains your energy at work?"
- "How do you prefer to work in teams?"
- "Describe a time you took ownership of something difficult."
- "What's your communication style with non-technical stakeholders?"
Synthesize into the behavioral profile.

### Section 6: Career Goals & Preferences
- Confirm priority order: Senior SWE → AI Engineer → Product/AI-adjacent
- What would a great role look like in 12 months?
- What would a 3-year path look like?
- Salary expectations (optional — note Austrian law requires KV minimum in ads)
- Hard deal-breakers beyond relocation?

### Section 7: References
- Names, titles, companies, emails, phone
- Relationship to Meenakshi

### Section 8: AI/ML Upskilling Status
This is unique to Meenakshi's strategic pivot goal:
- What are you studying currently (courses, books, projects)?
- What tools/frameworks have you touched (even basic: Python, LangChain, HuggingFace, etc.)?
- Do you have any side projects, even small ones?
- How are you planning to use your 20 hrs/week?

### Section 9: Job Search Configuration
Ask:
- **Role titles to search for:** e.g. "Senior Java Developer", "Backend Engineer", "Software Engineer", "AI Engineer", "Technical Lead"
- **Key skills as search terms:** e.g. "Java", "REST API", "Spring Boot", "microservices"
- **Target companies:** Any specific companies or types of companies?
- **Geographic scope:** Vienna primarily? Remote OK? EU-wide remote?
- **German language requirement:** Apply to German-only postings? English-only? Both?

Also suggest roles Meenakshi may not have considered:
- "Technical Product Owner" — bridges engineering and product, Agile background is directly relevant
- "API Platform Engineer / Integration Engineer" — plays to REST API strength
- "DevOps / Platform Engineer" — if there's tooling experience
- "Solutions Engineer / Pre-Sales Engineer" — if she enjoys client-facing work
- "Scrum Master" — if the facilitation experience is deep
- "AI / ML Platform Engineer" — infrastructure side of AI, closer to current Java/backend skills than pure ML research

---

## Step 3: Generate Profile Files

Populate or update these files. Check each before writing — skip if already populated.

1. **`CLAUDE.md`** — Replace any remaining `[placeholders]` with actual information
2. **`01-candidate-profile.md`** — Full structured profile
3. **`02-behavioral-profile.md`** — Behavioral assessment from interview answers
4. **`04-job-evaluation.md`** — Update skill match areas and career goals with actual detail
5. **`05-cv-templates.md`** — Add role-specific profile statement templates
6. **`07-interview-prep.md`** — Flesh out STAR stubs with actual scenario details
7. **`cv/main_example.tex`** — Replace all `[placeholders]` with actual data
8. **`.claude/skills/job-scraper/search-queries.md`** — Replace placeholder queries with actual role titles, skills, and location

---

## Step 4: Confirm & Next Steps

> **Setup complete!** Here's what was generated:
>
> - `CLAUDE.md` — Your full candidate profile
> - All 7 skill files in `.claude/skills/job-application-assistant/`
> - `cv/main_example.tex` — Your LaTeX CV template (compile with lualatex)
> - `.claude/skills/job-scraper/search-queries.md` — Job search queries for `/scrape`
>
> **Try it out:**
> - Run `/scrape` to search for matching jobs
> - Run `/apply <url>` with a job posting URL to generate a tailored CV + cover letter
> - Run `/setup --section search` later to update your search queries

Also remind the user:
- To install LaTeX if not already done (see `SETUP.md`)
- To get the OpenFonts for the cover letter template (see `SETUP.md`)
- That STAR stubs in `07-interview-prep.md` need fleshing out before interview practice
