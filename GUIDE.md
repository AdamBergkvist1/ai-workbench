# Så här gör jag

**Den enda filen jag behöver öppna.** Allt om att fånga en video och lägga in den står här.

---

# 1. Jag ser en video

**Vid datorn?** Hoppa direkt till steg 2.

**På telefonen?** Lägg upp en issue så jag inte glömmer:
> GitHub-appen → `ai-workbench` → **Issues** → **New issue** → titel + länk + en rad om
> varför jag reagerade → **Submit**

Issuen är bara en påminnelse. Den ersätter ingenting.

---

# 2. Jag kör analysen i Gemini

Kopiera hela rutan. Byt ut länkraden. Skicka.

```
Du utvärderar innehållet i en video. Jag samlar sådana utvärderingar i ett eget
register och fattar besluten själv senare. Din uppgift är att ta fram FAKTA,
inte att rekommendera.

VIDEO: <klistra länken här>
BILDTEXT OCH KOMMENTARER: <klistra in det som står under videon, om något>

STEG 0 — AVGÖR FÖRST VAD VIDEON FAKTISKT HANDLAR OM.
Titta på videons titel och innehåll. Den handlar kanske inte om ett verktyg alls.

  A) Handlar den om ett VERKTYG  → använd VERKTYGSMALLEN nedan.
  B) Handlar den om en METOD, ETT ARBETSSÄTT eller EN ERFARENHET
     → använd METODMALLEN nedan.

⚠️ SPONSRAT INNEHÅLL ÄR INTE VIDEONS ÄMNE.
Nämns ett verktyg bara i ett reklamavbrott — "...who is a sponsor of this video" —
är det INTE det videon handlar om. Utvärdera då videons faktiska ämne och skriv en
rad: "Videon sponsras av X men handlar om Y."

Kan du inte se videons innehåll: säg det rakt ut i stället för att gissa utifrån
titeln.

OM DET ÄR ETT VERKTYG, GÖR OCKSÅ DETTA FÖRST:
1. Ta reda på vad verktyget FAKTISKT heter. Uppläsning och automatiska undertexter
   förvränger namn — "memo" visade sig till exempel vara "mem0". Sök på
   beskrivningen av vad det gör, inte på hur namnet lät. Hittar du inte namnet
   säkert: skriv det rakt ut.
2. Leta upp det officiella repot eller sidan, och svara utifrån DEN. Inte videon.

═══ VERKTYGSMALLEN ═══
Börja svaret med denna rad, ordagrant:

## Faktautvärdering (Gemini)

**Namn och länk**
**Vad det är** — en mening
**Licens** — exakt beteckning (MIT, Apache-2.0, AGPL-3.0, Unlicense, ingen…).
  Hittar du ingen: skriv "okänd licens".
**Kostnad** — gratis / free tier med gräns / betalt. Belopp och vad som ingår.
**Stack och krav** — språk, körmiljö, vad som måste finnas för att använda det
**Mognad** — stjärnor, senaste aktivitet, en person eller ett team bakom
**Vad videon påstår som inte stämmer** — eller "inget"
**Begränsningar** — minst två. Sådant som gäller ALLA, inte bara mig
**Vem det är byggt för** — och vem det inte är byggt för

═══ METODMALLEN ═══
Börja svaret med denna rad, ordagrant:

## Faktautvärdering (Gemini)

**Vad videon handlar om** — en mening
**Vem som säger det** — namn, och vad personen faktiskt har gjort
**Påståendena** — punktlista med de konkreta råden
**Vad som är belagt** — siffror och resultat som går att kontrollera
**Vad som är enbart påstått** — låter konkret men saknar grund
**Förutsättningar rådet bygger på** — vad måste vara sant om läsaren?
**Vad som talar emot** — minst en sak. Obligatoriskt

REGLER (båda mallarna):
- Gissa aldrig. Vet du inte, skriv "vet inte". Ett osäkert svar som ser säkert ut
  är sämre än inget svar.
- Ge INGEN rekommendation. Säg inte om jag borde använda det. Du känner inte mina
  projekt, och den bedömningen görs någon annanstans.
- Under 300 ord.
```

