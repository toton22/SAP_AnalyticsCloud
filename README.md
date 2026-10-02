# SAC Certification Handbook

A self-contained study site for **SAP Certified – Data Analyst – SAP Analytics Cloud (C_SAC)**,
extended on 2 October 2026 with the SAP UCC Magdeburg workshop material and the SAP University
Alliances Global Bike curriculum. Static HTML, no build step, deploys to GitHub Pages as-is.

```
index.html        the handbook: 7 tabbed pages (start, ecosystem, syllabus, videos, 70 questions,
                  workshop notes, Global Bike lab) — deep-linkable as index.html#p-work, #p-lab, #p-qb …
uploads.html      the self-updating drop-folder page
uploads/          put new material here (see uploads/README.md)
uploads/manifest.js   generated — the list uploads.html renders; rebuilt by the Action
scripts/build_manifest.py   the generator; also runs locally
.github/workflows/rebuild-uploads-manifest.yml   rebuilds the manifest on every push to uploads/
.nojekyll         tells GitHub Pages to serve files verbatim
```

## Publish on GitHub Pages (once, ~3 minutes)

```bash
cd sac-handbook
git init -b main
git add .
git commit -m "SAC Certification Handbook — 2 Oct 2026 update"
gh repo create sac-handbook --public --source=. --push     # or create the repo on github.com and push
```

Then on GitHub: **Settings → Pages → Build and deployment → Source: Deploy from a branch → `main` / `/ (root)` → Save.**
The site appears at `https://<your-user>.github.io/sac-handbook/` within a minute or two.

One more switch so the Action may commit: **Settings → Actions → General → Workflow permissions →
Read and write permissions → Save.** (The workflow declares `permissions: contents: write`; this setting
has to allow it.)

## Adding material later

Drop files into `uploads/` (on GitHub: *Add file → Upload files*; or locally and push). The workflow
rebuilds `uploads/manifest.js`, commits it, Pages redeploys, and the Uploads page lists the new files.
Nothing else to touch. Folder convention: `uploads/YYYY-MM-DD-what-it-was/…`.

To preview locally without GitHub: `python scripts/build_manifest.py`, then open `index.html`.

## Before making the repository public

`uploads/2026-10-02-sap-ucc-sac-workshop/` currently holds the four SAP UCC curriculum documents and
screenshots of the trainers' slides. They are © SAP UCC Magdeburg, provided to SAP University Alliances
member institutions, and should not be redistributed publicly. Keep the repository private, or delete
that folder's `ucc-curriculum-3.0/`, `overview-slides/` and `whiteboard-protocol/` before the first
public push (`workshop-notes.md` is your own summary and can stay). The manifest rebuilds itself either way.

## Editing the handbook

Everything is in `index.html`: the CSS block at the top, one `<div class="page">` per tab, and the
question bank as the `Q` array in the script at the bottom. Add a question by appending an object
to `Q`; the filter chips and numbering follow automatically. Questions carry `w:1` when they came
from the workshop, which drives the *From the workshop* filter.
