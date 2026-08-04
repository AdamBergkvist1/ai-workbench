# ai-workbench

Min arbetsbänk för AI-assisterad utveckling. Regler jag återanvänder mellan projekt,
arbetsflöden som visat sig fungera, och beslut om verktyg — med motiveringen kvar.

Det här är inte en länksamling. **Varje verktygsanteckning har ett beslut och ett skäl**,
och skälet gäller mig och mina projekt, inte verktyget i allmänhet.

## Innehåll

| Mapp | Vad som ligger där |
|---|---|
| `rules/` | Block jag klistrar in i `CLAUDE.md` i nya projekt |
| `workflows/` | Arbetsflöden som är körda skarpt minst en gång |
| `tools/` | Verktygsbeslut: adopt / park / skip, med skäl |
| `projects/` | En fil per projekt: var det står, vad som är nästa |
| `CAPTURE.md` | Hur jag fångar en idé från telefonen och vad som händer sen |

## Den enda regel som håller det här levande

**Ingenting flyttas från inbox till `workflows/` förrän det använts en gång i ett riktigt
projekt.**

Anledningen: ett Google-dokument dör inte av dålig struktur, det dör av att allt sparas och
inget sorteras. Inboxen får vara rörig — det är dess jobb. `workflows/` får bara innehålla
sådant jag faktiskt kört.

## Aldrig här inne

Inga API-nycklar, tokens, lösenord eller anslutningssträngar. Inte i historiken heller —
en nyckel som committats en gång ligger kvar i git för alltid även om filen tas bort.
Nycklar bor i en lösenordshanterare.

## Aktiva projekt

- [Gym-App](projects/gym-app.md) — offline-first träningslogg (PWA), `AdamBergkvist1/Gym-App`

## Verktyg i drift

- [yt-dlp](tools/yt-dlp.md) — hämtar transkript från TikTok och YouTube. Verifierat 2026-08-03
- [remote control](tools/remote-control.md) — godkänn verktygsanrop från telefonen
- [designskills](tools/design-skills.md) — inför fas 11B

## Utrett och avfärdat

- [mem0](tools/mem0.md) — Skip. Kontexten vi redan skickar ÄR minnet
- [strix](tools/strix.md) — Park. Kör verkliga exploits, och vi har bara produktion att rikta den mot
- [sentry](tools/sentry.md) — Park. Idén adopteras på vår befintliga utkorg i stället
- [ntfy](tools/ntfy.md) — Adopt, ej byggd
- [greptile och cmux](tools/greptile-och-cmux.md) — Park respektive Skip
- [XcodeBuildMCP](tools/xcodebuild-mcp.md) — Park tills det finns en iOS-app
