Išpolirink visą projekto lietuvišką (ir anglišką) tekstą. Tikrina frontend, backend, dashboard, el. pašto šablonus, i18n failus - viską.

## Naudok šias references
Prieš pradėdamas perskaityk:
- `references/lithuanian-web-copy.md`
- `references/lithuanian-patterns.md`
- `references/linkeviciene-editing.md`
- `references/vlkk-skyryba-rules.md`
- `references/english-patterns.md` (angliškam tekstui)

---

## 1 žingsnis - rask VISUS failus

Paleisk skriptą:
```bash
python3 ~/.claude/skills/avoid-ai-writing/scripts/find_all_text_files.py .
```

Jei skriptas neveikia, ieškoti rankinu būdu - VISI šie tipai:

**Frontend / UI:**
- `src/components/**/*.tsx`, `src/app/**/*.tsx`, `src/pages/**/*.tsx`
- `*.jsx`, `*.svelte`, `*.vue`, `*.astro`
- `src/content/**/*.mdx`, `*.md` (ne README)

**Backend / API:**
- `src/app/api/**/*.ts` - API route atsakymai, klaidos
- `src/server/**/*.ts`, `src/lib/**/*.ts`
- `src/actions/**/*.ts` - server actions su toast/error pranešimais
- `src/middleware.ts`

**Dashboard / Admin:**
- `src/app/(admin)/**/*.tsx`, `src/app/dashboard/**/*.tsx`
- `src/app/(dashboard)/**/*.tsx`

**El. paštas:**
- `src/emails/**/*.tsx`, `emails/**/*.tsx`
- `src/templates/**/*.tsx`, `templates/**/*.html`

**i18n / vertimai:**
- `messages/*.json`, `locales/**/*.json`
- `src/i18n/**/*.json`, `public/locales/**/*.json`
- `**/*lt*.json`, `**/*LT*.json`

**Kiti:**
- `src/config/**/*.ts` (navigacijos pavadinimai, meta)
- `src/constants/**/*.ts` (user-facing strings)
- `src/hooks/**/*.ts` (error messages)

**PRALEISK:**
- `node_modules/`, `.next/`, `dist/`, `build/`, `out/`
- `*.test.*`, `*.spec.*`, `*.stories.*`
- `package.json`, `tsconfig.json`, `*.config.*`
- `schema.prisma`, `*types*.ts`, `*generated*`
- `*.lock`, `.env*`

---

## 2 žingsnis - analizuok pagal kategoriją

Kiekvienam failui ištrauk tik user-facing tekstą. Ignoruok:
- Kintamųjų pavadinimus: `className`, `href`, `id`, `key`
- Kodo logiką: `if/else`, `const`, `return`
- Import'us ir export'us
- CSS klases, Tailwind
- API endpoint'ų URL'us: `/api/users`
- Duomenų bazės laukų pavadinimus

**Tikrink pagal 3 lygius:**

### 🔴 Kritinės klaidos (taisyti būtinai)
- Gramatinės klaidos: „Registruojies" → „Registruokitės"
- Klaidinga žodžių forma: „didelis kiekis žmonių" → „daug žmonių"
- Neteisingas brūkšnys: — vietoje - arba –
- Anglų kalkės: „be galvos skausmo", „kita lygmeniu"
- Neteisingas „Jūs/tu" formų maišymas tame pačiame kontekste

### 🟡 AI stilius (labai rekomenduojama taisyti)
- Template antraštės: „Šiuolaikiniame sparčiai besivystančiame..."
- Tušti teiginiai: „aukščiausios kokybės", „inovatyvus", „išsamus sprendimas"
- Pertekliniai žodžiai: „Be to,", „Tuo tarpu", „Iš esmės"
- Daiktavardžių grandinės: „paslaugų teikimo optimizavimo vykdymas"
- Pasyvus balsas kur galima aktyvus
- Trijų būdvardžių sąrašai

### 🔵 Stiliaus gerinimai (pasirenkama)
- Gyvesnės formuluotės iš `lt-writing-quality.md`
- Trumpesnių sakinių pasiūlymai (>25 žodžių)
- Konkretesni veiksmažodžiai vietoje abstrakčių

---

## 3 žingsnis - pateik ataskaitą

Pirmiausia parodyk **suvestinę**:

```
═══════════════════════════════════════
🔍 POLISH-LT ATASKAITA
═══════════════════════════════════════
Nuskanuota failų:  [N]
Rasta problemų:    [M] vietose

🔴 Kritinės klaidos:     [X] (BŪTINA taisyti)
🟡 AI stilius:           [Y] (rekomenduojama)
🔵 Stiliaus gerinimai:   [Z] (pasirenkama)

Paveiktos sritys:
  Frontend:   [N] failų
  Backend:    [N] failų
  Dashboard:  [N] failų
  El. paštas: [N] failų
  i18n:       [N] failų
═══════════════════════════════════════
```

Tada suskirstyk **pagal sritį** ir rodyk kiekvieną failą:

