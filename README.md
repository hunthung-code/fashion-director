# fashion-director

> AI Fashion Director for Claude Code — creative direction, trend intelligence, style specialization, market strategy, and client deliverable generation.

**Free methodology layer. Bolt on a brand config folder for client-specific intelligence.**

---

## Install

```bash
npx skills add hunthung-code/fashion-director
```

Or add to your `.claude/settings.json`:
```json
{
  "plugins": ["hunthung-code/fashion-director"]
}
```

---

## What's included

### 8 Skills

| Skill | Invoke phrase | What it does |
|---|---|---|
| `creative-direction` | "做 moodboard" / "視覺方向" / "design direction" | Moodboard brief, color story, design tokens, visual direction doc |
| `trend-intelligence` | "趨勢掃描" / "最新風向" / "trend report" | WebSearch-powered seasonal trend brief, micro-trend radar, runway analysis |
| `style-specialist` | "男裝方向" / "奢侈品策略" / "style brief" | Routes to appropriate style agent, category context, style brief |
| `market-strategy` | "市場規模" / "競品分析" / "market sizing" | TAM/SAM/SOM, competitive landscape map, pricing architecture |
| `output-generator` | "整理成簡報" / "輸出 PDF" / "client deck" | Assembles Gamma decks, PDFs, Canva exports, Notion pages |
| `seasonal-curation` | "季度趨勢包" / "SS2026 趨勢" / "trend curation" | Brand-filtered seasonal brief, color strategy, styling direction, client-ready deck |
| `brand-audit` | "品牌健檢" / "brand audit" / "品牌診斷" | 5-dimension health scorecard + priority action plan before a rebrand |
| `lookbook-generator` | "做 lookbook" / "時尚 editorial" / "lookbook PDF" | Self-contained HTML → A4 PDF editorial lookbook, print-quality |

### 6 Style Agents

| Agent | Specialization |
|---|---|
| `tech-wear` | Smart materials, wearables, functional fashion aesthetics |
| `menswear` | Tailoring, contemporary, streetwear influence, Asian market |
| `womenswear` | Silhouette forecasting, color story, fabric direction |
| `luxury` | Heritage storytelling, HNW psychology, scarcity mechanics |
| `sportswear` | Performance tech, athleisure, collaboration strategy |
| `street-hype` | Drop mechanics, KOL dynamics, hype culture, resale market |

---

## Example usage

```
/creative-direction 幫我做一個針對台灣 25-35 歲職業女性的春夏色彩系統

/trend-intelligence 掃描 2026 SS 亞太女裝主要趨勢

/style-specialist 我的客戶做奢侈品男裝，進入台灣市場，給我定位建議

/market-strategy 台灣 athleisure 市場有多大？主要玩家是誰？

/seasonal-curation 幫我做 FW2026 趨勢包，品牌是 Payshow

/brand-audit 幫我診斷這個品牌哪裡有問題，rebrand 前先做健檢

/lookbook-generator 把這季 4 個造型整理成可以給客戶的 lookbook PDF

/output-generator 把今天的 creative direction 和 trend report 打包成 Gamma deck
```

---

## Project-Specific Intelligence Layer (paid / private)

The free plugin provides **methodology** — how to think, research, and output.

For client work, create a private `{client}-fashion-config/` folder alongside your project:

```
your-project/
  .claude/
    CLAUDE.md          ← references the config below
  client-fashion-config/
    CLAUDE.md          ← overrides free plugin with brand-specific rules
    brand/
      brand_guidelines.md
      color_system.md
      target_audience.md
    agents/
      {client}-director.md   ← custom agent for this client
    config/
      output_preferences.md  ← Canva kit ID, Notion DB, Gamma theme
    seasonal/
      SS2026_curated.md      ← hand-curated trend drops per season
```

The config layer **does not fork this plugin** — it stacks on top. When this plugin updates, your client configs automatically benefit.

See `payshow-config/` in this repo for a real-world example (Payshow, a Taiwanese showgirl/event staffing SaaS).

---

## Design principles

1. **Methods over content** — the free tier teaches *how* to direct; the paid tier provides the *brand DNA* to direct toward
2. **WebSearch-anchored** — no trend claims from training data alone; everything is verified at invocation time
3. **Deliverable-first** — every skill produces a usable output, not just an analysis
4. **Asia-Pacific aware** — defaults and examples are calibrated for Taiwan/Korea/Japan markets, not just Western fashion capitals

---

## Roadmap

- [x] `v0.2` — `seasonal-curation` skill (brand-filtered seasonal trend drop)
- [x] `v0.3` — `brand-audit` skill (5-dimension health scorecard + action plan)
- [x] `v0.4` — `lookbook-generator` skill (HTML → A4 PDF fashion editorial)
- [ ] `v0.5` — Integrate image generation pipeline (banana2 / DALL-E placeholders → real images)
- [ ] `v1.0` — Full config schema + validation for client config folders

PRs welcome. See [CONTRIBUTING.md](CONTRIBUTING.md).

---

## License

MIT © 2026 hunthung-code
