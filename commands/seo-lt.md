SEO auditas lietuviškoms svetainėms. Sujungia techninius SEO patikrinimus su lietuviškos copy kokybės analize.

## Naudok šiuos skillius kartu
- `seo-audit` - techninis + on-page SEO
- `seo-technical` - robots.txt, sitemap, canonicals, Core Web Vitals
- `seo-local` - jei vietinis verslas (GBP, NAP, vietiniai raktažodžiai)
- `seo-content-auditor` - turinio kokybė ir E-E-A-T
- `avoid-ai-writing` → `references/seo-copy.md` - lietuviškos copy taisyklės

---

## Argumentai

```
/seo-lt https://revmotors.lt          → tikrina live svetainę
/seo-lt https://revmotors.lt/paslauga → tikrina konkretų puslapį
/seo-lt                               → tikrina projektą iš failų
```

---

## 1 žingsnis - nustatyk kontekstą

Iš URL arba projekto failų išsiaiškink:
- **Verslo tipas** - vietinis verslas / e-commerce / SaaS / portfolio?
- **Miestas / regionas** - Vilnius, Kaunas, Klaipėda, visa Lietuva?
- **Pagrindinė paslauga / produktas** - kas parduodama?
- **Kalba** - lietuvių / anglų / mišri?

Jei vietinis verslas (servisas, kirpykla, advokatai, t.t.) → taip pat taikyk `seo-local` skillio taisykles.

---

## 2 žingsnis - techninis SEO

Naudok `seo-technical` skillio metodologiją. Tikrink:

### Indeksacija ir crawl
- [ ] robots.txt egzistuoja ir neblokuoja svarbių puslapių
- [ ] sitemap.xml egzistuoja, pateiktas Google Search Console
- [ ] Noindex tagų nėra ten, kur neturėtų būti
- [ ] Canonical tagai teisingi (ne duplicate content)
- [ ] HTTPS visur, ne HTTP