---

# 3. Var filen ska ligga och vad den ska heta

## Vilken mapp?

**En enda fråga avgör:**

> **Är det något man installerar, anropar eller betalar för?**
> **JA** → `tools/`  ·  **NEJ** → `ideer/`

| Exempel | Mapp |
|---|---|
| mem0, Sentry, yt-dlp, ntfy, Strix | `tools/` |
| "de fem dokumenten", "vad en agent är", karriärråd | `ideer/` |

Osäker? **Välj `ideer/`.** Det är lättare att flytta en fil än att hitta den på fel ställe.

## Vad ska den heta?

- **Verktyg:** verktygets riktiga namn. `tools/mem0.md`, `tools/sentry.md`
- **Idé:** kort beskrivning av innehållet, **inte** videons titel.
  `ideer/ai-agent-som-loop.md`, inte `ideer/how-to-build-an-ai-employee.md`

**Regler:** små bokstäver, bindestreck i stället för mellanslag, inga å ä ö, `.md` på slutet.

**Finns filen redan?** Lägg till i den i stället för att skapa en ny. Två videor om samma
verktyg ska mötas i en fil, inte ligga som två halva analyser.

---

# 4. Filmallen — kopiera detta

Skapa filen på github.com och klistra in:

```markdown
# <Namn på verktyget eller idén>

**Källa:** <videolänk>
**Analyserad:** <ÅÅÅÅ-MM-DD> av Gemini
**Status:** 🟡 FAKTA KLARA — projektbeslut saknas

> Innehållet nedan är Geminis faktalager. Ingen dom är fattad för något projekt
> ännu. Claude fyller på beslutstabellen nästa gång vi jobbar.

## Beslut per projekt

| Projekt | Beslut | Kort skäl | Villkor för omprövning |
|---|---|---|---|
| _(tomt — fylls i av Claude)_ | | | |

---

<KLISTRA HELA GEMINIS SVAR HÄR>

---

## Mina egna anteckningar

<Valfritt. Varför reagerade jag? Vad tänkte jag använda det till?>
```

**Det enda du fyller i själv:** namnet, källänken, datumet, och Geminis svar. Resten står
kvar som det är.

Raden `🟡 FAKTA KLARA` är signalen till mig att filen väntar på ett beslut.

---

# 5. Vad som händer sen

Nästa gång vi jobbar säger du bara:

> *"Kolla nya filer i ai-workbench"*

Då gör Claude tre saker: verifierar Geminis fakta, fyller i beslutstabellen för de projekt
det berör, och lägger till raden i [`REGISTER.md`](REGISTER.md).

**Du behöver aldrig röra registret själv.** En registerrad kräver ett beslut, och beslutet
är Claudes jobb.

---

# Varför uppdelningen ser ut så här

**Fakta är projektoberoende. Domen är det aldrig.**

Ett verktyg har en licens, en kostnad och verkliga begränsningar — det gäller alla som
använder det. Men om det passar *Gym-App* beror på saker Gemini omöjligt kan veta: att
bundlen ligger på 185 kB, att AGPL-kod inte får kopieras, att uppgift 8.0 redan skickar hela
historiken i varje anrop.

**Därför får Gemini uttryckligen INTE rekommendera.** En rekommendation utan den kunskapen
låter auktoritativ och är gissning — och en auktoritativ gissning i ett register man litar på
är precis det arbetsbänken finns för att undvika.

---

# Snabbfakta

| Fråga | Svar |
|---|---|
| Måste jag använda Gemini? | Nej. Ge Claude länken, den gör allt |
| Måste jag skapa en issue? | Bara om jag är på telefonen och vill minnas det |
| Vad om Gemini struntar i formatet? | Klistra in ändå. Ofullständigt slår ingenting |
| Vad om videon saknar undertexter? | Skriv en rad om vad den sa. Claude kan ofta hämta transkript ändå |
| Får jag lägga API-nycklar här? | **Nej. Aldrig.** Inte ens i en stängd issue |
