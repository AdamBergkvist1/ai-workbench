# Gym-App

Offline-first träningslogg som PWA. Repo: `AdamBergkvist1/Gym-App`.

**Uppdaterad:** 2026-08-03

Detaljerad status bor i projektets egen `docs/HANDOFF.md`. Den här filen är översikten:
var det står och vad som väntar.

## Stack

React 19 · Vite 7 · Tailwind 4 · Dexie (IndexedDB) · Supabase (Postgres + RLS + Edge
Functions) · vite-plugin-pwa · Vitest · Playwright

## Klart

Fas 0–9 och 11A. Loggning, vilotimer, synk med idempotensnycklar, historik med e1RM,
touch-först-gränssnittet, AI-reserven (byggd, ej deployad).

## Öppet

| Vad | Varför det väntar |
|---|---|
| **Fas 10 — deploy till Vercel** | Blockerar allt som kräver riktig enhet |
| **Fas 11B — designrundan** | Ska börja med en designbrief för *alla* skärmar, inte nio putsuppgifter |
| ntfy för vilotimern | Adopterad, ej byggd |
| Övningsdatabas från open source | Första skarpa provet på open source-regeln |
| Egen 1RM-kurva i stället för Epley | Backlog, kräver data över tid |

## Beslut värda att komma ihåg

**iOS presenterar inte webbnotiser i bakgrunden.** Mätt, inte gissat: sidans JavaScript
*körde* i bakgrunden och `showNotification()` lyckades — men notisen visades inte förrän
appen kom i förgrunden. Wake Lock bär därför vilotimern i dag.

Lärdomen som gäller bredare: **när en mätning och en användares upplevelse säger emot
varandra är det inte självklart att mätningen har rätt.** Diagnostiken loggade när vi
*anropade* notisen, inte när iOS *visade* den. Kontrollera först att mätningen mäter det
man tror.

**Osynlig data är värre än ett synligt fel** (11A.10). Fritext- och AI-set skrevs till
databasen men renderades aldrig, eftersom passvyn bara visade planen. Det såg ut som
dataförlust. Regeln som föll ut: planen är visningsmodellen, allt som loggas ska finnas i den.

**Designen är medvetet rå, inte färdig.** UI:t byggdes råt med flit medan de riskabla
delarna — synk, parser, RLS — mättes och verifierades. Fas 11B är där formen bestäms.

## Verktyg och arbetsflöden härifrån

- [open-source-first](../rules/open-source-first.md) — först skarpt använd här
- [pr-review-loop](../workflows/pr-review-loop.md) — adopterad, ej körd skarpt än
- [remote-control](../tools/remote-control.md) — relevant eftersom loggning sker på gymmet
