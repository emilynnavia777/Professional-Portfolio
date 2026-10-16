# Papers — Past Papers & Marking Guidelines (2019–2025)

Place the HSC Physics PDFs in this folder. The **Past Papers & Marking Guidelines**
download archive on the website serves files from here.

## Expected filenames

One pair per year, 2019 through 2025:

```
hsc-physics-2019-past-paper.pdf
hsc-physics-2019-marking-guidelines.pdf
hsc-physics-2020-past-paper.pdf
hsc-physics-2020-marking-guidelines.pdf
hsc-physics-2021-past-paper.pdf
hsc-physics-2021-marking-guidelines.pdf
hsc-physics-2022-past-paper.pdf
hsc-physics-2022-marking-guidelines.pdf
hsc-physics-2023-past-paper.pdf
hsc-physics-2023-marking-guidelines.pdf
hsc-physics-2024-past-paper.pdf
hsc-physics-2024-marking-guidelines.pdf
hsc-physics-2025-past-paper.pdf
hsc-physics-2025-marking-guidelines.pdf
```

If a filename differs, update the matching `data-f="…"` attribute on the
`.pp-btn` buttons in `index.html` (search for `pp-btn`).

## Publishing these PDFs to the repo

PDFs are ignored by default (see `.gitignore`) so the repository stays small and
GitHub Pages-friendly. To publish them, remove this line from `.gitignore`:

```
papers/*.pdf
```

Then commit and push. Note that GitHub Pages serves a maximum site size of 1 GB,
and individual files over 50 MB trigger a warning (100 MB is a hard limit).
