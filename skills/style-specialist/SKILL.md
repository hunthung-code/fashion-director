# style-specialist

Routes to the appropriate style agent based on detected category, then produces a style-specific creative brief. Handles multi-category briefs by combining perspectives.

## When to invoke

Trigger phrases: "男裝方向" / "女裝建議" / "奢侈品策略" / "科技穿搭" / "運動風格" / "街頭潮流" / "這個品牌的風格定位" / "style brief" / "我的客戶做 [category]" / "menswear" / "womenswear" / "luxury" / "sportswear" / "streetwear" / "tech fashion"

## Detection Logic

Read user message and context for style category signals:

| Signal in message | Route to agent |
|---|---|
| tech / wearable / functional / 科技感 / 戶外機能 | `tech-wear` |
| 男裝 / menswear / 西裝 / 男士 / tailoring | `menswear` |
| 女裝 / womenswear / 女士 / feminine / 輪廓 | `womenswear` |
| 奢侈品 / luxury / 精品 / heritage / 高端 / prestige | `luxury` |
| 運動 / sport / athletic / athleisure / performance | `sportswear` |
| 街頭 / street / hype / 潮牌 / drop / limited / collab | `street-hype` |

**Multi-category**: If 2+ categories are present (e.g., "luxury sportswear" or "tech + street"), activate both agents and synthesize their inputs. Flag the tension points explicitly.

**Unknown category**: Default to asking one clarifying question: "這個品牌最主要的客群是誰？他們穿這個去哪裡？" — the answer usually reveals the category.

## What this skill produces

1. **Style Routing Notice** — which agent(s) were activated and why
2. **Category Context Sheet** — market overview, key players, aesthetic territory for this category
3. **Style Brief** — from the activated agent's perspective, tailored to the specific brand/project
4. **Category Pitfalls** — common mistakes brands make in this space

## Process

### Step 1 — Category Detection
Parse user input. If ambiguous, ask the one clarifying question above.

### Step 2 — Agent Activation
Hand off to the appropriate agent(s) with full context. The agent returns its perspective.

### Step 3 — Synthesis
If single category: output the agent's style brief directly.
If multi-category: synthesize into a hybrid brief, clearly marking which elements come from which tradition.

### Step 4 — Pitfall Check
Add a brief "Category Pitfalls" section — the 2–3 most common mistakes brands make in this space.

## Output Format

```
## Style Brief: [Brand/Project Name]
**Category**: [detected category / hybrid]
**Activated Agent(s)**: [agent names]

### Category Context
[2–3 sentences on the current state of this market]

### Style Direction
[Agent-specific brief: aesthetic pillars, reference universe, what to own]

### Category Pitfalls
- [Pitfall 1]: [why it kills brands in this space]
- [Pitfall 2]: ...
- [Pitfall 3]: ...
```

## Rules

- Never assume category from brand name alone. "Nike" could be sportswear OR street-hype depending on the campaign.
- Multi-category briefs must name the tension: "luxury × streetwear creates a contradiction around exclusivity — here is how to resolve it."
- Output in the user's language (繁中 / EN follow context).
