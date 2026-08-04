# Utvärdera en video i Gemini — faktalagret

**För dig när du är på jobbet, på telefonen, utan repona framför dig.**

Du gör **fakta**. Claude gör **domen** senare, vid datorn, med projekten öppna. Det är samma
uppdelning som i `analysmall.md`: fakta om ett verktyg gäller alla projekt, domen gäller ett
i taget.

---

## Det finns två lägen. Välj efter var du är.

---

# 🖥️ Läge A — du sitter vid datorn

**Detta är det vanliga. Ingen issue, ingen GitHub, inget krångel.**

1. **Kör prompten i Gemini** (rutan längre ned). Byt ut länkraden.
2. **Kopiera hela svaret.**
3. **Klistra in det i Claude-chatten.** Säg typ *"här är Geminis analys, lägg in den"*.
4. Klart. Claude skriver filen i `tools/` eller `ideer/` och lägger till raden i
   `REGISTER.md`.

**Du behöver inte skapa någon issue.** Issues finns för när du *inte* kan prata med Claude.
Sitter du redan här är de bara ett extra steg.

> **Vill du hoppa över Gemini helt?** Ge bara länken till Claude direkt. Den hämtar
> transkriptet med `yt-dlp` och gör hela analysen. Gemini-steget finns enbart för att spara
> Claude-usage — inte för att det ger ett bättre resultat.

---

# 📱 Läge B — du är på jobbet eller ute

**Här behövs GitHub, eftersom Claude inte är med.**

1. **Lägg upp issuen** när du ser videon: länk + en rad om varför du reagerade.
2. **Kör prompten i Gemini** när du har en lucka.
3. **Klistra svaret som en KOMMENTAR på issuen:**
   > GitHub-appen → **Issues** → tryck på issuen → rutan **"Leave a comment"** längst ned →
   > klistra in → **Comment**
4. **Stäng inte issuen.** Vid datorn säger du *"gå igenom issues i ai-workbench"*.

### ⚠️ Kommentar — inte redigera issuens text

Originaltexten är **din** fångst: vad du såg och varför du reagerade. Skriver du över den
försvinner det enda som förklarar varför saken var intressant från början — och det är ofta
viktigare än vad verktyget tekniskt är. Gemini-svaret är ett **lager ovanpå**.

---

## Sammanfattat

| Var du är | Vad du gör med Geminis svar |
|---|---|
| **Vid datorn** | Klistra in det i Claude-chatten. Punkt |
| **På telefonen** | Klistra in det som kommentar på issuen |
| **Osäker** | Klistra in det i chatten. Det fungerar alltid |

---

## Prompten — kopiera allt i rutan

```
Du utvärderar innehållet i en video. Jag samlar sådana utvärderingar i ett eget
register och fattar besluten själv senare. Din uppgift är att ta fram FAKTA,
inte att rekommendera.

VIDEO: <klistra länken här>
BILDTEXT OCH KOMMENTARER: <klistra in det som står under videon, om något>

STEG 0 — AVGÖR FÖRST VAD VIDEON FAKTISKT HANDLAR OM.
Titta på videons titel och innehåll. Den handlar kanske inte om ett verktyg alls.

  A) Handlar den om ett VERKTYG  → fortsätt till steg 1, använd VERKTYGSMALLEN.
  B) Handlar den om en METOD, ETT ARBETSSÄTT eller EN ERFARENHET
     → hoppa över verktygsmallen, använd METODMALLEN längst ned.

⚠️ SPONSRAT INNEHÅLL ÄR INTE VIDEONS ÄMNE.
Nämns ett verktyg bara i ett reklamavbrott — "...who is a sponsor of this video",
"tack till X som sponsrar" — så är det INTE det videon handlar om. Utvärdera då
videons faktiska ämne, och skriv en rad: "Videon sponsras av X men handlar om Y."

Kan du inte se videons innehåll: säg det rakt ut i stället för att gissa utifrån
titeln.

GÖR SEDAN DETTA (bara om det är ett verktyg):
1. Ta reda på vad verktyget FAKTISKT heter. Uppläsning och automatiska undertexter
   förvränger namn — "memo" visade sig till exempel vara "mem0". Sök på
   beskrivningen av vad det gör, inte på hur namnet lät. Hittar du inte namnet
   säkert: skriv det rakt ut.
2. Leta upp det officiella repot eller den officiella sidan, och svara utifrån DEN.
   Inte utifrån videon.

SVARA MED EXAKT DETTA FORMAT, KORT. Börja med rubrikraden nedan, ordagrant, så att
svaret går att känna igen när det klistras in i ett register:

## Faktautvärdering (Gemini)

**Namn och länk**
**Vad det är** — en mening
**Licens** — exakt beteckning (MIT, Apache-2.0, AGPL-3.0, Unlicense, ingen…).
  Hittar du ingen: skriv "okänd licens".
**Kostnad** — gratis / free tier med gräns / betalt. Ange belopp och vad som ingår.
**Stack och krav** — språk, körmiljö, och vad som måste finnas för att kunna använda det
**Mognad** — antal stjärnor, senaste aktivitet, och om det underhålls av en person
  eller ett team
**Vad videon påstår som inte stämmer** — eller skriv "inget"
**Begränsningar** — minst två. Sådant som gäller ALLA som använder verktyget,
  inte sådant som bara gäller mig
**Vem det är byggt för** — och vem det inte är byggt för

─────────────────────────────────────────────────────────────
METODMALLEN — använd denna i stället om videon handlar om ett
arbetssätt, en erfarenhet eller en idé i stället för ett verktyg:

## Faktautvärdering (Gemini)

**Vad videon handlar om** — en mening
**Vem som säger det** — namn, och vad personen faktiskt har gjort
**Påståendena** — punktlista, de konkreta råden. Inga omskrivningar
**Vad som är belagt** — siffror, resultat, sådant som går att kontrollera
**Vad som är enbart påstått** — det som låter konkret men inte har någon grund
**Förutsättningar rådet bygger på** — vad måste vara sant om läsaren för att det
  ska gälla? (t.ex. "har betalande användare", "bygger native iOS", "söker jobb")
**Vad som talar emot** — minst en sak. Obligatoriskt
─────────────────────────────────────────────────────────────

REGLER (gäller båda mallarna):
- Gissa aldrig. Vet du inte, skriv "vet inte". Ett osäkert svar som ser säkert ut
  är sämre än inget svar.
- Ge INGEN rekommendation. Säg inte om jag borde använda det. Du känner inte mina
  projekt, och den bedömningen görs någon annanstans.
- Under 300 ord.
```

