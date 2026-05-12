# InPod
# INSO Podcast Index

A static GitHub Pages site listing INSO-recommended podcasts.

## Repo structure

```
├── index.html          ← the site
└── static/
    └── logo-symbol-wb.png
```

## Adding podcasts

### Option A — CSV import (no code needed)

1. Open the live site.
2. Click **Import CSV** (top right).
3. Drop in any `.csv` that has these columns (order doesn't matter, header names are flexible):

| Column | Matched by |
|---|---|
| `Created By` | contains "created" |
| `Title` | contains "title" |
| `Podcast producer` | contains "producer" |
| `Podcast application` | contains "application" |

4. A preview shows how many new rows will be added. Click **Add to index**.

> **Note:** The import is session-only — it doesn't persist after a page reload.  
> To permanently save new podcasts, follow Option B.

### Option B — Edit the seed data (permanent)

Open `index.html` and find the `seedData` array near the top of the `<script>` block. Add entries in the same format:

```js
{ submitter:"INSO_HQ_YOUR_ROLE", title:"Podcast Title", producer:"Producer Name", app:"Spotify" },
```

Commit and push — GitHub Pages will rebuild automatically.

## GitHub Pages setup

1. Go to **Settings → Pages** in your repo.
2. Set Source to `main` branch, `/ (root)` folder.
3. The site will be live at `https://<username>.github.io/<repo>/`.