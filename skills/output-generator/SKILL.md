# output-generator

Assembles fashion director deliverables into client-ready formats: trend report decks, brand visual spec PDFs, moodboard documents, and strategy presentations.

## When to invoke

Trigger phrases: "整理成簡報" / "做成 deck" / "輸出 PDF" / "客戶版本" / "打包交付" / "做成投影片" / "output" / "deliverable" / "export" / "client deck" / "generate report"

Also invoked as the final step after `creative-direction` or `market-strategy` to package findings.

## What this skill produces

| Format | Tool | Best for |
|---|---|---|
| Gamma deck (22-slide narrative) | Gamma MCP | Investor / client pitch, trend presentation |
| PDF (print-quality) | playwright-pdf skill | Brand spec doc, one-pager, formal report |
| Canva export | Canva MCP | Marketing materials, social assets, lookbook |
| Notion page | Notion MCP | Internal archive, ongoing client collaboration |
| Markdown doc | Write tool | Quick share, further editing |

## Process

### Step 1 — Content Inventory
Collect all generated content from this session:
- Moodboard / creative direction findings
- Trend report content
- Market strategy data
- Style brief

If pieces are missing, generate them first using the appropriate skill before packaging.

### Step 2 — Format Selection

Ask or infer from context:

| Context signal | Recommended format |
|---|---|
| "投資人看" / "pitch" | Gamma deck |
| "列印" / "正式文件" | PDF via playwright-pdf |
| "IG / 社群" / "設計師用" | Canva |
| "存起來" / "給團隊" | Notion |
| "快速給對方" | Markdown doc |

### Step 3 — Document Assembly

**For Gamma deck** (22-slide structure):
```
Slide 1: Cover — Brand name + season + high-concept tagline
Slide 2: Executive Summary — 3 bullets
Slides 3–5: Macro Trend Context (1 pillar per slide)
Slides 6–8: Style Direction (concept name + visual language + color story)
Slides 9–10: Target Customer (who, where, what occasion)
Slides 11–12: Competitive Landscape + White Space
Slides 13–15: Design Token System (color / type / motion)
Slides 16–17: Moodboard Description + Reference Universe
Slide 18: Pricing Architecture
Slides 19–20: Go-to-Market Entry Angle
Slide 21: Next Steps / Open Questions
Slide 22: Appendix / Sources
```

**For PDF brand spec**:
```
§1 Brand Overview (1 page)
§2 Visual Identity — color + type + token system (2 pages)
§3 Moodboard Direction (1 page)
§4 Trend Context (1 page)
§5 Market Position (1 page)
§6 Do's and Don'ts (1 page)
```

### Step 4 — Generation

**Gamma**: Use `mcp__e3d8567b-1b93-431a-b611-99742476e72a__generate` with `language: zh-TW` or `en`, `textOptions.baseFontSize: lg`, `theme: pearl` (white) or `theme: slate` (dark).

**PDF**: Invoke `playwright-pdf` skill with assembled HTML content.

**Canva**: Use `mcp__c4699412__generate-design` with appropriate design_type.

**Notion**: Use `notion-create-pages` with structured markdown content.

### Step 5 — Quality Check
Before delivering, verify:
- [ ] All cited data has sources
- [ ] No placeholder text remaining
- [ ] Brand name spelled consistently throughout
- [ ] Output format matches client's stated preference
- [ ] File named with convention: `[BrandName]_[DocType]_v[version]_[YYYYMMDD]`

## Rules

- Never generate a client deliverable with unverified market figures — go back to `market-strategy` to verify first.
- Gamma is preferred for pitch contexts (richer visual). PDF for formal / archival. Canva for repeatable marketing assets.
- If brand config folder exists, apply the brand's Canva kit ID and Notion DB for auto-filing.
- Output in the user's language (繁中 / EN follow context).
