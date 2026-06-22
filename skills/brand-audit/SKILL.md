# brand-audit

Diagnose the health of an existing fashion or lifestyle brand. Produces a structured audit scorecard across five dimensions, flags critical inconsistencies, and outputs a prioritized action plan — before any creative overhaul begins.

## When to invoke

Trigger phrases: "品牌健檢" / "brand audit" / "品牌診斷" / "現況評估" / "幫我看看這個品牌" / "brand health" / "品牌一致性" / "這個品牌哪裡有問題" / "before we rebrand" / "rebrand 前先檢查" / "我的品牌怎麼了" / "audit the brand"

Also invoked automatically by `creative-direction` when user asks to "refresh" or "evolve" an existing brand rather than build one from scratch.

## What this skill produces

1. **Brand Health Scorecard** — 5 dimensions × 1–5 star rating + one-line verdict per dimension
2. **Identity Consistency Audit** — visual + verbal system gaps
3. **Digital Presence Audit** — website, social, e-commerce touchpoint review
4. **Trend Alignment Assessment** — does current brand DNA ride or fight current macro trends
5. **Audience Resonance Check** — stated target vs. observable actual audience signals
6. **Priority Action Plan** — top 3 fixes ranked by Impact × Effort, with concrete first step

## How this differs from creative-direction

| `brand-audit` | `creative-direction` |
|---|---|
| Diagnose what exists | Build something new |
| Input: existing brand materials | Input: brand brief / blank slate |
| Output: scored gaps + fix plan | Output: moodboard + design tokens |
| Run BEFORE a rebrand | Run AFTER audit confirms direction |
| Reads brand config if available | Reads brand config if available |

## Process

### Step 0 — Gather Brand Materials

Ask the user to provide (or infer from brand config folder if it exists):

- **Brand name + category** (e.g., "Payshow — talent SaaS platform")
- **Target customer description** (who they say their customer is)
- **Logo / visual identity** — description or file reference
- **Brand color system** — hex codes if known
- **Brand copy / tagline** — homepage headline, social bio
- **Social channels** — URLs or handle names
- **Website URL** (if any)
- **Price positioning** — mass / mid / premium / luxury

If `brand/brand_guidelines.md` exists in the project config folder, read it first and skip re-asking what's already documented.

### Step 1 — Identity Consistency Audit

Evaluate whether the brand's visual + verbal identity is internally coherent.

Check for:

**Visual**
- Color consistency: does the brand use a defined palette across touchpoints, or drift into ad-hoc colors?
- Typography: is there a clear hierarchy (display / body / caption)? Is it used consistently?
- Logo usage: single lockup or multiple variants used carelessly?
- Imagery style: photography / illustration — defined aesthetic or random?

**Verbal**
- Tone of voice: is there a consistent personality (e.g., "confident but approachable" vs. randomly formal/casual)?
- Tagline clarity: does the tagline communicate what the brand does and for whom in <7 words?
- Name pronunciation / spelling: any confusion risk?

Output format:

```
Identity Consistency Score: ★★★☆☆

Visual Gaps:
- [gap 1]
- [gap 2]

Verbal Gaps:
- [gap 1]
- [gap 2]

Verdict: [one sentence — the root cause of inconsistency]
```

### Step 2 — Digital Presence Audit

If a website URL or social handles are provided, use WebSearch or WebFetch to review:

**Website** (if URL provided)
- Above-the-fold clarity: does the first screen communicate who this is for and what they do?
- CTA presence: is there a clear primary action (buy / book / sign up)?
- Mobile usability: does the site mention responsiveness or is there evidence of mobile issues?
- Loading / performance signals: any obvious heavy assets?

**Social Media**
- Bio completeness: name + what you do + link?
- Posting frequency: active (≥2×/week), occasional (≥2×/month), dormant?
- Content mix: product / lifestyle / UGC / pure promotional — balanced?
- Visual consistency with brand identity?

**E-commerce (if applicable)**
- Product photography consistency
- Price anchoring — is the tier signaled visually?

Output format:

```
Digital Presence Score: ★★★★☆

Website:
- [finding]
- [finding]

Social:
- [finding]

E-commerce:
- [finding or N/A]

Verdict: [one sentence — biggest digital gap]
```

### Step 3 — Trend Alignment Assessment

Cross-reference the brand's current visual DNA against current and upcoming macro fashion trends.

Use WebSearch: `[brand category] macro trends [current year]` to ground the assessment.

