# lookbook-generator

Generate a print-quality fashion lookbook as a self-contained HTML file, then render it to PDF via playwright-pdf. Produces editorial-grade output — cover spread, brand statement, look pages, color story, credits — ready for client delivery or pitch deck attachment.

## When to invoke

Trigger phrases: "做 lookbook" / "幫我生成 lookbook" / "時尚 editorial" / "lookbook PDF" / "做型錄" / "客戶型錄" / "look book" / "fashion editorial" / "lookbook generator" / "把這季造型整理成 lookbook" / "做給客戶的季度造型書"

## What this skill produces

1. **`lookbook_[brand]_[season].html`** — self-contained single-file HTML (inline CSS, no external deps, print-optimized)
2. **`lookbook_[brand]_[season].pdf`** — rendered via playwright-pdf, A4 portrait, print quality
3. **Image placeholder comments** — `<!-- REPLACE: ... -->` markers for easy photo drop-in
4. **Design token integration** — uses brand's color / typography tokens if available

## Lookbook page structure (default 8-page A4)

| Page | Content |
|---|---|
| 1 | Cover — brand name, season label, hero image placeholder |
| 2 | Brand Statement — season message (2–3 sentences) + editorial image |
| 3–6 | Look pages — 1 look per page: image placeholder + styling notes |
| 7 | Color Story — season palette swatches + names + brand application |
| 8 | Credits + contact / CTA |

Page count is adjustable. Default is 8. Minimum is 4 (cover + statement + 2 looks + credits merged).

## Process

### Step 1 — Content Intake

Gather or infer from context:

- **Brand name** + primary color + secondary color (hex)
- **Season label** (e.g., "SS 2026" / "FW 2026 / 2027")
- **Number of looks** to feature (default: 4)
- **Brand tagline / season message** (1–2 sentences)
- **Look descriptions** — for each look: name, key pieces, styling note, occasion
- **Color story** — 3–5 colors with names (if not already in brand config)
- **Credits** — photographer, stylist, model (can be TBD)

If brand config folder exists (`brand/brand_guidelines.md`, `brand/target_audience.md`), read it first — use existing brand colors, typography, and tone. Do not re-ask what's documented.

If `seasonal-curation` has been run in this session, pull the color story and trend pillars from that output instead of starting fresh.

### Step 2 — Design Token Setup

Define the HTML/CSS design system for this lookbook:

```
Primary color:    [from brand or user input]
Secondary color:  [from brand or user input]
Accent:           [derived — complementary or split-complementary]
Background:       [white #FFFFFF or near-black #0F0F0F — user chooses]
Text on dark:     #FFFFFF
Text on light:    #0F0F0F
Display font:     [serif for luxury/editorial OR sans for modern/streetwear]
Body font:        [clean sans-serif]
```

**Light vs. Dark base** — ask if not clear from brand config:
- Light base → editorial, luxury, resort feel
- Dark base → nightlife, street, high-drama editorial

### Step 3 — Generate HTML

Output a complete, self-contained HTML file. Template structure:

```html
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
<meta charset="UTF-8">
<style>
/* ── Reset & Page Setup ─────────────────────────── */
@page { size: A4 portrait; margin: 0; }
* { margin: 0; padding: 0; box-sizing: border-box; }

/* ── Design Tokens ──────────────────────────────── */
:root {
  --c-primary:   [hex];
  --c-secondary: [hex];
  --c-accent:    [hex];
  --c-bg:        [hex];
  --c-text-hi:   [hex];
  --c-text-lo:   [hex];
  --font-display: '[Display Font]', Georgia, serif;
  --font-body:    '[Body Font]', Arial, sans-serif;
}

/* ── Page Shell ─────────────────────────────────── */
.page {
  width: 210mm;
  min-height: 297mm;
  overflow: hidden;
  page-break-after: always;
  position: relative;
  background: var(--c-bg);
  color: var(--c-text-hi);
}
.page:last-child { page-break-after: auto; }

/* ── Image Placeholders ─────────────────────────── */
.img-placeholder {
  background: linear-gradient(135deg, var(--c-primary) 0%, var(--c-secondary) 100%);
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: var(--font-body);
  font-size: 11px;
  letter-spacing: 0.15em;
  text-transform: uppercase;
  color: rgba(255,255,255,0.6);
}
</style>
</head>
<body>

<!-- PAGE 1: COVER -->
<div class="page" id="cover">
  <!-- REPLACE: hero image → [brief description of hero shot] -->
  <div class="img-placeholder" style="width:100%;height:70%;">[HERO IMAGE]</div>
  <div class="cover-text">
    <h1>[BRAND NAME]</h1>
    <p class="season-label">[SEASON]</p>
    <p class="tagline">[TAGLINE]</p>
  </div>
</div>

<!-- PAGE 2: BRAND STATEMENT -->
...

<!-- PAGE 3–N: LOOK PAGES -->
...

<!-- FINAL PAGE: CREDITS -->
...

</body>
</html>
```

