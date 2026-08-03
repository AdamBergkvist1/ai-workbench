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

## Vid datorn

Starta en session i valfritt projekt och säg:

> Gå igenom öppna issues i `ai-workbench` och analysera dem enligt mallen i
> `workflows/analysmall.md`.

Vad som händer:

1. Claude läser issuen och hämtar det den kommer åt från länken
2. **Om det är TikTok:** transkriptet går sällan att hämta. Jag öppnar videon, kopierar
   transkriptet manuellt (eller skriver några meningar om vad den sa) och klistrar in.
   YouTube brukar gå att hämta direkt.
3. Claude fyller i mallen — **inklusive fältet "passar inte för att"**, som är obligatoriskt
4. Beslut: **Adopt** / **Park** / **Skip**
5. Anteckningen hamnar i `tools/` eller `workflows/`, issuen stängs med en länk dit

## Varför "passar inte för att" är obligatoriskt

Alla videor låter övertygande. Det är hela poängen med videor. Kravet att skriva ned
varför något *inte* passar är det enda som skiljer en analys från en önskelista.

Ett verktyg utan nackdelar betyder inte att verktyget är perfekt — det betyder att
analysen inte är gjord.

---

## Vad som INTE hör hemma här

- API-nycklar, tokens, lösenord. Aldrig. Inte ens i en stängd issue.
- Kod. Kod bor i sitt projekt. Här bor beslut och metod.