For each of the 3 most relevant macro trends currently active:

```
Trend: [name]
Brand's Current Alignment:
  ✅ Already riding — [how]
  ⚠️ Partially — [what's missing]
  ❌ Misaligned — [risk: brand feels dated or off-trend]
Risk Level: Low / Medium / High
```

Overall trend alignment score + key risk sentence.

```
Trend Alignment Score: ★★★☆☆
Biggest Risk: [one sentence — e.g., "Brand's core color palette is 3 seasons behind current earth-tone cycle"]
```

### Step 4 — Audience Resonance Check

Compare the stated target customer against observable signals of who the brand is actually attracting.

Ask or infer:
- Who does the brand say it's for? (from brief / brand_guidelines)
- Who does the brand's social content, copy, and pricing actually attract?
- Is there a gap?

Common gap patterns:
- **Aspirational Overshoot**: brand positions premium but product quality / UX signals mid-tier → erodes trust
- **Age Drift**: brand targets Gen Z but aesthetic reads Millennial (or vice versa)
- **Gender Ambiguity**: brand says "unisex" but all imagery skews one direction
- **Occasion Mismatch**: brand says "everyday" but product range / styling reads occasion-wear

```
Audience Resonance Score: ★★★★☆

Stated Target: [who they say]
Apparent Actual: [who the signals suggest]
Gap Type: [gap pattern name or "No significant gap"]
Risk: [one sentence]
```

### Step 5 — Commercial Clarity Check

Does the brand's communication drive a clear, believable commercial action?

Evaluate:
- **Value proposition legibility**: can a first-time visitor explain what the brand sells and why it's worth paying for?
- **Price-quality signal alignment**: does the brand's aesthetic warrant the price point?
- **Purchase trigger clarity**: is there urgency / scarcity / social proof present?
- **Trust signals**: reviews, press mentions, certifications, notable clients?

```
Commercial Clarity Score: ★★☆☆☆

Value Prop: [clear / unclear / muddled]
Price Signal: [aligned / over-priced signal / under-priced signal]
Trust Signals Present: [yes — list / no / partial]
Verdict: [one sentence]
```

### Step 6 — Brand Health Scorecard + Priority Action Plan

Compile all 5 scores into a single summary:

```
╔════════════════════════════════════════════════════╗
║         BRAND HEALTH SCORECARD                     ║
╠════════════════════════════╦═══════════════════════╣
║ Identity Consistency       ║ ★★★☆☆  [verdict]    ║
║ Digital Presence           ║ ★★★★☆  [verdict]    ║
║ Trend Alignment            ║ ★★★☆☆  [verdict]    ║
║ Audience Resonance         ║ ★★★★☆  [verdict]    ║
║ Commercial Clarity         ║ ★★☆☆☆  [verdict]    ║
╠════════════════════════════╩═══════════════════════╣
║ OVERALL                    ║ ★★★☆☆  (3.0 / 5.0)  ║
╚════════════════════════════════════════════════════╝
```

Then the Priority Action Plan — rank by **Impact × Effort** (High Impact + Low Effort first):

```
PRIORITY ACTION PLAN

#1 [Fix name] — Impact: HIGH / Effort: LOW
   Problem: [one sentence]
   First Step: [concrete, actionable — deliverable or decision]
   Skill to use: [creative-direction / output-generator / seasonal-curation]

#2 [Fix name] — Impact: HIGH / Effort: MEDIUM
   Problem: [one sentence]
   First Step: [concrete, actionable]
   Skill to use: [...]

#3 [Fix name] — Impact: MEDIUM / Effort: LOW
   Problem: [one sentence]
   First Step: [concrete, actionable]
   Skill to use: [...]
```

Offer to immediately kick off action #1 using the appropriate skill.

## Rules

- **Audit before creating.** Never use this skill to invent new brand direction — it's diagnostic only. Hand off to `creative-direction` for generative work.
- **Ground trend claims in WebSearch.** Never assert a brand is "on-trend" or "dated" from training data alone.
- **Score honestly.** A 5-star score on any dimension should be rare. If everything is 4–5 stars, the audit is not adding value.
- **One fix at a time.** The action plan caps at 3 priorities. More than 3 overwhelms clients and dilutes focus.
- **Config-first.** If a brand config folder exists (e.g., `payshow-config/brand/`), read it before asking any questions — the config is the source of truth for brand intent.
- Output in the user's language (繁中 / EN follow context).
