# Hur jag fångar och bearbetar idéer

Skrivet för mig själv, för att jag ska slippa komma ihåg det.

---

## På telefonen (10 sekunder)

Jag ser en video på TikTok eller YouTube som verkar användbar.

1. Öppna **GitHub-appen** → `ai-workbench` → **Issues** → **New issue**
2. Titel: verktyget eller idén, typ `XcodeBuildMCP` eller `Playwright för mobiltest`
3. Beskrivning: **klistra länken** + en rad om varför jag reagerade
4. Etikett `inbox` om jag orkar. Annars strunt samma.
5. Submit.

**Det är allt.** Ingen bedömning, ingen sammanfattning. Att sortera på telefonen är
anledningen till att man slutar fånga saker.

### Varför GitHub Issues och inte en anteckningsapp

- Fungerar från telefonen utan nya verktyg
- Versionerat och sökbart
- **Claude kan läsa det direkt** när jag sätter mig vid datorn
- En stängd issue är ett bevis på att något faktiskt bearbetades — en anteckning som
  ligger kvar säger ingenting om den är läst eller inte

---

## Vad Claude faktiskt kommer åt från en länk

**Testat skarpt 2026-08-03**, inte antaget:

| Källa | Vad som går att hämta | Vad som INTE går |
|---|---|---|
| **TikTok / YouTube** med [`yt-dlp`](tools/yt-dlp.md) | **Hela transkriptet**, när undertexter finns | Videor utan undertexter |
| **TikTok** (riktig webbläsare) | Konto, bildtext, hashtags, antal likes | Kommentarer — bakom en bot-kontroll som Claude inte får kringgå |
| **TikTok / YouTube** (rå direkthämtning) | Ingenting respektive bara titeln | Allt annat |
| **GitHub-repo, dokumentation, blogg** | I princip allt | — |

**Transkriptproblemet är löst.** `yt-dlp` hämtade en TikTok-video ordagrant identiskt med
det transkript jag tidigare kopierat för hand. Jag behöver alltså inte göra det längre —
klistra länken, be Claude hämta.

**Två saker måste fortfarande kopieras manuellt:**
- **Kommentarerna.** De är ofta det bästa i en video — folk fyller i det skaparen hoppade
  över. TikToks bot-kontroll stoppar automatisering, så de klistras in för hand när de
  är värda något.
- **Videor utan undertexter.** Sällsynt på YouTube, förekommer på TikTok.

## Det här förändrar arbetsordningen — till det bättre

**Videon är sällan källan. Verktyget är källan.**

En länk räcker nästan alltid för att få fram *namnet* på det som diskuteras. Och när namnet
är känt går Claude till den riktiga källan — repot, dokumentationen — som är både utförligare
och mer aktuell än videon.

**Bevis från första dagen:** Chris-videon sa "det finns något som heter remote control och
det är användbart". Dokumentationen gav de exakta inställningarna *och* tre begränsningar som
videon aldrig nämnde — att datorn måste vara påslagen, att sessionen dör efter ~10 minuter
utan nät, och att behörighetsfrågor inte går att kringgå. Det var begränsningarna som
avgjorde om verktyget var användbart, och de fanns inte i videon.

### Alltså:

1. **Länken ensam räcker oftast.** Claude identifierar vad det handlar om och läser sedan
   den verkliga källan.
2. **Transkript behövs bara när videon innehåller ett argument som inte finns i
   dokumentationen** — en jämförelse, en erfarenhet, ett omdöme. Exempel: Chris påstående
   att Greptile slog Bugbot över 60 PR:er. Det står ingenstans i någon dokumentation.
3. **Om transkript behövs:** YouTube har "Visa transkription" under videon — markera, kopiera,
   klistra in. TikTok har ingen sådan funktion; där får jag skriva några meningar om vad
   som sades, eller använda undertexterna.

Regeln blir: **klistra länken, låt Claude försöka, och komplettera bara om den ber om det.**

---

## Mellansteg (valfritt) — utvärdera i Gemini på jobbet

Är du nyfiken på något direkt: kör prompten i [`workflows/gemini-utvardering.md`](workflows/gemini-utvardering.md)
och klistra svaret som en **kommentar på issuen**.

Gemini gör **faktalagret** — namn, licens, kostnad, stack, begränsningar. Claude gör
**projektdomen** vid datorn. Uppdelningen står i `workflows/analysmall.md`: fakta gäller
alla projekt, domen gäller ett i taget.

**Helt valfritt.** En issue utan Gemini-kommentar fungerar precis som förut.

---

## Vid datorn

Starta en session i valfritt projekt och säg:

> Gå igenom öppna issues i `ai-workbench` och analysera dem enligt mallen i
> `workflows/analysmall.md`.

Vad som händer:

1. Claude läser issuen och identifierar vad länken handlar om
2. Claude går till den **riktiga källan** — repot, dokumentationen — och läser den
3. Claude säger till om den behöver ett transkript för att komma vidare
4. Mallen fylls i, **inklusive fältet "passar inte för att"**, som är obligatoriskt
5. Beslut: **Adopt** / **Park** / **Skip**
6. Anteckningen hamnar i `tools/` eller `workflows/`, issuen stängs med en länk dit

## Varför "passar inte för att" är obligatoriskt

Alla videor låter övertygande. Det är hela poängen med videor. Kravet att skriva ned
varför något *inte* passar är det enda som skiljer en analys från en önskelista.

Ett verktyg utan nackdelar betyder inte att verktyget är perfekt — det betyder att
analysen inte är gjord.

---

## Vad som INTE hör hemma här

- API-nycklar, tokens, lösenord. Aldrig. Inte ens i en stängd issue.
- Kod. Kod bor i sitt projekt. Här bor beslut och metod.
