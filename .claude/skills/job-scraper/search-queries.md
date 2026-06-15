# Search Queries — Vienna / Europe Market

<!-- Run /setup --section search to update these as priorities evolve -->

## Target Profile
- **Location:** Vienna, Austria (primary) + remote within Europe (secondary)
- **Languages:** English (primary), German (secondary — B1 level, flag German-only roles)

## Job Portals

### Primary (Austrian / DACH)
- **karriere.at** — Austria's largest job board
- **stepstone.at** — Major Austrian/German board
- **xing.com** — DACH professional network, strong job listings
- **willhaben.at/jobs** — Austrian-focused
- **jobs.at** — Austrian-focused

### Secondary (European / International)
- **linkedin.com/jobs** — Best for international tech companies with Vienna offices
- **indeed.com** (Austria filter) — Wide coverage
- **glassdoor.com/job-listings** — Good for company culture research
- **remoteok.com** — Remote-first roles, no location filter needed
- **weworkremotely.com** — Remote-first roles

### Tertiary (Company Career Pages via Google)
- `site:<company>.com careers` or `site:<company>.com jobs`

---

## Query Categories

### Priority 1: Senior Java / Backend Engineering
These match Meenakshi's strongest and most immediately hirable skills.

```
site:karriere.at "Senior Java Developer" Wien
site:karriere.at "Backend Engineer" Java Wien
site:stepstone.at "Senior Software Engineer" Java Wien
site:stepstone.at "Java Developer" REST Wien
site:linkedin.com/jobs "Senior Java Engineer" Vienna
site:linkedin.com/jobs "Backend Software Engineer" Java Vienna Austria
site:xing.com "Senior Java Entwickler" Wien
"Senior Java" REST API Vienna -junior
"Software Engineer" Java "Spring Boot" Vienna
```

### Priority 2: AI Engineer / ML Engineer (Transition Target)
These match Meenakshi's strategic pivot goal. Strong Java + learning AI is a real differentiator.

```
site:karriere.at "AI Engineer" Wien
site:karriere.at "ML Engineer" Wien
site:karriere.at "Machine Learning" Java Wien
site:linkedin.com/jobs "AI Engineer" Vienna
site:linkedin.com/jobs "ML Engineer" Vienna Austria
site:linkedin.com/jobs "AI Software Engineer" Vienna
"AI Engineer" Java Vienna
"LLM Engineer" Vienna backend
"Platform Engineer" AI ML Vienna
```

### Priority 3: Adjacent Roles (Pivot Opportunities)
Roles that leverage Agile facilitation, Java depth, or AI interest without requiring pure ML credentials.

```
site:karriere.at "Technical Product Owner" Wien
site:karriere.at "API Platform Engineer" Wien
site:karriere.at "Integration Engineer" Java Wien
site:stepstone.at "Scrum Master" Wien (if facilitation role interests you)
site:linkedin.com/jobs "Solutions Engineer" Java Vienna
site:linkedin.com/jobs "Technical Lead" Java Vienna
site:linkedin.com/jobs "API Engineer" Vienna
"Technical Product Owner" Java Vienna
"Platform Engineer" Java APIs Vienna
```

### Priority 4: Remote Europe (No location restriction)
For strong roles outside Vienna where remote is explicit.

```
site:remoteok.com "Senior Java Engineer" Europe
site:weworkremotely.com "Java Engineer"
site:linkedin.com/jobs "Senior Software Engineer" Java "remote" Europe
"Senior Backend Engineer" Java remote EU
"Senior Java Developer" remote Europe
```

### Priority 5: Target Companies in Vienna
Run site searches for companies known for strong engineering in Vienna. Update this list after `/setup`.

```
[Add target companies via /setup]
site:broadcom.com/careers [for reference — current employer, may be exiting]
site:dynatrace.com careers Vienna
site:tricentis.com careers Vienna
site:n26.com careers Vienna
site:rbi.at careers software engineer
site:george-labs.com careers
site:prelios.com careers
```

---

## Location Filter

**Ideal:** Vienna (1010–1230 postal codes)
**Acceptable:** Vienna metropolitan area, any remote-within-Europe role
**Borderline:** Lower Austria (Niederösterreich) — assess commute individually
**Too far / deal-breaker:** Relocation required outside Europe

## Date Filter
- Include: posted within the last 14 days, OR future application deadline (Bewerbungsfrist)
- Exclude: older postings with no visible date unless the deadline is future
- Flag: "date unknown" if no date is visible

## Language Filter
- **English-language postings:** Always apply in English
- **German-language postings:** Apply in English unless the posting explicitly requires German (most international tech companies in Vienna accept English)
- **German-only postings (e.g. local firms, public sector):** Flag for review — assess language fit honestly

## Adapting Queries
If you use `/scrape <focus>`:
- `/scrape java` — Priority 1 only
- `/scrape ai` — Priority 2 only
- `/scrape remote` — Priority 4 only
- `/scrape [company]` — site-search that company's careers page
