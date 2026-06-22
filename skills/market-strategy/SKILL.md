# market-strategy

Fashion market intelligence and business strategy. Produces market sizing, competitive landscape maps, brand positioning matrices, and pricing architecture recommendations.

## When to invoke

Trigger phrases: "市場規模" / "TAM SAM SOM" / "競品分析" / "定價策略" / "市場定位" / "競爭對手" / "market sizing" / "competitive analysis" / "pricing" / "brand positioning" / "市場機會" / "這個市場有多大" / "我要進入 [category]"

## What this skill produces

1. **Market Sizing** — TAM / SAM / SOM with sources and methodology
2. **Competitive Landscape Map** — positioning matrix of 6–10 key players
3. **White Space Analysis** — underserved segments and positioning opportunities
4. **Pricing Architecture** — price ladder by tier, with psychological anchoring rationale
5. **Go-to-Market Angle** — recommended entry point and differentiation thesis

## Process

### Step 1 — Market Definition
Clarify:
- **Category & sub-category** (e.g., "women's activewear, premium tier, Asia-Pacific")
- **Geography** (country / region)
- **Customer segment** (demographics, psychographics, occasion)
- **Business model** (DTC / wholesale / marketplace / brand licensing)

### Step 2 — Market Sizing (WebSearch)

Search for:
1. `[category] market size [geography] [year]` — find 2–3 industry reports
2. `[category] market CAGR forecast [year range]` — growth rate
3. `[category] [geography] consumer spending [year]` — demand-side validation

**TAM / SAM / SOM Structure:**
```
TAM (Total Addressable Market)
= Total [category] spending in [geography], all tiers
Source: [report name + URL]

SAM (Serviceable Addressable Market)
= TAM × (target tier % + target demographic %)
= [calculation with assumptions stated]

SOM (Serviceable Obtainable Market, Year 3 target)
= SAM × (realistic market share %)
= [calculation with justification]
```

Always state assumptions explicitly. Never present SOM without stating the share % and why it's achievable.

### Step 3 — Competitive Landscape

Identify 6–10 players across the positioning matrix. Use WebSearch to verify:
- Current positioning (premium / mass / niche)
- Price range
- Core customer
- Key differentiator
- Recent moves (funding, launches, expansions)

Map on two axes (choose the most strategically relevant pair):
- Price: low ↔ high
- Style: classic ↔ avant-garde
- OR: local ↔ global, functional ↔ fashion-forward, mass ↔ exclusive

```
Competitive Map:

HIGH PRICE
         [Brand A]          [Brand B]
CLASSIC ─────────────────────────────── AVANT-GARDE
         [Brand C]  [OUR BRAND]
         [Brand D]          [Brand E]
LOW PRICE

White Space: [describe the unclaimed territory and why it's attractive]
```

### Step 4 — Pricing Architecture

Build a price ladder for the category:

```
Tier          Price Range    Brands (examples)    Key Purchase Driver
────────────────────────────────────────────────────────────────────
Entry         $xx–$xx        ...                  Accessibility / trial
Core          $xx–$xx        ...                  Value + style balance
Premium       $xx–$xx        ...                  Quality signal / status
Luxury        $xx+           ...                  Heritage / exclusivity
```

Recommend where the brand should anchor and what psychological mechanism to use (e.g., "good-better-best," decoy pricing, limited edition scarcity).

### Step 5 — White Space & Entry Angle

Identify 2–3 positioning opportunities competitors have left open:
- Customer segments underserved
- Price points with low competition
- Aesthetic territories unclaimed
- Channel / business model gaps

Recommend one primary entry angle with rationale.

## Rules

- **All market figures require a cited source** — no invented numbers.
- State the year of every data point. Fashion market data from 3+ years ago may be materially wrong.
- Asia-Pacific markets often have different dynamics than Western markets. Specify geography.
- Pricing recommendations must account for the brand's actual cost structure (gross margin target). If COGS unknown, state the assumption.
- Output in the user's language (繁中 / EN follow context).