### Techniniai klausimai
- [ ] 404 puslapiai turi tinkamą pranešimą lietuviškai
- [ ] Redirect grandinės (<2 redirect'ai)
- [ ] Mobile-friendly
- [ ] Core Web Vitals (jei galima patikrinti)

### Struktūriniai duomenys (Schema)
- [ ] LocalBusiness schema (jei vietinis verslas)
- [ ] Organization schema
- [ ] BreadcrumbList navigacijoje
- [ ] Product/Service schema (jei paslauga)
- [ ] FAQPage schema (jei yra DUK)

**Pastaba:** `WebFetch` nemato JS-injected schema. Jei reikia tikslaus patikrinimo - naudok Google Rich Results Test: https://search.google.com/test/rich-results

---

## 3 žingsnis - on-page SEO (kiekvienas puslapis)

### Title tag - LIETUVIŠKA KOPIJA
Tikrink pagal `references/seo-copy.md` + šias taisykles:

| Kriterijus | Reikalavimas |
|---|---|
| Ilgis | 30-60 simbolių |
| Rakažodis | Pirmame žodyje arba frazėje |
| Struktūra | `[Paslauga] [Mieste] \| [Įmonė]` |
| Kalba | Lietuvių (ne angliška) |
| Tonas | Konkretus, ne AI šablonas |
| Unikalumas | Kiekvienas puslapis - skirtingas |

❌ Klaidos title tag'uose:
- AI šablonas: "Profesionalios ir kokybiškos paslaugos Jūsų komfortui"
- Per ilgas: >60 simbolių
- Be rakažodžio: "Pagrindinis puslapis | Įmonė"
- Angliška kalba lietuviškame puslapyje
- Ilgi brūkšniai (---) vietoje (-) arba (|)

### Meta description - LIETUVIŠKA KOPIJA
| Kriterijus | Reikalavimas |
|---|---|
| Ilgis | 120-160 simbolių |
| CTA | Turi būti: Skambinkite, Registruokitės, Sužinokite daugiau |
| Konkreti nauda | Kaina, laikas, faktas - ne tušti žodžiai |
| Rakažodis | Natūraliai įtrauktas |
| Tonas | Aktyvus, ne pasyvus |

❌ Klaidos meta description:
- "Mūsų įmonė teikia profesionalias paslaugas aukščiausios kokybės standartais" (AI, tušta)
- Be CTA
- Per trumpas (<80 simbolių) arba per ilgas (>165)
- Pasyvus balsas: "paslaugos yra teikiamos"

### H1 - PAGRINDINIS ANTRAŠTĖ
- Tik VIENAS H1 puslapyje
- Turi turėti pagrindinį rakažodį
- Žmogiškas, ne robotiškas
- Gali sutapti su title tag arba būti šiek tiek platesnis

### H2 / H3 - SKYRIAI
- H2 = skyrių pavadinimai su antriniais rakažodžiais
- Venk "Apie mus", "Mūsų paslaugos" - per bendri
- Geriau: "10 metų automobilių remonto patirtis Vilniuje"

### Nuotraukų alt tekstai
- Ne tušti, ne "image001.jpg"
- Aprašo kas pavaizduota + kontekstas
- Lietuvių kalba
- Pvz: `automobilių servisas vilniuje variklio remontas`

---

## 4 žingsnis - vietinis SEO (jei vietinis verslas)

Naudok `seo-local` skillio metodologiją. Tikrink:

### Vietiniai raktažodžiai puslapyje
- [ ] Miestas/regionas H1 arba pirmame paragrafe
- [ ] Adresas footer'yje (schema + plain text)
- [ ] Darbo valandos puslapyje
- [ ] Telefonas (click-to-call mobile)

### NAP nuoseklumas (Name, Address, Phone)
- Tiksliai tas pats adresas, pavadinimas, telefonas:
  - Svetainėje
  - Google Business Profile
  - Facebook
  - Direktoriuose (Aruodas.lt, 118.lt, Verslo žinios)

### Google Business Profile signalai
- [ ] Ar GBP profilis yra ir verifikuotas?
- [ ] Ar kategorija teisinga?
- [ ] Ar atsiliepimai yra ir atsakoma į juos?

### Vietinė schema - LocalBusiness
```json
{
  "@type": "LocalBusiness",
  "name": "...",
  "address": {
    "@type": "PostalAddress",
    "streetAddress": "...",
    "addressLocality": "Vilnius",
    "addressCountry": "LT"
  },
  "telephone": "+370...",
  "openingHours": "Mo-Fr 08:00-18:00"
}
```

---

## 5 žingsnis - turinio kokybė (E-E-A-T)

Naudok `seo-content-auditor` skillio metodologiją. Tikrink:

### Patirtis ir autoritetas (Experience, Expertise)
- [ ] Ar yra konkretūs faktai (metai, skaičiai, statistika)?
- [ ] Ar yra tikri atsiliepimai su vardais?
- [ ] Ar minima patirtis konkrečiai ("Dirbame nuo 2010 m.")?
- [ ] Ar tekstas parašytas kaip ekspertas, ne kaip AI?

### Pasitikėjimas (Trust)
- [ ] Kontaktai aiškiai matomi
- [ ] Fizinis adresas
- [ ] Licencijos / sertifikatai (jei taikoma)
- [ ] Grąžinimo / garantijos politika

### Turinio gylis
- [ ] Ar puslapis atsako į vartotojo klausimą pilnai?
- [ ] Ar yra dažni klausimai (FAQ)?
- [ ] Ar yra nuotraukos / video?

---

## 6 žingsnis - lietuviška copy kokybė

Papildomai patikrink visą matomą tekstą pagal `references/seo-copy.md` ir `references/lithuanian-patterns.md`:

### Greitasis patikrinimas
- [ ] Nėra AI šablonų antraštėse ("Šiuolaikiniame sparčiai besivystančiame...")
- [ ] Nėra trijų būdvardžių sąrašų ("greitas, patikimas, profesionalus")
- [ ] CTA mygtukai lietuviškai ir liepiamojoje nuosaką ("Registruokitės", ne "Registruojies")
- [ ] "Jūs" forma visur nuosekliai
- [ ] Brūkšniai: (-) arba (–), ne (---)
- [ ] Kabutės: „..." ne "..."
- [ ] Nėra angliškų kalkių

---

## 7 žingsnis - ataskaita

### Suvestinė

```
═══════════════════════════════════════════
🔍 SEO-LT ATASKAITA: [URL arba projektas]
Verslo tipas: [vietinis / e-comm / SaaS]
Tikrinta: [data]
═══════════════════════════════════════════

BENDRAS ĮVERTINIMAS: [●●●●○] 4/5

🔴 KRITINĖS PROBLEMOS ([N])   ← blokuoja rankinimą
🟡 SVARBŪS PATAISYMAI ([N])   ← turi būti ištaisyta
🟢 GERAI ([N])                ← veikia tinkamai
═══════════════════════════════════════════
```

### Kiekviena problema - šiuo formatu

```
🔴 [Kategorija] Problemos pavadinimas
─────────────────────────────────────
Puslapis:     /paslaugos
Dabartinis:   "Profesionalios automobilių remonto ir techninio aptarnavimo..."
Siūlomas:     "Automobilių servisas Vilniuje | RevMotors"
Priežastis:   Title tag per ilgas (87 simboliai > 60), AI stilius
Prioritetas:  AUKŠTAS - tiesiogiai veikia CTR Google paieškoje
```

### Ataskaitos skyriai pagal prioritetą

```
━━━ 🔴 KRITINĖS PROBLEMOS (taisyti pirma) ━━━
[problemos]

━━━ 🟡 SVARBŪS PATAISYMAI ━━━
[problemos]

━━━ 📊 TECHNINĖ BŪKLĖ ━━━
robots.txt:     ✅ / ❌
sitemap.xml:    ✅ / ❌
Schema:         ✅ Rasta / ⚠️ Nerasta / ❌ Klaidinga
HTTPS:          ✅ / ❌
Mobile:         ✅ / ⚠️ / ❌

━━━ 📝 ON-PAGE SUVESTINĖ ━━━
Puslapis          Title    Meta     H1      Schema
/                 ✅60     ✅145    ✅      LocalBiz
/paslaugos        ❌87     ⚠️95     ✅      -
/kontaktai        ✅45     ❌52     ⚠️      -

━━━ 🏠 VIETINIS SEO (jei taikoma) ━━━
NAP nuoseklumas:  ✅ / ❌
GBP:              ✅ / ❌ / nežinoma
Vietinė schema:   ✅ / ❌

━━━ ✍️  COPY KOKYBĖ ━━━
AI stiliaus klaidos: [N] rastos
Gramatikos klaidos:  [N] rastos
```

### Veiksmų planas

```
PRIORITETAI:

1. (Šiandien)   Ištaisyti /paslaugos title tag - per ilgas, blokuoja CTR
2. (Šią savaitę) Pridėti LocalBusiness schema - kritinė vietiniam SEO
3. (Šį mėnesį)  Perrašyti 3 puslapių meta descriptions - per trumpos, be CTA
4. (Vėliau)     Pataisyti 5 AI stiliaus klaidas copy
```

---

## Svarbus pastebėjimas dėl schema markup

`WebFetch` ir `curl` **nemato** JavaScript-injekcijų schema (Yoast, AIOSEO, RankMath).
Jei rodoma "schema nerasta" - patikrink rankiniu būdu:
→ https://search.google.com/test/rich-results

---

## Projektas / URL:
$ARGUMENTS
