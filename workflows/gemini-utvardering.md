# Utvärdera en video i Gemini — faktalagret

**För dig när du är på jobbet, på telefonen, utan repona framför dig.**

Du gör **fakta**. Claude gör **domen** senare, vid datorn, med projekten öppna. Det är samma
uppdelning som i `analysmall.md`: fakta om ett verktyg gäller alla projekt, domen gäller ett
i taget.

---

## Så här gör du — steg för steg på telefonen

**1. Issuen finns redan.** Du la upp den när du såg videon (länk + en rad om varför).

**2. Kör prompten i Gemini.** Kopiera rutan längre ned, byt ut de två raderna längst upp,
skicka.

**3. Kopiera hela Geminis svar.**

**4. Lägg det som en KOMMENTAR på issuen:**

> GitHub-appen → **Issues** → tryck på issuen → rutan **"Leave a comment"** längst ned →
> klistra in → **Comment**.
>
> Eller `github.com/AdamBergkvist1/ai-workbench/issues` i webbläsaren — samma sak.

**5. Klart.** Stäng inte issuen. Nästa gång vi sitter vid datorn säger du bara
*"gå igenom issues i ai-workbench"*.

### ⚠️ Kommentar — inte redigera issuens text

Originaltexten är **din** fångst: vad du såg och varför du reagerade. Det är signal, och den
ska stå kvar orörd. Gemini-svaret är ett **lager ovanpå**.

Skriver du över originalet försvinner det enda som säger varför saken var intressant för dig
från början — och det är ofta viktigare än vad verktyget tekniskt är.

**Du behöver inte göra detta för alla issues.** Bara de du är nyfiken på. En issue utan
Gemini-kommentar fungerar precis som förut.

---

## Prompten — kopiera allt i rutan

```
Du utvärderar ett verktyg som nämns i en video. Jag samlar sådana utvärderingar i ett
eget register och fattar besluten själv senare. Din uppgift är att ta fram FAKTA,
inte att rekommendera.

VIDEO: <klistra länken här>
BILDTEXT OCH KOMMENTARER: <klistra in det som står under videon, om något>

GÖR SÅ HÄR FÖRST:
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

REGLER:
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
