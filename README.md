# Dr. Emilyn Navia-Lagazon, PHD — The Physics Educator

A fully **offline, single-file** professional website for Dr. Emilyn Navia-Lagazon, PHD —
Senior International Physics Educator (Australia HSC · UK IGCSE & A Level · US AP Physics).

## Features

- **About Me** — profile, education and specialisation, curricula taught
- **Recent Stories** — conference, graduation, keynote and RoboRAVE highlights with photo slideshows
- **Curriculum I Taught** — Overview & Syllabus for Australia (HSC), UK (IGCSE & A Level), US (AP Physics)
  - NSW Stage 6 syllabus versions: **Physics Stage 6 (2017)** and the new **Physics 11–12 (2025)**, implemented from 2027
- **Resources** — past papers, trial papers & references, plus a **downloadable past-paper & marking-guidelines archive (2019–2025)**
- **Gallery** — archives of the teaching journey across the Philippines and China, with country filter
- **Social Activities** — community, leadership and Kiwanis International (KCDM Chapter) slideshow
- **Interactive physics demos** — pendulum, projectile motion and wave simulations (canvas-based)

## Fully offline — no network required

Everything is embedded directly into one file:

- All photographs are inlined as **data URIs** (no external image requests)
- All styles and scripts are inline — **no CDNs, no web fonts, no frameworks**
- The physics demos are drawn with the HTML `<canvas>` API and run entirely client-side

Open `index.html` in any modern browser and the whole site works, including navigation,
tabs, gallery filtering, slideshows and the interactive demos.

> **Note:** `index.html` is large (~16 MB) because every photo is embedded as base64.
> This is intentional — it is what makes the site work with no internet connection.

## Video files (optional)

Four video slots look for local `.mp4` files placed next to `index.html`. If a file is
absent, each player shows a friendly upload prompt instead — nothing breaks:

| Slot | Filename |
| --- | --- |
| Catapult Competition highlights | `catapult.mp4` |
| Catapult Competition highlights (2) | `catapult2.mp4` |
| Electroscope demo | `electroscope.mp4` |
| Awarding of the Certificate | `certificate.mp4` |

## Past-paper archive (optional)

The **Past Papers & Marking Guidelines** download folder looks for PDFs in a `papers/`
folder next to `index.html`, one pair per year from 2019 to 2025:

```
papers/hsc-physics-2019-past-paper.pdf
papers/hsc-physics-2019-marking-guidelines.pdf
...
papers/hsc-physics-2025-past-paper.pdf
papers/hsc-physics-2025-marking-guidelines.pdf
```

Drop the real NESA PDFs into that folder and the download buttons will serve them.

## Hosting on GitHub Pages

Because the site is a single static file, GitHub Pages works with no build step:

1. Push this repository to GitHub
2. **Settings → Pages → Source: Deploy from a branch**
3. Choose `main` / root, then Save
4. Your site is live at `https://<username>.github.io/<repo>/`

No `_config.yml`, bundler or Jekyll setup is needed.

## Local development

No server or build required — just open the file:

```bash
open index.html          # macOS
xdg-open index.html      # Linux
start index.html         # Windows
```

Or serve it locally if you prefer:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Repository contents

| Path | Description |
| --- | --- |
| `index.html` | The entire website (all content, styles, scripts and images) |
| `uploads/` | Original source photographs (not referenced by the page — the page uses embedded copies) |
| `papers/` | Optional past papers & marking guidelines, 2019–2025 |
