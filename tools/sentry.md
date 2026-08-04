# Sentry — kraschloggning i produktion

**Källa:** issue #11 — https://vm.tiktok.com/ZN8d5Ttkp/ (@chris.raroque)
**Analyserad:** 2026-08-04
**Beslut:** **Park** — men idén bakom adopteras, byggd på det vi redan har

## Vad
Fångar krascher i produktion och visar vad användaren gjorde, vilken enhet, och exakt vilken
rad som brast. Chris kör dessutom en daglig automation som hämtar nya kraschloggar, fixar
felen och öppnar en PR han granskar på kvällen.

## Kostnad
Free tier finns (begränsat antal fel per månad). `@sentry/browser` 10.69.0 är **2,7 MB
uppackat i 695 filer** — men *det är inte bundle-kostnaden*, eftersom paketet innehåller
flera modulformat och sourcemaps. **Den verkliga gzippade ökningen måste mätas, inte
gissas.** Vår bundle ligger på 185 kB gzip, så varje tillskott märks.

## Poängen i kommentarerna, som är bättre än videon

> **@ISRAAD VISUALS:** *om kraschen hände, betyder inte det att du måste pusha en uppdatering
> till App Store?*
> **@Chris Raroque:** *Ja, det måste du.*

**Den invändningen gäller inte oss.** Gym-App är en PWA. En fix är en `git push`, Vercel
bygger, och servicearbetaren erbjuder uppdateringen vid nästa start. Ingen granskning, ingen
väntan. **Loopen Chris beskriver är alltså snävare för oss än för honom** — vilket gör idén
mer värd, inte mindre.

## Vad det skulle ersätta hos mig
Ingenting i dag — men det täcker ett verkligt hål: **en krasch på gymmet, offline, som inte
går att återskapa efteråt.**

Det hålet är inte hypotetiskt. Bugg 11A.10 (set sparades men syntes aldrig) krävde en
direktfråga mot Postgres för att förstås, och såg ut som dataförlust under tiden. Ett fel som
inträffar i en gymkällare utan nät lämnar i dag inga spår alls.

## Passar INTE för att
- **Värdet skalar med användare man inte kan prata med.** Adam är ende användaren och kan
  berätta direkt. Chris har betalande användare som mejlar support.
- **Bundle-kostnad i en offline-first app.** Allt som precachas laddas ner en gång i en
  gymkällare. Uppgift 7.13 (614 → 642 kB precache) är fortfarande öppen; att lägga till
  innan den är löst vore att gå åt fel håll.
- **En tredjepartstjänst till** som ser användardata, vid sidan av Supabase och LLM-
  leverantören. Kraschkontext innehåller ofta datan som orsakade kraschen.

## 💡 Vad jag gör i stället — vi har redan rörledningen

**Gym-App har redan en offline-först telemetrikanal.** `ai_parse_log` skickas genom
**utkorgen**, uttryckligen därför att de flesta inmatningar sker utan nät och telemetri som
bara skrevs online hade missat de intressantaste fallen.

Exakt samma resonemang gäller krascher — och den svåraste kraschen att fånga är den som sker
offline. Rörledningen finns alltså redan, och den är byggd för precis det här fallet:

- en `error_log`-tabell på samma väg som `ai_parse_log`
- en `window.onerror` / `unhandledrejection`-hanterare som lägger raden i utkorgen
- synkas när nätet kommer tillbaka, precis som pass och set

**Noll nya beroenden, noll extra tredjepart, försumbar bundle-ökning.** Det ger inte Sentrys
gränssnitt eller gruppering — men det ger den enda del vi faktiskt saknar: *att felet
överlever resan hem från gymmet.*

## Beslut
**Park Sentry.** ⏰ **Villkor:** när någon annan än Adam använder appen.

**Adoptera idén nu, i vår egen form:** en minimal felloggning på befintlig utkorg. Läggs som
förslag till backlog i Gym-App när fas 11B är klar — inte före, eftersom designrundan inte
ska blandas med ny infrastruktur.
