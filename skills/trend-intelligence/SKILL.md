# trend-intelligence

Real-time fashion and lifestyle trend scanning powered by WebSearch. Produces seasonal trend reports, micro-trend alerts, and runway analysis summaries.

## When to invoke

Trigger phrases: "趨勢掃描" / "最新風向" / "這季流行什麼" / "runway report" / "trend report" / "市場趨勢" / "現在流行" / "macro trend" / "micro trend" / "WGSN style report" / "trend brief"

Also auto-invoked by `creative-direction` (Step 2) to anchor visual concepts.

## What this skill produces

1. **Seasonal Macro Brief** — 3–5 macro trend pillars for current/upcoming season with evidence
2. **Micro-Trend Radar** — fast-moving signals (3–6 months horizon) with source citations
3. **Category-Specific Trend Sheet** — drill into one style vertical (tech-wear / luxury / sportswear etc.)
4. **Competitive Signal Report** — what key brands are pushing right now

## Process

### Step 1 — Scope Definition
Clarify before searching:
- **Style category** (menswear / womenswear / luxury / sportswear / street / tech-wear / unisex)
- **Geography focus** (global / Asia-Pacific / Europe / North America)
- **Time horizon** (current season SS/FW + next season preview)
- **Price tier** (mass / contemporary / premium / luxury / ultra-luxury)

### Step 2 — Multi-Source WebSearch

Run searches across these source categories:

**Runway & Editorial**
- `[season] [category] runway trends [year]` — Vogue Runway, WWD, Business of Fashion
- `[brand] [season] collection key pieces [year]`

**Consumer & Social Signal**
- `[category] trending [geography] [year]` — Pinterest Predicts, Google Trends fashion
- `TikTok fashion trend [category] [year]`

**Industry Reports**
- `McKinsey State of Fashion [year]` (annual)
- `[category] market trend report [year]`
- `sustainable fashion trend [year]` (if relevant)

Run at minimum **4 searches** before drafting. Cite every claim.

### Step 3 — Trend Synthesis

Organize findings into this structure:

```
## [Season/Year] Trend Brief: [Category]

### Macro Pillars (3–5)
Each pillar:
- Pillar Name: [memorable label]
- Signal: [what you're seeing across runway / retail / social]
- Evidence: [2–3 specific examples with sources]
- Brand Window: [how this brand can enter / what to avoid]
- Shelf Life: [emerging / building / peak / fading]

### Micro-Trend Radar
Fast-moving items to watch (3–6 month window):
- [Item / silhouette / color / material] — Signal: [where it's appearing] — Risk: [fad vs. staying power]

### Key Brand Movements
What 3–5 relevant brands are pushing this season:
- [Brand]: [what they're doing and why it matters]

### Macro Context
1–2 cultural / economic forces shaping the season:
- [Force]: [how it translates to product / aesthetic choices]

### Watch List (Next Season Preview)
2–3 signals that will likely build for next season.
```

### Step 4 — Brand Filtering (if brand config exists)
Cross-reference findings with brand's established aesthetic and rejected territory. Flag:
- ✅ Trends that align with brand DNA
- ⚠️ Trends that require careful interpretation
- ❌ Trends to actively avoid (competitor territory or off-brand)

## Rules

- **Never cite trend names from memory alone** — verify with WebSearch that the term is currently being used in the industry.
- Date all searches. Fashion trends expire fast; a report from 6+ months ago is noise, not signal.
- Distinguish **macro** (2–3 year arc) from **micro** (1–2 season window). Conflating them misleads clients.
- If geography focus is Asia-Pacific, prioritize Korean / Japanese / Taiwanese market signals — Western-centric reports often lag 1–2 seasons on AP adoption.
- Output in the user's language (繁中 / EN follow context).
