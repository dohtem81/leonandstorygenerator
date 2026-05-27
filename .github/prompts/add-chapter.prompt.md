---
name: "Add New Chapter"
description: "Use when a new Polish story file has been added to stories/pl/ and needs to be translated to English, chapters.txt updated in both languages, and the website chapter count updated."
argument-hint: "e.g. 026  (file number without .txt)"
agent: "agent"
---

A new Polish story file has been added to `stories/pl/`. Complete all steps below.

## Input

The user may specify a file number as an argument (e.g. `026`).
If no argument is given, detect the new file automatically by comparing `stories/pl/` against `stories/en/` — the numbered `.txt` file present in `pl/` but missing in `en/` is the new one.

## Steps

### 1 — Read Polish source file

Read the full content of `stories/pl/<NNN>.txt`.

### 2 — Derive chapter titles

The new story file does not yet have an entry in `chapters.txt`. Read the full story content and derive a concise, fitting Polish chapter title (noun phrase, consistent with the style of existing Polish titles in `stories/pl/chapters.txt`). Then produce an English equivalent matching the style of existing English titles in `stories/en/chapters.txt` (concise, title-case noun phrase).

### 3 — Translate to English

Translate each Polish story to English following these rules:
- Match the tone, rhythm and formatting of the existing English stories in `stories/en/` exactly
- Keep all dialogue dashes (`—`), bold markers (`**…**`), horizontal rules (`---`), italics, and emoji
- "Bajkogenerator" → "Storygenerator", "Iskra 7" → "Spark 7"
- Preserve all sound-effect words in a natural English equivalent (e.g. `PRRT`, `BŁUP`, `PLASK` → `PRRT`, `BLUP`, `SPLAT`)
- Keep the song/poem stanzas rhyming in English where the Polish original rhymes

### 4 — Save English translation

Write each translated story to `stories/en/<NNN>.txt`.

### 5 — Update chapters.txt (Polish)

Append a new line to `stories/pl/chapters.txt` for the new chapter, following the exact format of existing lines:
```
Rozdział <N> — <Polish title>
```

### 6 — Update chapters.txt (English)

Append a new line to `stories/en/chapters.txt` for the new chapter:
```
Chapter <N> — <English title>
```

### 7 — Update website chapter count

Open `web/src/pages/[lang]/[chapter].astro`.
Find the two hardcoded numbers that cap the chapter range:
- the upper bound in `for (let i = 1; i <= <N>; i++)` inside `getStaticPaths`
- `const totalChapters = <N>;`

Update both to the new total chapter count.

### 8 — Update README

In `README.md`, update the chapters table by appending a row for the new chapter:
```
| <N> | <Polish title> | <English title> |
```
Also update the sentence "X chapters later, here we are." to the new total.

## Verification

After completing all steps, confirm:
- `stories/en/<NNN>.txt` exists and has the full translated content
- `stories/pl/chapters.txt` and `stories/en/chapters.txt` both list the new chapter
- `[chapter].astro` loop bound and `totalChapters` both equal the new total
- README table includes the new chapter
