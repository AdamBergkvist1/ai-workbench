# Strix — autonom AI-penetrationstestning

**Källa:** issue #2 — https://vm.tiktok.com/ZN8d5hYTo/ (@howtowebdev)
**Repo:** https://github.com/usestrix/strix — ⭐47 890 · Apache-2.0 · Python · aktiv 2026-08-04
**Analyserad:** 2026-08-04
**Beslut:** **Park**

> ⏰ **Villkor för att ta upp igen:** när appen har användare utöver Adam **OCH** det finns en
> separat testmiljö att rikta den mot. Båda villkoren, inte det ena.

## Vad
AI-agenter som analyserar koden, **kör verkliga exploit-payloads** för att bevisa att en
sårbarhet är på riktig, och föreslår patchar. Byggd för att ligga i en CI-pipeline.

## Kostnad
Själva verktyget är gratis (Apache-2.0). **Körningen är det inte** — agenterna drivs av en
LLM, så varje svep kostar API-anrop. Relevant här: `TASKS.md` 8.1 dokumenterar att vår
Groq-nyckel delas med `news-signal-engine`, och att kvoten kan tömmas åt båda hållen.

## Vad det skulle ersätta hos mig
Den manuella kodgranskningen 2026-08-03, som gick igenom Edge Function, valideringen,
synkvägen, RLS-policyerna och `apply_mutations` — och hittade tre verkliga fynd.

## Passar för att
Angreppsytan är liten men äkta: en Edge Function som tar emot autentiserad indata och når en
extern LLM, RLS-policyer som är enda skyddet mellan två konton, och en RPC som skriver till
databasen. **Att bevisa en sårbarhet med en fungerande exploit är starkare än att resonera
sig fram till att den finns** — det är samma skillnad som mellan mätning och antagande som
gick igen hela 2026-08-03.

## Passar INTE för att
- **🔴 Den kör verkliga exploits. Vi har ingenstans att rikta den.** Vi har **en** Supabase-
  instans, och den är produktion — med riktig (om än test-) data och en RLS-uppsättning som
  bär hela säkerhetsmodellen. Att släppa autonoma agenter med exploit-payloads mot den är
  inte ett test, det är en incident som råkar vara självförvållad. Supabase har branch-
  funktion, men vi använder den inte.
- **Vi har ingen CI-pipeline.** Verktyget är byggt för att köras vid varje PR. Vi bygger via
  Vercel på push, utan testkörning i molnet. Strix hade behövt köras för hand — precis den
  manuella loop den finns för att avskaffa.
- **Fel skala.** 47 890 stjärnor speglar att företag med säkerhetsteam behöver det. Vår
  angreppsyta är några hundra rader och genomgången på en eftermiddag täckte den.
- Python + Docker mot vår stack.

## Vad jag gör i stället
`/code-review` och `/security-review` enligt `workflows/pr-review-loop.md`. Gratis, ingår i
det jag redan betalar för, och bevisligen tillräckligt: genomgången 2026-08-03 hittade en
saknad storleksgräns som kunde tömma LLM-kvoten, en API-nyckel i en query-sträng, och en
evighetsloop i utkorgen.

**Den svaghet Strix skulle täcka och som granskningen inte gör:** granskningen *resonerar*
sig fram till att något är en sårbarhet. Den kör inte exploiten. Det är en verklig skillnad,
och skälet att detta är **Park** och inte **Skip**.
