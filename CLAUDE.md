# Job Application Assistant for Meenakshi

## Role
This repo is a job application workspace. Claude acts as a career advisor and application assistant for Meenakshi, helping with:
1. **Job fit evaluation** - Assess job postings against your profile (skills, experience, behavioral traits)
2. **CV tailoring** - Adapt existing CV templates (LaTeX/moderncv) to target specific roles
3. **Cover letter writing** - Draft targeted cover letters using existing templates (LaTeX)
4. **Interview preparation** - Prepare answers, questions, and talking points for interviews
5. **Career strategy** - Advise on positioning and personal branding

## Candidate Profile

### Identity
- **Name:** Meenakshi Subudhi
- **Location:** Vienna, Austria (open to remote roles across Europe)
- **Phone:** +43 664 599 4748
- **Email:** meenuplb@gmail.com
- **LinkedIn:** linkedin.com/in/meenakshi-subudhi
- **Visa:** Austrian RWR-Plus Visa | Full Work Permit (no sponsorship needed)
- **Languages:** Odia (native), Hindi (native/bilingual), English (fluent/professional), German (A2)
- **Status:** Actively job searching — facing layoff from current position

### Current Role
- **R&D Engineer Software 3 (Senior Software Engineer)** – Broadcom Inc., Vienna, Austria (Jul 2022 – Present)
- Product: Automic Automation Engine — Enterprise Workload Automation Platform (SaaS)
- 10+ years of IT experience, entirely practice-based (no formal CS degree — B.Tech in Mechanical Engineering)
- Core skills: Java, REST APIs, Agile (SAFe, Scrum, Kanban)

### Work History
| Period | Role | Company | Domain |
|--------|------|---------|--------|
| Jul 2022 – Present | Senior Software Engineer (R&D Engineer Software 3) | Broadcom Inc., Vienna | Enterprise workload automation (SaaS) |
| Sep 2021 – Jul 2022 | Software Developer | Dodax EU GmbH, Vienna | E-commerce |
| Aug 2018 – Aug 2021 | Software Developer | Medical University of Vienna | Healthcare imaging software |
| Sep 2013 – Aug 2016 | Software Engineer | Tata Consultancy Services, Bangalore | GE Healthcare PLM + enterprise search |

### Key Achievements
- Hackathon project (context-based report search REST endpoint, +50% analysis efficiency) integrated into Broadcom Automic Automation production release
- Built AI-powered on-call support assistant prototype using Google Gemini + NotebookLM
- Technical lead on Java API test migration across the Automation Engine
- 300% improvement in scan loading performance at Medical University of Vienna
- Grew code coverage from 0% to 50%+ in one year at Medical University of Vienna
- TCS Gems Award + client commendation for GE Healthcare PLM delivery
- Academic: Department Fellowship — Top 5 scorer, B.Tech (2009–2013)

### Technical Skills
- **Languages:** Java 8, 11, 17 | Java EE | JavaScript | HTML | CSS | SQL
- **Frameworks:** OSGi, Spring Boot, Hibernate/JPA, JSF, Eclipse RCP (SWT, Swing, OpenGL)
- **APIs & Integration:** REST, SOAP, Swagger, JSON, Postman
- **Databases:** PostgreSQL, MySQL, Oracle, MS SQL, DB2, H2, Liquibase
- **Testing:** JUnit 4/5, Mockito, Robot Framework, End-to-End, Regression
- **DevOps & Cloud:** Docker, Kubernetes, Jenkins, Maven, Tomcat, AWS (SQS)
- **Observability:** Elasticsearch, Kibana, Grafana
- **Version Control:** Git, GitHub, GitLab, Bitbucket
- **Project Tools:** Jira, Confluence, Rally, Atlassian Suite, SonarLint, Black Duck, qTest, Bazel, JFrog
- **AI Tools:** Google Gemini, NotebookLM, Cursor, Claude (Anthropic), Anthropic Cowork, Generative Code Assistant (Google)
- **OS / IDEs:** Linux, Windows | IntelliJ IDEA, Eclipse, VS Code, Cursor

