# seasonal-curation

Produces structured seasonal fashion trend packages — curated, filtered through a specific brand's lens, and ready for client delivery. This is the paid-tier's core deliverable skill.

## When to invoke

Trigger phrases: "季度趨勢包" / "幫我做 SS2026 / FW2026 趨勢" / "seasonal trend report" / "這季流行什麼幫我整理成客戶版本" / "trend curation" / "策展包" / "seasonal brief"

Also invoked by `output-generator` when building a full client deck that requires a trend anchor.

## What this skill produces

1. **Curated Seasonal Brief** — 5 macro trend pillars, each filtered through the brand's lens
2. **Color Strategy** — season's key colors mapped to brand's existing palette
3. **Styling Direction** — how the trends translate to actual product / styling decisions
4. **Next-Season Early Signals** — 2–3 emerging signals to watch
5. **Client-Ready Output** — formatted for Gamma deck or PDF delivery

## Difference from trend-intelligence

| `trend-intelligence` | `seasonal-curation` |
|---|---|
| Research tool | Deliverable tool |
| Raw trend data | Brand-filtered interpretation |
| For internal use | For client presentation |
| No styling guidance | Includes styling decisions |
| Single-use | Repeatable seasonal cadence |

## Process

### Step 1 — Season & Brand Scoping
Confirm:
- **Season**: SS (Spring/Summer, Jan–Jun runway) or FW (Fall/Winter, Sep–Oct runway)
- **Year**: Current or next
- **Brand**: Read brand config if exists (`brand/brand_guidelines.md`, `brand/target_audience.md`)
- **Delivery format**: Gamma deck / PDF / Markdown doc

### Step 2 — Multi-Source Research (WebSearch)

Minimum 6 searches across:

**Runway Sources**
- `[Season][Year] runway trends key looks` → Vogue Runway, WWD, Business of Fashion
- `[Season][Year] fashion week trends summary` → Harper's Bazaar, Who What Wear

**Color Intelligence**
- `[Season][Year] color trends Pantone` → official color authority
- `[Season][Year] color trends [target geography]` → regional adoption

**Asia-Pacific Filter** (always run if brand is Asia-based)
- `Korean fashion trends [Season][Year]`
- `[Taiwan/Japan] fashion trend [Season][Year]`

**Consumer Signal**
- `[Season][Year] fashion trend social media TikTok Pinterest`

### Step 3 — Brand Filtering

For each identified macro trend, apply the brand filter:

```
Trend: [name]
Global Signal: [what's happening globally]
AP Signal: [Asia-Pacific specific manifestation]
Brand Verdict:
  ✅ Adopt — [why it fits + how to apply]
  ⚠️ Adapt — [what to keep, what to modify for brand fit]
  ❌ Skip — [why it conflicts with brand DNA / rejection list]
Brand Application: [concrete styling / product / visual direction]
```

**Never include a trend the brand should skip** in the client deliverable — only ✅ and ⚠️ (adapted) trends go to the client.

### Step 4 — Color Strategy

Build a season-specific color map:

```
Season Color     | Status    | Brand Application
──────────────── | ───────── | ──────────────────
[Color A]        | ★★★★★    | [how brand uses it]
[Color B]        | ★★★★☆    | [specific touchpoint]
[Brand's Core]   | Evergreen | [reinforce — not trend-dependent]
[Skip Color]     | ★★☆☆☆    | [why skip for this brand]
```

### Step 5 — Styling Direction

Translate macro trends into concrete decisions:

For **apparel / SG styling**:
- Silhouette priority (1–2 shapes to adopt this season)
- Texture / material direction
- Key accessory moment (what's the one statement piece)
- What to retire from last season

For **brand visual / UI / marketing**:
- Which trend informs campaign photography aesthetic
- Which color enters the visual system (even temporarily)
- Motion / energy direction for this season's content

### Step 6 — Assembly & Delivery

Structure the final deliverable:

```markdown
# [Brand] × [Season][Year] Trend Package

## 本季總精神 (1 paragraph — the season's emotional register)

## 五大 Macro 趨勢
[For each: name / global signal / AP signal / brand application / styling direction]

## 色彩策略
[Season color map + brand palette update]

## 造型方向
[Concrete styling decisions for this brand's specific context]

## 下季早期信號
[2–3 emerging trends to monitor]

## 資料來源
[All WebSearch URLs cited]
```

Then hand off to `output-generator` for Gamma / PDF packaging.

### Seasonal Cadence (for ongoing client relationships)

| Delivery | Timing | Contents |
|---|---|---|
| SS Trend Package | December–January | Full SS brief (5 pillars + color + styling) |
| SS Mid-Season Update | April | Micro-trend alert (what's actually selling / trending) |
| FW Trend Package | June–July | Full FW brief |
| FW Mid-Season Update | October | Micro-trend alert |

This cadence = 4 deliverables/year per client = subscription value proposition.

## Rules

- Every trend claim must be sourced from a WebSearch result in this session. No training-data trend names.
- Always run the AP filter — Western runway trends often land 1–2 seasons late in Taiwan/Korea.
- Skip trends that conflict with brand rejection list. Client deliverables only show what's relevant to them.
- Date-stamp the package (curated date + applicable season window).
- Output in the user's language (繁中 / EN follow context).
