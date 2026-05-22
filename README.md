# avoid-ai-writing

A [Claude Code](https://claude.ai/code) skill that audits and rewrites prose in **English and Lithuanian** to remove AI writing patterns ("AI-isms").

## What it does

- Detects 21 pattern categories that make text sound machine-generated
- Applies a 43-entry word/phrase replacement table (e.g. *leverage → use*, *robust → reliable*)
- Fixes Lithuanian-specific issues: English calques, noun string compounds, passive overuse, loan words
- Returns: issues found → rewritten text → what changed → second-pass audit

## Core principle

> Human writing is **simple, short, and specific**. AI writing is vague, inflated, and formulaic.

## Install

Download `avoid-ai-writing.zip` from [Releases](../../releases) and install it in Claude Code, or clone this repo and point Claude Code at the folder.

After installing the skill, copy the commands to your Claude Code commands folder:

```bash
cp avoid-ai-writing/commands/* ~/.claude/commands/
```

## Commands

| Command | What it does |
|---|---|
| `/fix-ai-slop` | Audits and rewrites any text (LT or EN) |
| `/rašyk-lt` | Writes Lithuanian copy from scratch - polite, no AI patterns |
| `/rašyk-en` | Writes English copy from scratch - no AI patterns |
| `/scan-website` | Scans entire project, shows all AI text issues, fixes with approval |

## Usage

Trigger phrases (English or Lithuanian):
- "remove AI-isms from this"
- "make this sound less like AI"
- "clean up AI writing"
- "nerašyti kaip AI"
- "pašalinti AI stilių"

## Files

```
avoid-ai-writing/
├── SKILL.md                          # Skill definition + 6-step process
└── references/
    ├── english-patterns.md           # 43-entry table + 15 structural categories
    └── lithuanian-patterns.md        # Lithuanian word replacements + grammar fixes
```

## English patterns covered

Word replacements, template openings, hollow intensifiers, hedging chains, rule of three, negative parallelism, copula avoidance, significance inflation, superficial -ing endings, vague attributions, formulaic challenges sections, generic conclusions, chatbot artifacts, em dash overuse, mechanical bold/bullets.

## Lithuanian patterns covered

Word replacements, English calques (*naviguojame per* etc.), noun string compounds, over-nominalization, passive voice overuse, loan word inflation (*kontentas → turinys*, *implementuoti → įgyvendinti*), AI transition words (*Be to, Tuo tarpu, Apibendrinant*).

## License

MIT
