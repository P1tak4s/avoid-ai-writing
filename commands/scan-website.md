Nuskanuok šį projektą lietuviško ir angliško teksto kokybei. Naudok avoid-ai-writing skillio references.

## 1 žingsnis - rask failus

Paleisk skriptą rasti failams su tekstu:

```bash
python3 ~/.claude/skills/avoid-ai-writing/scripts/find_text_files.py .
```

Jei skriptas neveikia arba projektas nenurodytas, ieškoti rankinu būdu: .tsx, .jsx, .mdx, .md failai, ne node_modules, ne .next, ne dist.

## 2 žingsnis - analizuok kiekvieną failą

Kiekvienam failui:
1. Perskaityk failą
2. Ištrauk tik user-facing tekstą (ne kodą, ne kintamųjų pavadinimus, ne import'us)
3. Patikrink pagal avoid-ai-writing skillio taisykles:
   - `references/lithuanian-web-copy.md` - lietuviškam tekstui
   - `references/lithuanian-patterns.md` - lietuviškoms AI klaidoms
   - `references/english-patterns.md` - angliškam tekstui

## 3 žingsnis - pateik pasiūlymus

Sugrupuok visus radimus pagal failą. Kiekvienam failui parodyk:

```
📄 src/components/Hero.tsx
─────────────────────────
DABARTINIS:
  "Šiuolaikiniame sparčiai besivystančiame pasaulyje..."

SIŪLOMAS:
  "Automobilių servisas Vilniuje."

PRIEŽASTIS: Template antraštė, AI stilius

---
DABARTINIS:
  "Registruojies vieną kartą"

SIŪLOMAS:
  "Registruokitės vieną kartą"

PRIEŽASTIS: Gramatinė klaida - liepiamoji nuosaka
```

## 4 žingsnis - patvirtinimas

Po visų pasiūlymų paklausk:

```
Rasta pakeitimų: [N] failuose, [M] teksto vietų.

Ką daryti?
  [1] Taisyti viską automatiškai
  [2] Taisyti failą po failo (kiekvienas su patvirtinimu)
  [3] Rodyti tik sąrašą, netaisyti
  [4] Atšaukti
```

## 5 žingsnis - taisymas

Pagal pasirinkimą:

**Pasirinkimas 1 - taisyti viską:**
- Kiekvienam failui taikyk visus siūlomus pakeitimus
- Pakeisk TIK tekstą, ne kodą, ne struktūrą, ne className
- Po kiekvieno failo: `✅ src/components/Hero.tsx - pataisyta (3 pakeitimai)`
- Pabaigoje: bendra suvestinė

**Pasirinkimas 2 - failas po failo:**
Kiekvienam failui:
```
📄 src/components/Hero.tsx - 3 pakeitimai
Taisyti šį failą? (t/n/peržiūrėti)
```
- `t` → taisyk ir eik prie kito
- `n` → praleisk
- `peržiūrėti` → parodyk pakeitimus dar kartą

**Pasirinkimas 3 - tik sąrašas:**
Eksportuok Markdown lentelę su visais radimais bet nieko nekeisk.

## Svarbios taisyklės taisymui

- Keisk TIK teksto turinį - ne JSX struktūrą, ne props pavadinimus, ne kodo logiką
- Jei tekstas yra i18n faile (en.json, lt.json) - taisyk tik ten, ne komponentuose
- Jei tekstas dinamiškas (props, kintamieji) - pažymėk bet netaisyk
- Išsaugok originalią eilutę numerių struktūrą
- Nerašyk komentarų prie pakeitimų kode

## Projekto kelias (jei nurodytas):
$ARGUMENTS
