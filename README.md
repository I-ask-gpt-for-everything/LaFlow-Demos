# LandscapeFlow — Showcase site

A self-contained, client-facing website that presents the five LandscapeFlow (LaFlow) feature demos as one polished, interactive showcase. Built to hand to prospective clients (Greek landscape-architecture firms) and to publish on GitHub Pages.

Everything here is **static and self-contained** — no build step, no server required, **zero external requests** (no CDN, no web fonts, no analytics). It works both by double-clicking `index.html` locally and when hosted online.

## What's inside

```
laflow-showcase/
  index.html              The showcase landing page (Greek, client-facing)
  README.md               This file
  .gitignore
  assets/screens/         Screenshots used as card art + hero collage
  demos/                  The five live demos (self-contained single-file apps)
    offer-drafter/        01 · Δημιουργός Προσφορών
    project-diary/        02 · Ημερολόγιο Έργων
    client-updates/       03 · Ενημερώσεις Πελατών με AI
    followups/            04 · Εκκρεμότητες Επικοινωνίας
    incoming-offers/      05 · Εισερχόμενες Προσφορές
```

The demos are the **redesigned** versions of the LaFlow track. Each is a single `index.html` with all CSS/JS inline, works offline, and stores its state in the browser's `localStorage`.

## How to view it locally

**Easiest:** double-click `index.html`. It opens in your browser and the five feature cards work immediately.

**Recommended (matches the hosted experience exactly):** serve the folder over a local web server, so the in-page demo viewer (the embedded preview) behaves identically to production. From this folder:

```bash
# Python 3
python -m http.server 8000
# then open http://localhost:8000/
```

> Why serve it? The landing page opens each demo in an in-page viewer (an `iframe`). Some browsers restrict `iframe`s when a page is opened directly from the filesystem (`file://`). Over a local server (or once hosted) there's no such restriction. Either way, every card also has an **«Άνοιγμα σε νέα καρτέλα»** link that always works.

## Publishing to GitHub

Because the folder is fully self-contained, you can publish it two ways:

**A) As its own repository (cleanest — recommended).** The contents of this `laflow-showcase/` folder become the whole repo, so none of the studio's internal documents are ever exposed.

```bash
cd laflow-showcase
git init
git add .
git commit -m "LandscapeFlow showcase site"
git branch -M main
git remote add origin https://github.com/<you>/<repo>.git
git push -u origin main
```

Then on GitHub: **Settings → Pages → Source: `main` / root** → your site goes live at `https://<you>.github.io/<repo>/`.

**B) As a subfolder of a larger repo.** Commit the folder as-is and point GitHub Pages at it (root or `/docs` per your setup), or use a Pages action. Note that publishing the *whole* parent studio repo would also publish its internal docs — option A avoids that.

### Before you publish — one edit
Open `index.html` and replace the placeholder contact details in the closing call-to-action:
- the `href="#"` on the **«Κλείστε παρουσίαση»** button (e.g. a `mailto:` or a booking link), and
- the `[Όνομα] · [τηλέφωνο] · [email]` line just below it.
(Both are marked with a `TODO` comment in the HTML.)

## Notes

- **Simulated AI.** Every "AI" action in the demos is staged with canned Greek output keyed to your selections plus a brief typing/shimmer effect — there is no live model call and nothing leaves the browser. The site says so plainly.
- **Sample data.** All clients, projects and numbers are fictional but realistic, shared across the demos for continuity (Βίλα Εκάλη, εταιρικό campus Μαρούσι, roof garden Κολωνάκι, …).
- **Language.** All client-facing copy is Greek; the promise lines match the LaFlow teaser the client has already seen.
- Two known cosmetic nits carried over from the demos: the offer-drafter mobile grand-total «€» can wrap to its own line, and the project-diary header subtitle clips at ~375px width. Neither blocks use.
