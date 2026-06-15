# Cover Letter Templates and Tailoring Guide

## Template: Custom cover.cls (XeLaTeX)

**Output file:** `cover_letters/cover_<company>_<role>.tex`
**Compile with:** XeLaTeX (cover.cls requires fontspec)
**Font directory:** `cover_letters/OpenFonts/fonts/`

### Compile command
```bash
cd cover_letters && xelatex -interaction=nonstopmode cover_<company>_<role>.tex
```

Expected output: `Output written on cover_<company>_<role>.pdf (1 page, ...)`. Any other page count is a failure.

## Document Structure

```latex
\documentclass[]{cover}
\usepackage{fancyhdr}
\pagestyle{fancy}
\fancyhf{}
\rfoot{Page \thepage \hspace{0pt}}
\thispagestyle{empty}
\renewcommand{\headrulewidth}{0pt}

\begin{document}

\namesection{}{Meenakshi [Last Name]}{
  \href{mailto:meenuplb@gmail.com}{meenuplb@gmail.com} | [Phone] | \urlstyle{same}\href{[LinkedIn URL]}{LinkedIn}
}

\currentdate{\today}
\lettercontent{Dear [Name / Hiring Team],}

\lettercontent{[Opening — role, connection to background, 2-3 sentences.]}

\lettercontent{[Body — most relevant experience, specific and forward-looking.]}

{\raggedright\fontspec[Path = OpenFonts/fonts/raleway/]{Raleway-Medium}\fontsize{11pt}{13pt}\selectfont
\begin{itemize}
    \item [Concrete achievement/skill 1]
    \item [Concrete achievement/skill 2]
    \item [Concrete achievement/skill 3]
\end{itemize}\par}
\vspace{6pt}

\lettercontent{[Why this company specifically — researched, specific, not generic.]}

\lettercontent{I look forward to hearing from you.}

\begin{flushright}
\closing{Kind regards,\\}
\signature{Meenakshi [Last Name]}
\end{flushright}

\end{document}
```

## Key Commands Reference

| Command | Purpose |
|---------|---------|
| `\namesection{}{Name}{contact info}` | Header with name and contact |
| `\currentdate{date}` | Date field |
| `\lettercontent{text}` | Body paragraph (adds spacing after) |
| `\closing{text}` | Closing line |
| `\signature{name}` | Printed name |

## Known Template Pitfall: itemize inside `\lettercontent{}`

**Wrong (breaks compile):**
```latex
\lettercontent{Here is how my experience maps:
\begin{itemize}
    \item ...
\end{itemize}}
```

**Correct:**
```latex
\lettercontent{Here is how my experience maps:}

{\raggedright\fontspec[Path = OpenFonts/fonts/raleway/]{Raleway-Medium}\fontsize{11pt}{13pt}\selectfont
\begin{itemize}
    \item ...
\end{itemize}\par}
\vspace{6pt}

\lettercontent{[next paragraph]}
```

## Tailoring Guidelines

### Salutation
- Named person: "Dear [First Last],"
- Known team: "Dear [Company] hiring team,"
- Generic: "Dear Hiring Manager,"
- German posting: "Sehr geehrte Damen und Herren," or "Sehr geehrte/r [Name],"

### Length — Hard 1-Page Limit
- **Word budget: 250-300 words** of body text. 350 words will overflow.
- 3 content blocks: opening + body + closing. Add a 4th only if others are short.
- When adding company-specific content, trim other content — never add net length

### Non-English Cover Letters
- Same template structure, write in the posting's language
- German date format: Vienna, [DD. Month YYYY]
- German closing: "Mit freundlichen Grüßen," (formal) or "Mit freundlichem Grüßen,"
- **Vienna market note:** Most international tech companies in Vienna accept English-language cover letters regardless of posting language. When in doubt, write in English unless the company is Austrian-only (e.g. local Mittelstand firms).

## Checklist Before Finalizing
- [ ] No em-dashes
- [ ] No cliches or empty filler
- [ ] Every claim backed by a specific example
- [ ] Forward-looking framing
- [ ] Motivation section references this specific company's mission/values/product
- [ ] Company name and role are correct throughout
- [ ] Date is current
- [ ] Fits on one page
- [ ] Language matches the job posting (or English if international tech)
- [ ] Salutation is appropriate