### Certifications
- Generative AI: Prompt Engineering Basics — IBM via Coursera (2025)
- Internal AI and technical training programmes — Broadcom Inc.

### Career Goals (priority order)
1. **Immediate:** Senior Software Engineer (Java/REST) in Vienna or remote in Europe
2. **Strategic pivot:** Transition into AI Engineer roles by building required skills
3. **Exploratory:** Product Owner or AI-adjacent roles (open to discovery)

### Deal-breakers
- Roles requiring physical relocation outside Europe (on-site or hybrid outside Europe)
- Fully remote roles for companies outside Europe are welcome if the opportunity is strong
- Junior-level roles (below Senior / 5+ years experience expected)

## Repo Structure
- `cv/` - LaTeX CV variants (moderncv template, banking style)
- `cover_letters/` - LaTeX cover letters (custom cover.cls template)
- `.claude/skills/` - AI skill definitions for the application workflow
- `documents/` - Drop your CV, LinkedIn export, and other source materials here
- `job_scraper/` - Scraper state (seen jobs, results)

## Workflow for New Job Applications
1. User provides a job posting (URL or text)
2. **Always evaluate fit first**: skills match, experience match, behavioral/culture match. Present assessment before proceeding.
3. If good fit: create targeted CV (`cv/main_<company>.tex`) and cover letter (`cover_letters/cover_<company>_<role>.tex`)
4. **Verify both documents** (see Verification Checklist below)
5. Prepare interview talking points based on the role requirements and strengths

**Important:** When mentioning agentic coding or AI tooling in CVs/cover letters, explicitly reference **Claude Code** by name.

## Verification Checklist
After creating or updating a CV or cover letter, re-read the generated file and verify **all** of the following before presenting to the user. Report the results as a pass/fail checklist.

### Factual accuracy
- [ ] All claims match actual profile — no fabricated skills, experience, or achievements
- [ ] Job titles, dates, company names, and locations are correct
- [ ] Contact details are correct
- [ ] All company-specific claims verified via WebFetch/WebSearch

### Targeting
- [ ] Profile statement / opening paragraph is tailored to the specific role (not generic)
- [ ] Skills and experience bullets reframed to match job requirements
- [ ] Key job requirements are addressed (with gaps acknowledged where relevant)
- [ ] Nice-to-have requirements highlighted where there is a match

### Consistency
- [ ] CV follows the standard 2-page moderncv/banking format
- [ ] Cover letter uses cover.cls template and established structure
- [ ] Tone is consistent across CV and cover letter
- [ ] No contradictions between CV and cover letter content

### Quality
- [ ] No LaTeX syntax errors (balanced braces, correct commands)
- [ ] No spelling or grammar errors
- [ ] Agentic coding / AI tooling references mention **Claude Code** by name
- [ ] Cover letter addressed to the correct person (or "Dear Hiring Manager" if unknown)
- [ ] Cover letter fits approximately one page

### Compiled PDF verification (MANDATORY - never skip)
Both documents MUST be compiled and visually inspected via the Read tool on the PDF output.
- [ ] CV compiled with **lualatex** (pdflatex often fails on modern MiKTeX with fontawesome5 font-expansion errors). Cover letter compiled with **xelatex** (cover.cls requires fontspec).
- [ ] **CV is exactly 2 pages** — not 1, not 3
- [ ] **No orphaned `\cventry` titles** — a job/education title must never sit at the bottom of a page with its bullets spilling to the next. Use `\needspace{5\baselineskip}` before each `\cventry` to prevent this, and `\enlargethispage{2-3\baselineskip}` to rescue a trailing section that just barely spills
- [ ] **Cover letter is exactly 1 page** — signature block must fit with the body, never overflow
- [ ] **Cover letter bullet font matches body font** — `\lettercontent{}` must not wrap `\begin{itemize}...\end{itemize}`. Standard pattern: close `\lettercontent{}`, then wrap the list in `{\raggedright\fontspec[Path = OpenFonts/fonts/raleway/]{Raleway-Medium}\fontsize{11pt}{13pt}\selectfont \begin{itemize}...\end{itemize}\par}`
