# Add Harmonie Café Project Card — Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Add a 7th project card for Harmonie Café (live site `harmoniero.cafe`) to `proiecte.html`, plus a new "Website" filter button. Card opens the external live site in a new tab.

**Architecture:** Single-file HTML edit. Reuses the existing `.project-card` class, `filterProjects()` JS function (which already handles arbitrary `data-category` values), and the same internal card structure as the 6 existing cards. New card uses a green→gold color scheme matching the live brand identity.

**Tech Stack:** Plain HTML + inline CSS + vanilla JS (no framework, no build step). Dev server: `node serve.mjs` on `http://localhost:3000`. Screenshot tool: `node screenshot.mjs <url>`.

---

## Task 1: Add „Website" filter button

**Files:**
- Modify: `proiecte.html:183` (filter row, inside `<div class="reveal" style="display:flex;gap:10px...">`)

- [ ] **Step 1: Add the new filter button**

Add after the „Agent Vocal" button (currently at line 182). The button reuses the existing `.filter-btn` styles and the existing `filterProjects()` function — no JS changes needed.

```html
<button class="filter-btn" data-filter="website" onclick="filterProjects(this,'website')">Website</button>
```

The full filter row should read:

```html
<div class="reveal" style="display:flex;gap:10px;flex-wrap:wrap;margin-bottom:48px;">
  <button class="filter-btn active" data-filter="all" onclick="filterProjects(this,'all')">Toate</button>
  <button class="filter-btn" data-filter="chatbot" onclick="filterProjects(this,'chatbot')">Chatbot Site</button>
  <button class="filter-btn" data-filter="whatsapp" onclick="filterProjects(this,'whatsapp')">WhatsApp Bot</button>
  <button class="filter-btn" data-filter="vocal" onclick="filterProjects(this,'vocal')">Agent Vocal</button>
  <button class="filter-btn" data-filter="website" onclick="filterProjects(this,'website')">Website</button>
</div>
```

- [ ] **Step 2: Do not commit yet** — Task 2 changes the same file. Single commit at end.

---

## Task 2: Add the Harmonie Café card

**Files:**
- Modify: `proiecte.html:372` (after Card 6 / LogiTrans closing `</div>`, before `</div><!-- end grid -->`)

- [ ] **Step 1: Insert the new card at the end of `#projects-grid`**

Place this HTML after the LogiTrans card (after the closing `</div>` of Card 6) and before `</div><!-- end grid -->`:

```html
      <!-- Card 7: Harmonie Café -->
      <div onclick="window.open('https://harmoniero.cafe','_blank')" style="cursor:pointer;" class="project-card" data-category="website">
        <div style="height:6px;background:linear-gradient(90deg,#1a4d3a,#d4a574);"></div>
        <div style="padding:32px;">
          <div style="display:flex;align-items:center;justify-content:space-between;margin-bottom:24px;">
            <div style="background:rgba(212,165,116,0.18);color:#d4a574;font-size:12px;font-weight:600;padding:4px 12px;border-radius:999px;border:1px solid rgba(212,165,116,0.28);font-family:'DM Sans',sans-serif;letter-spacing:0.06em;text-transform:uppercase;">Website</div>
            <div style="width:40px;height:40px;background:linear-gradient(135deg,#1a4d3a,#d4a574);border-radius:10px;display:flex;align-items:center;justify-content:center;font-family:'Syne',sans-serif;font-weight:700;font-size:14px;color:#fff;flex-shrink:0;">HC</div>
          </div>
          <div style="display:flex;align-items:center;gap:14px;margin-bottom:8px;">
            <div style="width:12px;height:12px;background:#22c55e;border-radius:50%;animation:pulse 2s infinite;flex-shrink:0;"></div>
            <div style="font-family:'Syne',sans-serif;font-size:3rem;font-weight:800;color:#d4a574;letter-spacing:-0.04em;line-height:1;">LIVE</div>
          </div>
          <div style="font-size:13px;color:rgba(255,255,255,0.45);margin-bottom:20px;font-family:'DM Sans',sans-serif;">site lansat și activ în Galați</div>
          <h3 style="font-size:18px;font-weight:700;color:#fff;margin-bottom:10px;letter-spacing:-0.01em;">Harmonie Café</h3>
          <p style="font-size:14px;color:rgba(255,255,255,0.60);line-height:1.65;margin-bottom:24px;">Cafenea de specialitate din Galați. Site elegant cu meniu vizual filtrabil, galerie foto, locație și program — atmosferă premium care reflectă identitatea brandului.</p>
          <div style="display:flex;gap:8px;flex-wrap:wrap;margin-bottom:24px;">
            <span style="background:rgba(255,255,255,0.06);color:rgba(255,255,255,0.55);font-size:12px;padding:3px 10px;border-radius:6px;font-family:'DM Sans',sans-serif;">Meniu interactiv</span>
            <span style="background:rgba(255,255,255,0.06);color:rgba(255,255,255,0.55);font-size:12px;padding:3px 10px;border-radius:6px;font-family:'DM Sans',sans-serif;">Galerie foto</span>
            <span style="background:rgba(255,255,255,0.06);color:rgba(255,255,255,0.55);font-size:12px;padding:3px 10px;border-radius:6px;font-family:'DM Sans',sans-serif;">Hartă &amp; program</span>
          </div>
          <div style="display:flex;align-items:center;justify-content:space-between;padding-top:20px;border-top:1px solid rgba(255,255,255,0.08);">
            <div style="display:flex;align-items:center;gap:6px;">
              <div style="width:7px;height:7px;background:#22c55e;border-radius:50%;animation:pulse 2s infinite;"></div>
              <span style="font-size:13px;color:rgba(255,255,255,0.45);">Lansat Mai 2026</span>
            </div>
            <a href="https://harmoniero.cafe" target="_blank" rel="noopener" onclick="event.stopPropagation();" style="font-size:13px;font-weight:600;color:#d4a574;text-decoration:none;display:flex;align-items:center;gap:4px;transition:color 0.2s;" onmouseover="this.style.color='#fff'" onmouseout="this.style.color='#d4a574'">
              Vezi site
              <svg width="14" height="14" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2.5"><path stroke-linecap="round" stroke-linejoin="round" d="M17 8l4 4m0 0l-4 4m4-4H3"/></svg>
            </a>
          </div>
        </div>
      </div>
```

