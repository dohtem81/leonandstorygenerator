# Bajkogenerator / The Storygenerator

A bedtime story that got out of hand — in the best way.

---

## How this started

It was late. My son needed a story. No light, just wind-him-down time, and I had nothing left in the tank.

So I opened ChatGPT, gave it a few hints about what I wanted — a boy, a magic device, something about pancakes — and the first chapter was there in seconds.

He loved it.

That was three weeks ago. Since then I've been sitting down every few days, shaping the next chapter, nudging the direction, adding the running jokes and recurring characters that he keeps asking about. 28 chapters later, here we are.

These stories didn't write themselves — AI gave me the raw material, but every chapter went through rounds of "no, make him more scared here" and "the dragon needs to be funnier" and "can the sausage come back?". It became a proper collaborative thing, just between me, my son, and a language model at midnight.

---

## What this is

**Bajkogenerator** (Polish: *Story Generator*) is a short chapter-book for kids, available in both Polish and English.

It follows **Leon** and his magical device — the Bajkogenerator — a small glowing box on a wooden desk that pulls him into a different story every time he clicks it.

The stories are:
- Short enough for bedtime (one chapter = one night)
- Funny and a little weird (pancake castles, rhyming turtles, sausage-related subplots)
- Warm at the core — each one is really about something small and human

---

## Chapters

| # | Polski | English |
|---|--------|---------|
| 1 | Pierwsze kliknięcie | The First Click |
| 2 | Kolekcjoner zakończeń | The Collector of Endings |
| 3 | Smok bez skrzydeł | The Dragon Without Wings |
| 4 | Złamany statek | The Broken Ship |
| 5 | Chłopiec, który napisał swoją historię | The Boy Who Wrote His Own Story |
| 6 | Efekt historii | The Effect of a Story |
| 7 | Mała sprawa | A Small Thing |
| 8 | Niewidoczne przyciski | Invisible Buttons |
| 9 | Gorszy dzień | A Bad Day |
| 10 | W przestrzeń kosmiczną | Into Space |
| 11 | Kiedy historie się zderzają | When Stories Collide |
| 12 | Strefa ciszy | The Zone of Silence |
| 13 | Zaginiony smak | The Missing Flavour |
| 14 | Idealna kiełbasa | The Perfect Sausage |
| 15 | Historia o złości | The Story of Anger |
| 16 | Chłopiec, który nie chciał tańczyć | The Boy Who Didn't Want to Dance |
| 17 | Smok napędowy | Dragon-Powered |
| 18 | Książę Naleśnikonu | Prince of Pancakeon |
| 19 | Noc w muzeum zagubionych historii | Night at the Museum of Lost Stories |
| 20 | Piekielna kiełbasa kosmiczna | Cosmic Hellfire Sausage |
| 21 | Symulacja stresu scenicznego | Stage Stress Simulation |
| 22 | Planeta Na Opakową | Planet Upside-Down |
| 23 | Ostatnie cztery dni | The Last Four Days |
| 24 | Balonowa zasadzka | The Balloon Ambush |
| 25 | Planeta Pancakea | Planet Pancakea |
| 26 | Wakacyjny Cookout | Holiday Cookout |
| 27 | Smocze Jajka | Dragon Eggs |
| 28 | Planeta Pink | Planet Pink |

---

## Read online

**[leon-and-storygenerator.netlify.app](https://leon-and-storygenerator.netlify.app/)**

The stories are published as a static website built with [Astro](https://astro.build) and hosted on Netlify — dark sky, parchment pages, glowing gold text. Felt right for a magic story.

---

## For other parents

If any of these make your kid laugh, or help you get through a late-night "just one more story", that's the whole point. Take them, read them, skip the chapters that don't land, add your own details. The Bajkogenerator belongs to whoever needs it that night.

---

## Adding new chapters

New chapters are written in Polish first and saved as `stories/pl/<NNN>.txt`. That's all — the agent takes care of everything else.

There are two Copilot prompts for this. Open any Copilot chat in VS Code and use:

**Single chapter:**
```
/add-chapter 026
```
With no argument it will detect the one Polish file that is missing an English counterpart automatically.

**Multiple chapters** (range or list):
```
/add-chapters 026-028
/add-chapters 026 027 028
```
With no argument it detects all missing files and processes them in order. It calls `/add-chapter` once per chapter, waiting for each to finish before starting the next, then prints a summary table.

Each run of `/add-chapter` will:
1. Translate the new Polish story to English and save it in `stories/en/`
2. Append the new chapter title to `stories/pl/chapters.txt` and `stories/en/chapters.txt`
3. Update the hardcoded chapter count in `web/src/pages/[lang]/[chapter].astro`
4. Add the new row to the README chapter table and update the chapter count in the intro

The prompt files live at `.github/prompts/add-chapter.prompt.md` and `.github/prompts/add-chapters.prompt.md`.

---

## Tech

- Stories: plain `.txt` files, one per chapter, in `stories/pl/` and `stories/en/`
- Website: [Astro](https://astro.build) static site in `web/`
- Hosting: Netlify (auto-deploys on push)
- Analytics: GoatCounter (privacy-friendly, no cookie banner)
