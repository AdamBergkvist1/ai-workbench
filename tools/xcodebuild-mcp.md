# XcodeBuildMCP

**Källa:** Chris Raroque, "I'm keeping my $200/mo Claude Code plan (UPDATED workflow)"
https://www.youtube.com/watch?v=9vPyxCucxqI
**Analyserad:** 2026-08-03
**Beslut:** **Park**

> ⏰ **Villkor för att ta upp igen:** när jag börjar bygga en native iOS-app och har en Mac.
> Påminn mig om denna fil då.

## Vad
En gratis MCP-server (byggd av Sentry) som låter Claude Code styra Xcode och iOS-simulatorn:
bygga appen, starta simulatorn, trycka på saker på skärmen, ta skärmdumpar och hämta loggar.

## Kontext
Chris bygger native iOS-produktivitetsappar på en M4 Max. Han säger att den täcker ~90 % av
det han gjorde i Xcode, och att han numera har Xcode stängt större delen av tiden.

## Kostnad
Gratis.

## Vad det skulle ersätta hos mig
Ingenting i dag. På sikt: den manuella loopen där jag kör simulatorn själv, tar skärmdumpar
och klistrar in loggar.

## Passar för att
Det löser exakt samma problem som Playwright löser för webb — att AI:n kan verifiera sitt
eget arbete i stället för att jag ska beskriva buggar i ord. Den loopen har bevisat sig vara
den enskilt största tidsvinsten i Gym-App.

## Passar INTE för att
- Kräver **macOS och Xcode**. Jag utvecklar på Windows.
- Jag bygger PWA, inte native. Ingen Xcode-projektfil finns att styra.
- Chris nämner själv en lucka: **komplexa multi-touch-gester** (t.ex. dra för att sortera
  om en lista) går inte att testa automatiskt. Den delen förblir manuell.

## Motsvarigheten jag faktiskt använder
För webb finns tre nivåer, och de gör olika saker:

| Verktyg | Roll | Status |
|---|---|---|
| Browser-MCP (Claude with Chrome) | **Ögon** — engångsblick, klicka, läsa konsol | Använder |
| Playwright | **Minne** — skrivna tester som körs för alltid | Använder (Gym-App) |
| XcodeBuildMCP | Ögon + händer för native iOS | Parkerad |

**Mätt sidonot 2026-08-03:** browser-MCP:ns klick krävde att webbläsarpanelen var synlig —
läsning fungerade headless, klick gjorde det inte. Playwright klickar headless och obevakat.
Det är därför de inte ersätter varandra.
