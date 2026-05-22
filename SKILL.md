---
name: avoid-ai-writing
description: "Audit and rewrite prose in English or Lithuanian to remove AI writing patterns: 43-entry word replacement table, 21 structural pattern categories, and Lithuanian-specific calque/grammar fixes."
risk: none
date_updated: "2026-05-21"
---

# Avoid AI Writing — Audit & Rewrite

Detects and fixes AI writing patterns ("AI-isms") that make text sound machine-generated. Works in **English and Lithuanian**. Covers 21 pattern categories with a 43-entry word/phrase replacement table and a separate set of Lithuanian-specific grammar and calque issues.

The core principle: human writing is **simple, short, and specific**. AI writing is vague, inflated, and formulaic.

## When to Use

- When asked to "remove AI-isms", "make this sound less like AI", "clean up AI writing", "nerašyti kaip AI", "pašalinti AI stilių"
- After drafting any content before publishing
- When auditing documentation, blog posts, emails, marketing copy, or internal communications

## Reference Files

Load these into context as needed:

- `references/english-patterns.md` — 43-entry word replacement table, structural patterns, formatting rules, second-pass checklist (English)
- `references/lithuanian-patterns.md` — Lithuanian word replacements, grammar fixes, calque patterns, loan-word table, second-pass checklist (Lithuanian)
- `references/lithuanian-web-copy.md` — Lithuanian website tone guide, grammar mistakes Claude makes, natural phrases, before/after examples
- `references/vlkk-grammar-rules.md` — Official VLKK 2022 spelling rules: brūkšnelis vs brūkšnys, kabutės, skaičiai, sutrumpinimai
- `references/vlkk-skyryba-rules.md` — Official VLKK 2020 punctuation rules: kableliai, brūkšniai, dvitaškiai, bullet sąrašai, kabutės

## Process

### Step 1: Detect language

Determine if the text is English, Lithuanian, or mixed. For mixed text, apply both pattern sets.

### Step 2: Load the right reference file

- English text → load `references/english-patterns.md`
- Lithuanian text → load `references/lithuanian-patterns.md`
- Mixed → load both

### Step 3: Audit — find every AI-ism

Read the text and list every instance of:

1. **Words on the replacement table** — flag each one with the suggested replacement
2. **Template openings** — "In today's rapidly evolving...", "Šiuolaikiniame sparčiai besivystančiame..."
3. **Overused transitions** — Moreover, Furthermore, Additionally / Be to, Tuo tarpu, Apibendrinant
4. **Hollow intensifiers** — truly, really, absolutely / iš esmės, apskritai (as fillers)
5. **Hedging chains** — "it could be argued", "one might say"
6. **Rule of three** — three-adjective lists padding thin claims
7. **Negative parallelism** — "Not only X but also Y" / "Ne tik X, bet ir Y"
8. **Copula avoidance** — "serves as", "stands as" instead of "is" / "veikia kaip" instead of "yra"
9. **Significance inflation** — "pivotal role", "testament to", "vaidina svarbų vaidmenį"
10. **Superficial -ing endings** — "highlighting the importance", "underscoring the significance"
11. **Vague attributions** — "experts say", "researchers argue" / "ekspertai teigia"
12. **Formulaic challenges section** — "Despite these achievements, X faces challenges..."
13. **Generic conclusions** — "The future remains bright", "Ateitis atrodo perspektyvi"
14. **Formatting tells** — em dash overuse, mechanical bold, bullet-heavy sections, emoji headers
15. **Lithuanian-specific** (if applicable): noun string calques, over-nominalization, passive overuse, English loan words where native words exist

### Step 4: Rewrite

Apply the fixes. Rules:

- **Cut or replace every flagged word/phrase** using the replacement table
- **Prefer active voice** over passive
- **Use short sentences** — if a sentence runs past 25 words, split it
- **Cut filler transitions** — if a sentence starts with Moreover/Furthermore/Be to, either delete the word or merge the sentence with the previous one
- **No three-adjective lists** — state the one most accurate adjective
- **No generic openings or conclusions** — start in the middle of the idea; end when the information ends
- **For Lithuanian**: prefer native Lithuanian words over English loan words; fix noun string calques; use active verbs instead of nominalized phrases

### Step 5: Second-pass audit

Re-read the rewritten text. Check:

- Any replacement-table word surviving
- Sentences starting with AI transition words
- "It's worth noting" / "verta paminėti" still present
- Sentences ending in "...highlighting/underscoring X importance" or Lithuanian equivalents
- Generic conclusion sentences

### Step 6: Report output

Return four sections:

1. **Issues found** — every AI-ism quoted from the original with category label
2. **Rewritten version** — the clean text
3. **What changed** — brief list of edits made
4. **Second-pass result** — confirm the rewrite is clean or flag any remaining issues

## Example (English)

**Input:**
> "In today's rapidly evolving AI landscape, developers are embarking on a pivotal journey to leverage cutting-edge tools that streamline their workflows. Moreover, these robust solutions serve as a testament to the industry's commitment to fostering seamless experiences."

**Output:**

*Issues found:* "In today's rapidly evolving AI landscape" (template opening), "embarking on" (AI verb), "pivotal journey" (significance inflation), "leverage" (table: use), "cutting-edge" (table: new/latest), "streamline" (table: simplify), "Moreover" (AI transition), "robust" (table: reliable), "serve as a testament to" (copula avoidance + significance inflation), "fostering" (table: building), "seamless" (table: smooth/easy)

*Rewritten:* "Developers are starting to use newer AI tools to simplify their work. These tools are reliable, and they're making development less painful."

*What changed:* Removed template opening, replaced 7 table words, cut "Moreover", replaced "serve as a testament to" with "are", cut "seamless experiences"

*Second-pass:* Clean.

## Example (Lithuanian)

**Input:**
> "Šiuolaikiniame sparčiai besivystančiame skaitmeninių technologijų pasaulyje įmonės vaidina svarbų vaidmenį skatinant inovatyvius sprendimus. Be to, šių procesų optimizavimo vykdymas yra esminis sėkmingo augimo veiksnys."

**Output:**

*Issues found:* "Šiuolaikiniame sparčiai besivystančiame...pasaulyje" (template opening), "vaidina svarbų vaidmenį" (significance inflation), "skatinant inovatyvius sprendimus" (superficial -ing equivalent + "inovatyvius" table word), "Be to," (AI transition), "šių procesų optimizavimo vykdymas" (noun string calque + over-nominalization), "esminis" (table: svarbus/pagrindinis)

*Rewritten:* "Įmonės kuria naujus sprendimus. Šiuos procesus optimizuoti — svarbu, kad verslas augtų."

*What changed:* Removed template opening, replaced significance inflation phrase, cut "Be to,", replaced noun string with active verb construction, replaced "esminis" with "svarbu"

*Second-pass:* Clean.

## Limitations

- Does not detect AI-generated code, only prose
- Pattern matching is guideline-based — some flagged words are fine in specific contexts; use judgment
- The replacement table suggests alternatives; pick the one that fits the sentence
- Cannot verify factual claims or find real citations to replace vague attributions
- Lithuanian loan-word fixes assume the text is aimed at a native Lithuanian audience; adjust for technical audiences where loan words are standard
