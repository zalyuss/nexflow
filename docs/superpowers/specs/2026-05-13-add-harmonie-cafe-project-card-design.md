# Add Harmonie Café Project Card to `proiecte.html`

**Date:** 2026-05-13
**Scope:** Single-file edit on `proiecte.html`

## Goal

Add a new project card for **Harmonie Café** (live site: `harmoniero.cafe`) to the portfolio page. This is the first "Website" project on the page — all existing entries are chatbot / WhatsApp bot / voice agent automations.

## Context

- `proiecte.html` shows a grid of 6 cards, each linking to an internal detail page (`marin-auto.html`, `clinica-popa.html`, etc.).
- Filters above the grid: **Toate / Chatbot Site / WhatsApp Bot / Agent Vocal**.
- Each card has: gradient header, category badge, initials block, big metric, title, description, 3 tags, "Activ din [month]" footer, "Similar?" CTA.
- Brand identity of Harmonie Café (from the live site): deep forest green background + warm cream/gold accent + elegant serif typography.

## Changes

### 1. New filter button

Add a **„Website"** filter to the existing filter row, after „Agent Vocal":

```html
<button class="filter-btn" data-filter="website" onclick="filterProjects(this,'website')">Website</button>
```

No JS changes needed — the existing `filterProjects()` function already handles any `data-category` value.

### 2. New project card (Card 7)

Appended at the end of `#projects-grid`, after the LogiTrans card. Same structure as the others, with these values:

| Field | Value |
|---|---|
| `onclick` | `window.open('https://harmoniero.cafe','_blank')` (opens live site in new tab) |
| `data-category` | `website` |
| Gradient header | `linear-gradient(90deg, #1a4d3a, #d4a574)` (forest green → warm gold) |
| Badge text | `Website` |
| Badge color | Gold accent (`#d4a574` on `rgba(212,165,116,0.20)` background) |
| Initials | `HC` on green→gold gradient |
| Big metric | `LIVE` (text, not number) with green pulsing dot before it |
| Metric color | `#d4a574` (gold) |
| Metric subtitle | `site lansat și activ în Galați` |
| Title | `Harmonie Café` |
| Description | `Cafenea de specialitate din Galați. Site elegant cu meniu vizual filtrabil, galerie foto, locație și program — atmosferă premium care reflectă identitatea brandului.` |
| Tag 1 | `Meniu interactiv` |
| Tag 2 | `Galerie foto` |
| Tag 3 | `Hartă & program` |
| Bottom-left | `Lansat Mai 2026` (instead of „Activ din ...") with green pulsing dot |
| "Similar?" link color | `#d4a574` (gold) |

### 3. Click behavior — different from existing cards

All existing cards do `onclick="window.location.href='<page>.html'"` (internal navigation). The Harmonie card uses `window.open('https://harmoniero.cafe','_blank')` to open the live site externally. No detail page is created for this project.

## Out of scope

- Creating an internal `harmonie.html` detail page.
- Adding Harmonie Café to other pages (footer, index hero, testimonials).
- Adding additional website-category projects.
- Any styling refactor of `proiecte.html`.

## Acceptance criteria

- New „Website" filter appears in the tab row and is clickable.
- Clicking „Website" shows only the Harmonie Café card; clicking „Toate" shows all 7 cards.
- The Harmonie card visually matches the existing card layout (same proportions, same internal structure).
- Card color scheme is green→gold, distinct from all 6 existing cards.
- Clicking anywhere on the Harmonie card opens `https://harmoniero.cafe` in a new tab.
- Mobile view (≤768px): card displays in single column like the others.
- Tablet view (≤1024px): grid shows 2 columns; new card flows naturally.
- No regressions: existing 6 cards display and filter correctly.
