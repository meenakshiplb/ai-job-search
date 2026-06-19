# /scrape - Job Search for Vienna / Europe Market

You are searching for job opportunities matching Meenakshi's profile. The focus area is `$ARGUMENTS` (optional — if empty, search all priority categories).

Read the search queries and candidate profile first:
- `.claude/skills/job-scraper/search-queries.md`
- `.claude/skills/job-application-assistant/01-candidate-profile.md` (for fit evaluation context)
- `.claude/skills/job-application-assistant/04-job-evaluation.md` (for scoring criteria)

---

## Search Strategy

Unlike the Danish-market version of this framework, the Vienna/Europe version does **not** use CLI scrapers. Instead, use `WebSearch` and `WebFetch` directly with targeted queries from `search-queries.md`.

Search the following job portals in order of priority:

### Tier 1: Austrian / DACH Market
- **karriere.at** — Austria's largest job board
- **stepstone.at** — Major Austrian/German job board
- **willhaben.at/jobs** — Popular in Austria
- **xing.com** (XING Jobs) — Dominant in the DACH region alongside LinkedIn
- **jobs.at** — Austrian-focused

### Tier 2: European / International
- **linkedin.com/jobs** — Best for international tech companies in Vienna
- **indeed.com** (Austria/Germany) — Wide coverage
- **glassdoor.com** — Useful for company research alongside job listings
- **remoteok.com** and **weworkremotely.com** — For remote-first roles

### Tier 3: Company Career Pages (via Google site: search)
- Use `site:<company-domain> jobs` or `site:<company-domain> careers`
- Especially useful for known target companies

---

## Search Execution

For each query category in `search-queries.md`:

1. Run `WebSearch` with the query
2. For promising results, use `WebFetch` to retrieve the job posting detail
3. Filter: must be posted within the last 14 days OR have a future deadline. Flag posts with no visible date.
4. Record results in `job_scraper/results.md` with: title, company, URL, posted date, brief summary

### LinkedIn note (IMPORTANT)
LinkedIn **search pages** return HTTP 403 — never WebFetch `linkedin.com/jobs/search/...` or `linkedin.com/jobs?keywords=...`.
Instead: run `site:linkedin.com/jobs/view` queries via WebSearch (Google), extract individual job IDs from results, then WebFetch each `https://www.linkedin.com/jobs/view/{ID}/` directly — these individual pages load successfully. See the LinkedIn Discovery Protocol section in `search-queries.md`.

### Date filter note
Austrian job ads often don't show a post date but show an application deadline ("Bewerbungsfrist"). Include if the deadline is in the future. LinkedIn pages show "Posted X days ago" — use that for date verification.

---

## Deduplication

Before presenting results, check `job_scraper/seen_jobs.md` (create if it doesn't exist). Skip any job URL already listed there — this prevents the same posting appearing across multiple daily files. After presenting results, append newly seen job URLs to `job_scraper/seen_jobs.md`.

---

## Output Format

Present results sorted by estimated fit (highest first) using a quick scoring pass:

```
## Job Search Results — [Date]

### Strong Fits (estimated 70+)
---
**[Role Title]** — [Company]
📍 [Location] | 🗓 [Posted/Deadline]
🔗 [URL]
> [2-sentence summary: role in their words + why it fits Meenakshi's profile]
Estimated fit: [XX/100] — [one-line reason]
---

### Good Fits (estimated 55-70)
[same format]

### Worth Reviewing (estimated 40-55)
[same format]
```

After presenting, ask:
> "Which of these would you like me to evaluate in detail? Say `/apply <URL>` for any you want to pursue, or I can run a full fit evaluation on one now."

---

## Focus Area Variants

If `$ARGUMENTS` is provided, narrow the search:
- `/scrape java` — Priority 1 queries only (Senior Java/Backend)
- `/scrape ai` — Priority 2 queries (AI Engineer / ML)
- `/scrape remote` — Remote-only queries
- `/scrape [company name]` — Search that specific company's careers page

---

## After Scraping

1. Save results to `job_scraper/daily/YYYY-MM-DD.md` (use today's actual date in the filename, e.g. `2026-06-15.md`). Create the file if it doesn't exist; overwrite if it does.
2. Append newly seen job URLs to `job_scraper/seen_jobs.md` for deduplication on future runs.
3. Offer to evaluate a specific posting in detail or run `/apply` on a chosen posting.
