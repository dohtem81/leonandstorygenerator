---
name: "Add New Chapters"
description: "Use when multiple new Polish story files need to be processed. Accepts a range (e.g. 026-028), a list (e.g. 026 027 028), or auto-detects all missing files. Calls the Add New Chapter prompt once per chapter in order."
argument-hint: "e.g. 026-028  or  026 027 028  (range or space-separated list; omit to auto-detect)"
agent: "agent"
---

Multiple new Polish story files have been added to `stories/pl/`. Process them one by one using the **Add New Chapter** prompt.

## Input

The user may provide:
- A **range**: e.g. `026-028` — expand to `026`, `027`, `028`
- A **list**: e.g. `026 027 028` — use as-is
- **Nothing** — auto-detect all numbered `.txt` files present in `stories/pl/` but missing in `stories/en/`, sorted ascending

## Steps

### 1 — Resolve the chapter list

Based on the input above, produce an ordered list of zero-padded three-digit file numbers (e.g. `["026", "027", "028"]`).

### 2 — Process each chapter in order

For each number in the list, invoke the **Add New Chapter** prompt (`add-chapter.prompt.md`) with that number as the argument.

Wait for each chapter to be fully completed before starting the next one.

### 3 — Summary

After all chapters have been processed, print a short summary table:

| # | File | Polish title | English title |
|---|------|-------------|---------------|
| … | …    | …           | …             |

Confirm the final total chapter count and that all files, `chapters.txt` entries, `[chapter].astro`, and README are up to date.
