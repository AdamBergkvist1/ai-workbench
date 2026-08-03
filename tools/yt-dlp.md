# yt-dlp

**Källa:** https://github.com/yt-dlp/yt-dlp
**Analyserad:** 2026-08-03
**Beslut:** **Adopt** — installerad och verifierad samma dag

## Vad
Kommandoradsverktyg som hämtar undertexter, metadata och media från tusentals sajter.
Här används det bara för **undertexter** — videon laddas aldrig ner.

## Kostnad
Gratis. Unlicense (public domain).

## Vad det ersätter hos mig
Att öppna varje video, kopiera transkriptet för hand och klistra in det i chatten.

## Passar för att
- **Verifierat på riktigt, inte antaget.** Kört mot en TikTok-video jag redan hade
  transkriberat manuellt. Resultatet blev **ordagrant identiskt** — samma 29 rader.
- Samma kommando fungerar för TikTok och YouTube.
- Följer regeln *CLI framför MCP*: mindre kontextfönster, och underhålls av tusentals
  bidragsgivare i stället för att vara en enskild persons sidoprojekt.

## Passar INTE för att
- **Hämtar bara undertexter som redan finns.** Har skaparen inte slagit på dem finns
  ingenting att hämta. TikTok är ojämnt; YouTube har nästan alltid automatiska.
- Löser inte **kommentarerna**. De ligger bakom TikToks bot-kontroll och måste kopieras
  för hand.
- Får inte allt: bildtext och hashtags kommer inte med undertexterna — men de går att
  läsa med webbläsaren, se `CAPTURE.md`.

## Kommandon

Kolla först om undertexter finns:

```bash
yt-dlp --list-subs --skip-download "<länk>"
```

Hämta dem (skriver en `.vtt`-fil, laddar inte ner videon):

```bash
yt-dlp --write-subs --sub-langs "eng-US,en,sv" --skip-download -o "%(id)s.%(ext)s" "<länk>"
```

För YouTube, där undertexterna oftast är automatgenererade:

```bash
yt-dlp --write-auto-subs --sub-langs "en,sv" --skip-download -o "%(id)s.%(ext)s" "<länk>"
```

### Fälla jag gick i
`--print` tillsammans med `--write-subs` gör att **ingen undertextfil skrivs** — flaggan
tystar hela nedladdningssteget. Metadata och undertexter måste hämtas i två separata anrop.

## Om undertexter saknas
Nästa steg vore **Whisper** (tal-till-text, gratis och open source, körs lokalt). Inte
installerat, inte utrett. **Villkor för att ta upp det:** när jag stöter på en video utan
undertexter som jag faktiskt behöver innehållet i. Inte innan.

## Installation
`winget install --id yt-dlp.yt-dlp`. Installerad version: `2026.07.04`.
