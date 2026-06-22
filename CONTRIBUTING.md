# Contributing to fashion-director

Thanks for your interest in contributing. This plugin is an open methodology layer — contributions that improve *how* fashion and brand work is structured are welcome. Contributions that embed client-specific brand DNA should go into a private config folder instead.

---

## What belongs here (free tier)

- New skills that add methodology — e.g., a `campaign-planning` skill, a `sustainability-audit` skill
- New style agents for underrepresented categories (e.g., `kidswear`, `accessories`, `fragrance`)
- Improvements to existing skill processes, prompt structures, or output templates
- Asia-Pacific market calibration — defaults and examples should work well for TW / KR / JP, not just US / EU
- Bug fixes, typos, broken references

## What does NOT belong here

- Brand config files (`*-config/` folders) — keep these private, in your own repo
- Client deliverables, lookbooks, or curated content for specific brands
- Anything that would compromise a client's proprietary brand DNA

---

## How to add a new skill

1. Create `skills/{skill-name}/SKILL.md`
2. Register it in `plugin.json` under `"skills"`
3. Add a row to the Skills table in `README.md`
4. Add an invoke example to the Examples section
5. Bump the minor version in `plugin.json` (e.g., 0.4.0 → 0.5.0)

### Skill file structure

```markdown
# skill-name

One-sentence description of what this skill does.

## When to invoke

Trigger phrases: "phrase A" / "phrase B" / "English phrase"

## What this skill produces

Numbered list of deliverables.

## Process

### Step 1 — [Name]
...

## Rules

- Rule 1
- Rule 2
- Output in the user's language (繁中 / EN follow context).
```

**Rules for every skill:**
- Trigger phrases must include both Chinese and English variants
- Every skill must produce at least one concrete deliverable
- Claims requiring external data (market size, trend names) must call WebSearch — not training data
- If a brand config folder exists, read it before generating — never re-ask what's already documented
- End with "Output in the user's language (繁中 / EN follow context)"

---

## How to add a new style agent

1. Create `agents/{category}.md`
2. Register it in `plugin.json` under `"agents"`
3. Update README agents table

### Agent file structure

```markdown
# {category} Style Agent

[2–3 sentence positioning. What does this agent know that others don't?]

## Domain expertise

[3–5 bullet points of specialized knowledge]

## Vocabulary

Key terms this agent uses precisely: [term list]

## How this agent differs from general creative-direction

[1 paragraph]

## Default invocation

When activated via `style-specialist`, this agent:
1. [step 1]
2. [step 2]
3. [step 3]
```

---

## Versioning

This plugin follows **semver-lite**:

| Change | Version bump |
|---|---|
| New skill or agent | Minor (0.x.0) |
| Bug fix / copy improvement | Patch (0.0.x) |
| Breaking change to config schema | Major (x.0.0) |

---

## Client config folder convention

If you're building a private config layer for a client, follow this structure:

```
{client}-fashion-config/
  CLAUDE.md               ← overrides plugin rules for this client
  brand/
    brand_guidelines.md   ← brand DNA, tone, colors, what to avoid
    target_audience.md    ← 2–4 personas with jobs-to-be-done
    color_system.md       ← hex codes + usage rationale (optional)
  config/
    output_preferences.md ← Canva kit ID, Notion DB, Gamma theme
  seasonal/
    {Season}{Year}_curated.md   ← curated trend drop for this brand
```

The `{client}-fashion-config/` folder **should not be committed to this repo**. The root `.gitignore` blocks all `*-config/` patterns.

---

## Questions

Open an issue. PRs without a linked issue for new skills will be reviewed but may take longer.
