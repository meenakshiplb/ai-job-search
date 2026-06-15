# OpenFonts

The cover letter template requires Lato and Raleway font files in these directories:
- `fonts/lato/` — Lato-Lig, Lato-Reg, Lato-Bol, Lato-LigIta, Lato-RegIta, Lato-Hai
- `fonts/raleway/` — Raleway-ExtraLight, Raleway-Medium

## How to get the fonts

**Option A (recommended):** Clone the original repo and copy the OpenFonts folder:
```bash
git clone https://github.com/MadsLorentzen/ai-job-search /tmp/ai-job-search
cp -r /tmp/ai-job-search/cover_letters/OpenFonts/ ./cover_letters/OpenFonts/
```

**Option B:** Download Lato from https://fonts.google.com/specimen/Lato and Raleway from https://fonts.google.com/specimen/Raleway, rename files to match the expected names in cover.cls.

Without these fonts, the cover letter will not compile.