```
━━━ 🖥️  FRONTEND ━━━━━━━━━━━━━━━━━━━━━

📄 src/components/Hero.tsx
┌─────────────────────────────────────
│ 🔴 KRITINĖ KLAIDA
│ DABARTINIS: "Registruojies čia"
│ SIŪLOMAS:   "Registruokitės čia"
│ PRIEŽASTIS: Klaidinga sangrąžinio veiksmažodžio forma
└─────────────────────────────────────
│ 🟡 AI STILIUS
│ DABARTINIS: "Profesionali, greita ir patikima paslauga"
│ SIŪLOMAS:   "Remontuojame per dieną"
│ PRIEŽASTIS: Trijų būdvardžių sąrašas, tušta frazė
└─────────────────────────────────────

━━━ ⚙️  BACKEND / API ━━━━━━━━━━━━━━━━

📄 src/app/api/contact/route.ts
┌─────────────────────────────────────
│ 🔴 KRITINĖ KLAIDA
│ DABARTINIS: "Kažkas nutiko nepavyko išsiųsti"
│ SIŪLOMAS:   "Nepavyko išsiųsti. Bandykite dar kartą."
│ PRIEŽASTIS: Negramatiškas sakinys
└─────────────────────────────────────

━━━ 📊  DASHBOARD ━━━━━━━━━━━━━━━━━━━━

📄 src/app/dashboard/page.tsx
┌─────────────────────────────────────
│ 🔵 STILIAUS GERINIMAS
│ DABARTINIS: "Jūsų užsakymų valdymo sistema"
│ SIŪLOMAS:   "Užsakymai"
│ PRIEŽASTIS: Perteklinė frazė - trumpiau aiškiau
└─────────────────────────────────────

━━━ 📧  EL. PAŠTAS ━━━━━━━━━━━━━━━━━━━

━━━ 🌐  i18n FAILAI ━━━━━━━━━━━━━━━━━
```

---

## 4 žingsnis - patvirtinimas

Po ataskaitos VISADA paklausk:

```
══════════════════════════════════════
Rasta: [X] kritinių + [Y] AI stiliaus + [Z] stilistinių
Tai apima: frontend, backend, dashboard, el. paštą, i18n

Ką taisyti?
  [1] VISKĄ - visas 3 kategorijas visuose failuose
  [2] Tik kritines klaidas (🔴) - [X] pakeitimų
  [3] Kritines + AI stilių (🔴🟡) - [X+Y] pakeitimų
  [4] Failas po failo su patvirtinimu
  [5] Tik ataskaita, nieko nekeisti
  [6] Atšaukti
══════════════════════════════════════
```

Lauk atsako. NETAISYK nieko be patvirtinimo.

---

## 5 žingsnis - taisymas

### Kaip taisyti failus

**JSX/TSX komponentai:**
- Keisk tik tekstą tarp tagų: `<p>tekstas</p>` → `<p>naujas tekstas</p>`
- Keisk string literal'us: `placeholder="Įveskite..."` → `placeholder="Įveskite..."`
- NEKEISK: className, href, onClick, key, id, data-* atributų

**JSON i18n failai:**
- Keisk tik reikšmes, ne raktus: `"title": "senas"` → `"title": "naujas"`
- NEKEISK raktų: `"hero.title"` lieka tas pats

**Backend/API:**
- Keisk tik string'us kurie siunčiami vartotojui: error messages, success messages
- NEKEISK: kintamųjų pavadinimų, SQL, API paths, console.log

**El. pašto šablonai:**
- Keisk tekstą, temą, preview tekstą
- NEKEISK: HTML struktūros, inline stilių

### Po taisymo - ataskaita

```
═══════════════════════════════════════
✅ POLISH-LT BAIGTA
═══════════════════════════════════════
Pataisyta failų:     [N]
Pakeistų vietų:      [M]

Detalės:
  ✅ src/components/Hero.tsx        (3 pakeitimai)
  ✅ src/app/api/contact/route.ts   (1 pakeitimas)
  ✅ messages/lt.json               (8 pakeitimai)
  ...

⚠️  Praleista (dinamiškas tekstas):
  - src/components/Notifications.tsx: {message} props - taisyk rankiniu būdu

🔍 Rekomenduoju patikrinti rankiniu būdu:
  - El. pašto šablonai (jei yra)
  - 404/500 klaidos puslapiai
═══════════════════════════════════════
```

---

## Svarbios taisyklės

1. **NIEKADA** nekeisk kodo logikos - tik teksto turinį
2. **NIEKADA** nekeisk kintamųjų pavadinimų, funkcijų pavadinimų
3. **VISADA** išsaugok JSX struktūrą - keisk tik tekstą viduje
4. Jei tekstas gaunamas iš props (`{title}`, `{children}`) - pažymėk bet NETAISYK
5. Jei i18n failas - taisyk TEN, ne komponentuose kurie naudoja i18n
6. Jei abejoji - rodyti vartotojui sprendimui, ne spėlioti

## Projektas (jei nurodytas):
$ARGUMENTS
