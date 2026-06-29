# Memory Maintenance & Token Optimization

**Last updated:** June 26, 2026  
**Purpose:** Reduce token overhead, keep Claude's context lean and actionable, establish standing preferences for all requests.

---

## 1. Archive/Trim Triggers

Archive from "Active applications and contacts" section when:

| Condition | Action |
|-----------|--------|
| Application rejected or withdrawn | Remove entirely |
| Interview completed (pass or fail) | Move to summary line only (e.g., "X role: interviewed, outcome TBD") |
| No updates for 2+ weeks | Mark as "cold lead" or deprioritize |
| Posting expires or role filled | Remove |
| Contact unresponsive after 2 follow-ups | Move to "Past outreach" |

### Current cleanup candidates:
- **Ethos expert network** → low-priority, posting date stale, verify if still live before next session
- **WienIT** → consolidate to one-liner: "Applied; neighbor referral identified"

---

## 2. Standing Preferences (Apply Every Session)

### Response style
- **Default: "brief"** unless working on a major deliverable (CV, interview prep, full analysis)
- **Structured:** Headers and bullets only when complexity demands; otherwise prose
- **No flattery, no sugarcoating** — blunt assessment, flag blind spots

### Task batching
- **Group related edits into ONE request** instead of 5 serial ones
  - ❌ "Update objective" → then "add this bullet" → then "check font"
  - ✅ "Update objective, add this bullet to Experience, verify EB Garamond loaded"
- Reduces token overhead and context-switching

### File handling
- **Cache locally.** Don't ask me to re-view files you already have
  - ❌ "View Docker_Cheat_Sheet.md" (nth time)
  - ✅ "I was reading the Docker cheat sheet; my question is..."
- **Ask about files, don't ask me to view them again**
  - ❌ "View my Career_Tracker.xlsx and tell me what's overdue"
  - ✅ "In my Career_Tracker, what should I prioritize next? (I'll check the dates)"
- Exception: First read of a new file, or if the file was just modified

### Artifact strategy
- **"Chat only"** if you want a draft to review before artifact
- **"Text first"** if you want HTML/markdown before PDF generation
- Don't regenerate full PDFs for one-word edits; ask for inline changes instead

### Communication defaults
- Assume I remember your context — reference it directly
  - ✅ "Like the BAWAG interview, but for Check24"
- **Reference this file:** "Check MEMORY_MAINTENANCE.md and apply cleanup" at start of a session if you want old items trimmed

---

## 3. Token Optimization Checklist

### Before sending a request:
- [ ] Can I batch this with another task? (Group edits, questions, reviews)
- [ ] Am I asking you to re-view a file I already have? (Ask about it instead)
- [ ] Is this "brief answer" or "deep dive"? (Signal it)
- [ ] Do I need an artifact or just a draft? (Say "chat only" if uncertain)
- [ ] Can I reference an existing resource instead of asking for a full re-read? (e.g., "In the Docker cheat sheet...")

### Claude will avoid:
- Over-structuring simple answers
- Unnecessary tool calls (visualization, artifact creation unless asked)
- Re-reading files without freshness reason
- Verbose preambles or meta-commentary about memory/context

---

## 4. File Read Avoidance Patterns

**Don't ask me to view:**
- `Docker_Cheat_Sheet.md` — ask a question about it instead
- `Career_Tracker.xlsx` — summarize what you remember; ask me to help prioritize
- CV versions — reference the one you're working on by name; ask for edits
- Interview prep notes — reference the specific topic; ask for advice

**DO ask me to:**
- "Summarize the Docker cheat sheet in 3 bullets"
- "Based on the job pipeline, what's my next move?"
- "I'm reading the Check24 JD; here's where I think I have gaps…"
- "In the Docker section on signals/PID 1, did I get the interview answer right?"

---

## 5. Memory Cleanup Log

| Date | Item | Action |
|------|------|--------|
| 2026-06-26 | Docker cheat sheet finalized | Keep; reference-only, not view-again |
| 2026-06-26 | Token optimization baseline | Document this file |
| TBD | Ethos expert network | Verify posting date; archive if stale |
| TBD | Completed applications | Move to past summary as they resolve |

---

## 6. How to Use This File

**In conversation:**
- At start of a session: *"Check MEMORY_MAINTENANCE.md and apply cleanup"*
- Mid-conversation if you want brief mode: *"Brief answer only"*
- When batching tasks: *"Three edits: [1] [2] [3]"* (not three separate messages)
- If you want me to stop re-viewing a file: *"I'll manage X; focus on the question"*

**To update this file:**
- Add new archive candidates as they emerge
- Update cleanup log when applications resolve
- Add standing preferences if your needs change

---

## 7. Token Savings Summary

| Strategy | Savings |
|----------|---------|
| Batch 3 edits into 1 request | ~30% (eliminates 2 context reloads) |
| Avoid redundant file re-reads | ~10–15% per file |
| Use "brief" mode for simple answers | ~20% (less preamble) |
| "Chat only" drafts (no artifact overhead) | ~5–10% on iteration |
| Archive old applications from memory | ~5% ongoing (less context to load) |

**Realistic total:** 50–70% reduction in token overhead if all strategies are used consistently.

---

**Version:** 1.0  
**Next review:** When first application is rejected or major cleanup is needed
