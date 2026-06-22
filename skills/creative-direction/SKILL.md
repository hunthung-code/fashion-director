# creative-direction

AI Creative Director for brand and product visual concepts. Generate moodboards, design token systems, color stories, and visual direction documents.

## When to invoke

Trigger phrases: "做 moodboard" / "視覺方向" / "設計定調" / "色彩系統" / "品牌調性" / "concept brief" / "creative direction" / "define the look" / "給視覺規範" / "風格定義"

## What this skill produces

1. **Moodboard Brief** — concept name, aesthetic pillars (3–5), reference universe, what to avoid
2. **Color Story** — primary / secondary / accent palette with hex codes, usage rationale, seasonal context
3. **Design Token Draft** — typography scale, spacing rhythm, border radius, motion signature, surface treatment
4. **Visual Direction Doc** — one-page PDF-ready summary combining all of the above

## Process

### Step 1 — Brand Intake (2 min)
Ask or infer from context:
- **Who is the customer?** (age, lifestyle, occasion)
- **What is the product / service?** (category, price point)
- **What 3 adjectives does the brand own?** (e.g., "bold / clean / feminine")
- **What must be avoided?** (competitor territory, past mistakes, off-brand signals)

If a brand config folder exists (e.g., `payshow-config/brand/`), read it first — do NOT re-ask what's already documented.

### Step 2 — Trend Anchor (use trend-intelligence if needed)
- Call `/trend-intelligence` to get current macro context for the relevant style category
- Identify which 1–2 macro trends the brand can credibly ride vs. must avoid

### Step 3 — Moodboard Concept
Generate 2–3 concept directions (not just one). For each:

```
Direction Name: [poetic, memorable title]
Aesthetic Pillars: [3 words that define it]
Color Story: [primary hex] + [secondary hex] + [accent hex] + rationale
Typography Feel: [serif / sans / display — and emotional register]
Texture / Material Language: [matte / gloss / soft / industrial / organic...]
Key Reference Universe: [3–4 cultural / brand / art references — verified real]
Motion Signature: [how things move on this brand]
What We Reject: [1–2 things that would kill the vibe]
```

Present all 3 directions briefly, then recommend one with reasoning.

### Step 4 — Design Token System (if confirmed direction)
Output as CSS custom properties format — immediately usable:

```css
/* [Brand] Design Tokens v0.1 */
:root {
  /* Color */
  --color-bg:        #...;
  --color-surface:   #...;
  --color-primary:   #...;
  --color-accent:    #...;
  --color-text-hi:   #...;
  --color-text-lo:   #...;
  --color-border:    #...;

  /* Typography */
  --font-display:    '[Font Name]', serif;
  --font-body:       '[Font Name]', sans-serif;
  --text-xs:  0.75rem;
  --text-sm:  0.875rem;
  --text-base: 1rem;
  --text-lg:  1.25rem;
  --text-xl:  1.5rem;
  --text-2xl: 2rem;
  --text-hero: 3.5rem;

  /* Spacing */
  --space-1: 4px; --space-2: 8px; --space-3: 12px;
  --space-4: 16px; --space-6: 24px; --space-8: 32px;
  --space-12: 48px; --space-16: 64px;

  /* Shape */
  --radius-sm:  4px;
  --radius-md:  8px;
  --radius-lg: 16px;
  --radius-pill: 999px;

  /* Motion */
  --ease-snappy: cubic-bezier(0.25, 0, 0.1, 1);
  --ease-soft:   cubic-bezier(0.4, 0, 0.2, 1);
  --duration-fast:   150ms;
  --duration-normal: 300ms;
  --duration-slow:   500ms;
}
```

### Step 5 — Visual Direction Doc (optional, on request)
Compile into a Markdown doc suitable for `output-generator` to render as PDF or Gamma deck.

## Rules

- Reference universes must be **real, verifiable** brands / artists / campaigns. Use WebSearch to confirm before citing.
- Color palettes must pass WCAG AA contrast (text on background). Check before finalizing.
- Always give the brand something to **say no to** — the rejection list is as important as the affirmations.
- If brand config exists, read it before generating. Do not override established brand DNA unless user explicitly asks to.
- Output in the user's language (繁中 / EN follow context).
