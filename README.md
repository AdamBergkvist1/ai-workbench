# ai-workbench

Min arbetsbänk för AI-assisterad utveckling. Regler jag återanvänder mellan projekt,
arbetsflöden som visat sig fungera, och beslut om verktyg — med motiveringen kvar.

Det här är inte en länksamling. **Varje verktygsanteckning har ett beslut och ett skäl**,
och skälet gäller mig och mina projekt, inte verktyget i allmänhet.

---

### 👉 Ska jag lägga in en video? → **[GUIDE.md](GUIDE.md)**

Den enda fil jag behöver öppna. Gemini-prompten, var filen ska ligga, vad den ska heta,
och mallen att klistra in i.

### 👉 Vad finns redan? → **[REGISTER.md](REGISTER.md)**

En rad per video, med beslut och länk till filen.

---

## Vad som ligger var

| Mapp | Innehåll | Vem läser den |
|---|---|---|
| `tools/` | Verktyg: adopt / park / skip, med skäl | Jag och Claude |
| `ideer/` | Det som inte är ett verktyg — metod, principer, lärande | Jag och Claude |
| `rules/` | Block jag klistrar in i `CLAUDE.md` i nya projekt | Jag, vid projektstart |
| `projects/` | En fil per projekt: var det står, vad som är nästa | Claude |
| `workflows/` | Arbetsflöden Claude följer | **Claude — jag behöver inte läsa dem** |

## Den enda regel som håller det här levande

**Ingenting flyttas till `workflows/` förrän det använts en gång i ett riktigt projekt.**

Ett Google-dokument dör inte av dålig struktur, det dör av att allt sparas och inget
sorteras. Inkorgen får vara rörig — det är dess jobb.

## Aldrig här inne

Inga API-nycklar, tokens, lösenord eller anslutningssträngar. Inte i historiken heller —
en nyckel som committats en gång ligger kvar i git för alltid även om filen tas bort.
Nycklar bor i en lösenordshanterare.

## Aktiva projekt

- [Gym-App](projects/gym-app.md) — offline-first träningslogg (PWA), `AdamBergkvist1/Gym-App`

## Verktyg i drift

- [yt-dlp](tools/yt-dlp.md) — hämtar transkript från TikTok och YouTube
- [remote control](tools/remote-control.md) — godkänn verktygsanrop från telefonen
- [designskills](tools/design-skills.md) — inför fas 11B

## Utrett och avfärdat

- [mem0](tools/mem0.md) — Skip. Kontexten vi redan skickar ÄR minnet
- [strix](tools/strix.md) — Park. Kör verkliga exploits, och vi har bara produktion att rikta den mot
- [sentry](tools/sentry.md) — Park. Idén adopteras på vår befintliga utkorg i stället
- [iOS-widgets](tools/ios-widgets.md) — Skip. En PWA kan inte, dörren är stängd
- [ntfy](tools/ntfy.md) — Adopt, ej byggd
- [greptile och cmux](tools/greptile-och-cmux.md) — Park respektive Skip
- [XcodeBuildMCP](tools/xcodebuild-mcp.md) — Park tills det finns en iOS-app