Notes on the design:
- `onclick="window.open('https://harmoniero.cafe','_blank')"` — opens live site in new tab (different from other cards which navigate internally).
- The bottom-right link uses `event.stopPropagation();` so clicking it doesn't also fire the card's onclick (avoids opening two tabs).
- Bottom-left text is „Lansat Mai 2026" (not „Activ din ...") — flags it as a brand-new launch rather than implying a year of operation.
- Big metric is the text „LIVE" with a 12px pulsing green dot — visually parallel to the other metrics (same Syne font, same size, same color treatment) but signals presence not numbers.
- Color is `#1a4d3a` (forest green) → `#d4a574` (warm gold), matching the live site's palette and distinct from the 6 existing color schemes (purple / violet / green-bright / amber / cyan / pink).

---

## Task 3: Verify visually in browser

**Files:** none modified — verification only.

- [ ] **Step 1: Check if dev server is running**

Run: `curl -s -o /dev/null -w "%{http_code}" http://localhost:3000` (or open in browser)
Expected: `200`. If not 200, start the server: `node serve.mjs &` and wait 1-2 seconds.

- [ ] **Step 2: Screenshot the projects page**

Run: `node screenshot.mjs http://localhost:3000/proiecte.html harmonie-card`
Expected: New file `./temporary screenshots/screenshot-N-harmonie-card.png` exists.

- [ ] **Step 3: Read the screenshot and verify**

Use the Read tool on the new PNG. Check:
- 7 cards visible (6 existing + Harmonie Café at the end)
- Harmonie card uses green→gold gradient header
- „LIVE" displayed in gold with green pulsing dot
- Badge says „Website" in gold
- 3 tags visible: Meniu interactiv / Galerie foto / Hartă & program
- Bottom-left says „Lansat Mai 2026" with green pulsing dot
- Filter row shows „Website" button after „Agent Vocal"
- Layout: cards arranged in 3 columns on desktop, new card on row 3 leftmost
- No visual glitches, ghost cards, or broken layout

- [ ] **Step 4: Test the „Website" filter**

Run: `node screenshot.mjs "http://localhost:3000/proiecte.html#" harmonie-filter-test`

Manually test via a fresh browser visit:
1. Click „Website" filter button → only Harmonie card should be visible.
2. Click „Toate" → all 7 cards visible.
3. Click „Chatbot Site" → Harmonie card should NOT be visible.

If you can't manually click in this environment, inspect the JS: the existing `filterProjects()` at line 537 reads `data-category` and matches with `.includes(filter)`. Since the new card has `data-category="website"` and no other card includes "website" in its category, the filter logic works as-is.

- [ ] **Step 5: Fix any mismatches**

If any of the visual checks fail, edit `proiecte.html`, re-screenshot, re-verify. Per CLAUDE.md, do at least 2 comparison rounds before declaring done.

---

## Task 4: Commit

**Files:** Stage all changes to `proiecte.html`.

- [ ] **Step 1: Verify diff**

Run: `git diff proiecte.html`
Expected: Diff shows (1) new filter button line inside the filter row, (2) new 7th card block before `</div><!-- end grid -->`. No other changes.

- [ ] **Step 2: Commit**

```bash
git add proiecte.html docs/superpowers/specs/2026-05-13-add-harmonie-cafe-project-card-design.md docs/superpowers/plans/2026-05-13-add-harmonie-cafe-project-card.md
git commit -m "Add Harmonie Café (harmoniero.cafe) project card + Website filter"
```

- [ ] **Step 3: Verify commit**

Run: `git log --oneline -3`
Expected: New commit at top with the message above.

---

## Self-Review Notes

- **Spec coverage:** All 8 acceptance criteria from the spec are addressed — filter button (Task 1), card visuals + colors + content + click behavior (Task 2), responsive layout verified (Task 3), filter behavior verified (Task 3 Step 4), no regressions checked (Task 3 Step 3).
- **No placeholders.** All HTML and commands are complete.
- **Type/value consistency:** `data-category="website"` matches `data-filter="website"` matches `filterProjects(this,'website')`. Color `#d4a574` is used consistently across badge text, initials gradient stop, big metric, and CTA link.
- **TDD note:** No automated tests exist in this project (plain static HTML, no test harness). Visual verification via screenshot is the test, per project conventions in CLAUDE.md.
