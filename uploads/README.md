# uploads/ — the drop folder

Put new study material here and the **Uploads** page of the handbook lists it by itself.

How it works, in one breath: a GitHub Action watches this folder, rebuilds
`manifest.js` on every push, and the page reads that file. No build step on your
side, no database, nothing to configure after the first push.

## Adding material

Either of these works:

1. On GitHub: open the `uploads/` folder → **Add file → Upload files** → commit to `main`.
2. Locally: copy files in, `git add uploads && git commit -m "add ..." && git push`.

Preferred layout (the page groups by it):

```
uploads/
  2026-10-02-sap-ucc-sac-workshop/     ← one folder per session/day: YYYY-MM-DD-what-it-was
    whiteboard-protocol/               ← optional sub-group
    overview-slides/
    ucc-curriculum-3.0/
  2026-10-09-sac-planning-session/
```

A `YYYY-MM-DD-` prefix on the folder name gives the page a date to sort by.
Loose files dropped straight into `uploads/` still show up, under "Loose files".

## Previewing locally

`python scripts/build_manifest.py` then open `uploads.html` in a browser. The page
loads `manifest.js` with a plain `<script>` tag, so it works from `file://` too.

## A word on what you commit here

The material from the 2 October 2026 workshop (the four SAP UCC Magdeburg
curriculum documents and the slide screenshots) is © SAP UCC Magdeburg and is
provided to SAP University Alliances member institutions. That is fine for your own
study and for a private repository. If this repository is public, remove those
files before pushing (the manifest rebuilds itself) and keep them local.