**Image placeholder rule**: Every placeholder must include a `<!-- REPLACE: ... -->` comment immediately above it with a clear description of what photo should go there. Placeholders use CSS gradients that feel intentional, not broken.

**Typography scale for A4 print** (larger than screen — print px ≈ 96dpi but A4 layout assumes ~150dpi visual weight):

```css
.cover-title    { font-size: 72px; line-height: 1.0; letter-spacing: -0.02em; }
.section-title  { font-size: 48px; line-height: 1.1; }
.look-title     { font-size: 32px; line-height: 1.2; }
.body-text      { font-size: 14px; line-height: 1.6; }
.caption        { font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase; }
.micro          { font-size: 9px;  letter-spacing: 0.2em;  text-transform: uppercase; }
```

### Step 4 — Look Page Layout (per look)

Each look page follows this pattern (choose from 2 layout variants):

**Layout A — Image dominant (80% image)**
```
┌──────────────────┐
│                  │
│  [LOOK IMAGE]    │  ← 80% height
│                  │
├──────────────────┤
│ LOOK 01   NAME   │  ← look number + name
│ Styling notes    │  ← 2–3 lines max
│ Key pieces       │  ← bulleted, 2–4 items
└──────────────────┘
```

**Layout B — Split (50/50 image/text)**
```
┌────────┬─────────┐
│        │  LOOK   │
│ IMAGE  │  NAME   │
│        │         │
│        │ Styling │
│        │ notes   │
│        │         │
│        │ • piece │
│        │ • piece │
└────────┴─────────┘
```

Use Layout A for hero looks; Layout B for detailed editorial notes.

### Step 5 — Color Story Page

Display the season's color palette as editorial swatches:

```
┌──────────────────────────────────────────┐
│  COLOR STORY  [SEASON]                   │
│                                          │
│  ██████  ██████  ██████  ██████  ██████  │
│  [NAME]  [NAME]  [NAME]  [NAME]  [NAME]  │
│  #hex    #hex    #hex    #hex    #hex     │
│                                          │
│  [One-line color narrative]              │
└──────────────────────────────────────────┘
```

### Step 6 — Save & Render

1. Save the generated HTML to `lookbook_[brand-slug]_[season-slug].html` in the current working directory (or `OUTPUTS/` if the project has that structure).

2. Invoke playwright-pdf:
   - Input: the saved HTML file
   - Output: `lookbook_[brand-slug]_[season-slug].pdf`
   - Format: A4 portrait, `printBackground: true`

3. Confirm both files exist and report their paths.

## Rules

- **No external dependencies** — the HTML must be self-contained (inline CSS, no CDN fonts, no remote images). Web fonts can be loaded from Google Fonts `@import` only if user explicitly requests; default to system fonts for print reliability.
- **Image placeholders are required** — never leave a layout empty without a placeholder + `<!-- REPLACE -->` comment. The lookbook must look intentional even before real photos are inserted.
- **Print-first CSS** — use `mm` units for page structure, avoid `vh/vw` for page layout, no hover states, no animations.
- **Brand config wins** — if design tokens exist in the brand config, use them. Do not invent a new palette if one is already defined.
- **Honest placeholders** — gradient backgrounds should use the brand's actual primary/secondary colors so the placeholder reads as a brand-colored editorial block, not a broken image.
- **Playwright-pdf hand-off** — always invoke `playwright-pdf` skill at Step 6. Do not deliver only the HTML without the PDF.
- Output in the user's language (繁中 / EN follow context); lookbook content language follows the brand's market (e.g., 繁中 copy for Taiwan clients).
