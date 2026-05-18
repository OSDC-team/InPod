# INSO Podcast Index

A static GitHub Pages site listing INSO-recommended podcasts.

## Repo structure

```
├── index.html          ← the site
├── data/
│   └── podcasts.csv    ← podcast data (loaded at runtime)
└── static/
    └── logo.png
```

## Data source

The index loads `data/podcasts.csv` at runtime via `fetch()`. This means the site **requires an HTTP server** — opening `index.html` directly via `file://` will fail due to browser CORS restrictions.

To run locally:
```bash
python3 -m http.server
```
Then open `http://localhost:8000`.

## CSV format

The CSV parser is flexible with column names (it matches on substrings, case-insensitive). Supported columns:

| Column | Matched by |
|---|---|
| Title | contains "title" |
| Producer | contains "producer" |
| Platform/App | contains "app" or "application" |
| Link | contains "link" |
| Tags | contains "tag" |
| Language | contains "lang" |
| Region/Country | contains "region" or "countr" |
| Frequency | contains "freq" |
| Description | contains "desc" |

Tags may be comma- or pipe-separated within a cell.

## Adding podcasts

### Option A — Manual entry (session only)

1. Open the live site.
2. Click **+ Add** (top right or bottom of page).
3. Fill in the form. Only **Title** is required.
4. Click **Add to index**.

> **Note:** Manually added entries are session-only and won't persist after a page reload.

### Option B — CSV import (session only)

1. Open the live site.
2. Click **Import CSV**.
3. Drop or select a `.csv` file. A preview shows how many new rows will be added (duplicates by title are skipped).
4. Click **Add to index**.

> **Note:** Imported entries are also session-only.

### Option C — Edit the CSV (permanent)

Edit `data/podcasts.csv` directly, following the column format above. Commit and push — GitHub Pages will rebuild automatically.

## Filtering & search

The toolbar supports:

- **Search** — matches title, producer, tags, region, and description
- **Platform** filter — Spotify, Apple Podcasts, Deezer, YouTube, Web
- **Language** filter — EN, FR, ES, AR, NL, CZ, DE, PT, RU, UK
- **Frequency** filter — Daily, Weekly, Biweekly, Monthly, Irregular
- **Topic** filter — two-level taxonomy (primary category → subtopic)
- **Region** filter — built dynamically from the loaded data
- **Sort** — Default, A→Z, Frequency
- **View** — Card view or Compact view

Active filters are shown as removable pills above the results.

## Tag taxonomy

Tags are grouped into four primary categories:

| Category | Subtags |
|---|---|
| Conflict & Security | security, military, organised crime, cyber, intelligence, investigation, sanctions & finance |
| Politics & Policy | politics, foreign policy, governance, law |
| Humanitarian Affairs & Aid | humanitarian, development, human rights, displacement |
| Critical & Emerging Issues | news, tech, disinformation, culture, environment, verification |

## GitHub Pages setup

1. Go to **Settings → Pages** in your repo.
2. Set Source to `main` branch, `/ (root)` folder.
3. The site will be live at `https://<username>.github.io/<repo>/`.