---

## TikTok respektive YouTube

**YouTube:** klistra bara länken. Gemini kommer oftast åt innehållet.

**TikTok:** Gemini ser sannolikt **inte** videon. Klistra därför också in:
- bildtexten under videon
- **kommentarerna som verkar vettiga** — de bär ofta mer konkret information än videon.
  (Guidekällorna till de fem dokumenten stod bara i en kommentar. Chris bekräftelse om
  App Store-uppdateringar likaså.)

Räcker inte det spelar det ingen roll — Claude kan hämta transkriptet med `yt-dlp` vid
datorn. **Gemini-steget är en genväg, inte ett krav.**

---

## Om formatet — och vad som händer om Gemini inte lyder

Prompten ber om **exakta rubriker** i fetstil, vilket renderas rätt i en GitHub-kommentar.
Första raden är alltid `## Faktautvärdering (Gemini)` — den finns där så att jag direkt ser
att det är Geminis fakta och inte din egen anteckning.

**Men lyd inte formatet slaviskt.** Hoppar Gemini över en rubrik, svarar på engelska, eller
skriver rakt text i stället för rubriker — **klistra in det ändå.** Jag läser det oavsett.

Formatet finns av två skäl, och inget av dem är strikthet:

1. **Rubrikerna tvingar Gemini att svara på allt.** Utan `**Licens**` som egen rad hoppas den
   ofta över — och licensen är det som avgör om vi ens får röra koden.
2. **Du ska kunna skumma det på telefonen** utan att läsa ett stycke löptext.

Saknas något viktigt fyller jag i det vid datorn. **Ett ofullständigt svar är oändligt mycket
bättre än inget svar** — och långt bättre än ett komplett svar som är gissat.

---

## Varför prompten ser ut som den gör

**"Ta reda på vad det FAKTISKT heter" ligger först** eftersom det felet redan hänt: ett
transkript sa *"memo"* och verktyget hette `mem0`. En utvärdering av fel verktyg är värre än
ingen utvärdering.

**"Svara utifrån repot, inte videon"** eftersom videon är marknadsföring. Dokumentationen till
remote control gav tre begränsningar som videon aldrig nämnde — och det var de som avgjorde
om verktyget dög.

**"Minst två begränsningar"** är samma regel som `Passar INTE för att` i analysmallen. Ett
verktyg utan nackdelar betyder inte att verktyget är perfekt, det betyder att analysen inte är
gjord.

**"Ge ingen rekommendation"** är det viktigaste. Gemini vet inte att Gym-App redan skickar hela
historiken i varje anrop, eller att bundlen ligger på 185 kB, eller att vi inte får kopiera
AGPL-kod. En rekommendation utan den kunskapen låter auktoritativ och är gissning.
