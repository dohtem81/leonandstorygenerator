# Changelog

## v1.1.2 — Illustrated Holidays (2026-05-26)

### New chapters

Three new holiday adventure chapters added in both Polish and English:

| # | Polish | English |
|---|--------|---------|
| 26 | Wakacyjny Cookout | Holiday Cookout |
| 27 | Smocze Jajka | Dragon Eggs |
| 28 | Planeta Pink | Planet Pink |

### Chapter illustrations

Each of the first 24 chapters now displays its own illustration on the story page.
A single sprite sheet (`chapters-sprite.png`) is cropped at runtime using CSS `background-position` — no extra requests, no image processing. Chapters 25–28 are not yet illustrated.

### Workflow tooling

Two Copilot agent prompts for adding chapters:

- **`/add-chapter`** — processes a single new chapter (translate, update chapters.txt, update site, update README)
- **`/add-chapters`** — accepts a range (`026-028`) or list (`026 027 028`), calls `/add-chapter` once per chapter in order, prints a summary on completion

---

## v1.0.0 — Initial release (2026-05-01)

25 chapters published in Polish and English.
Static website live at [leon-and-storygenerator.netlify.app](https://leon-and-storygenerator.netlify.app/).
