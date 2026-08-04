# Registret — allt jag sparat och vad det blev

**En rad per video.** Det här är sidan att öppna när du vill se vad du faktiskt samlat på dig
och vad som kom ut av det.

| Status | Betyder |
|---|---|
| ✅ **Klar** | Analyserad, beslut fattat, fil finns |
| 🕓 **Inkorg** | Upplagd men inte utredd ännu |
| 💬 **Fakta klara** | Gemini har gjort faktalagret, projektdomen kvarstår |

---

## Verktyg

| Datum | Vad | Källa | Beslut (Gym-App) | Fil |
|---|---|---|---|---|
| 2026-08-03 | **yt-dlp** — hämtar transkript | YouTube-video | ✅ **Adopt** | [tools/yt-dlp.md](tools/yt-dlp.md) |
| 2026-08-03 | **Remote Control** — styr sessionen från telefonen | Chris Raroque | ✅ **Adopt** | [tools/remote-control.md](tools/remote-control.md) |
| 2026-08-03 | **ntfy** — push utan egen server | issue #7 | ✅ **Adopt**, ej byggd | [tools/ntfy.md](tools/ntfy.md) |
| 2026-08-04 | **Designskills för Claude** | issue #1 | ✅ **Adopt** (emilkowalski) | [tools/design-skills.md](tools/design-skills.md) |
| 2026-08-04 | **Radix Colors** — färgskalor | egen sökning | ✅ **Adopt** — i bruk i `DESIGN.md` §1 | [Gym-App/docs/EXTERNT.md](https://github.com/AdamBergkvist1/Gym-App/blob/main/docs/EXTERNT.md) |
| 2026-08-03 | **XcodeBuildMCP** — iOS-simulator | Chris Raroque | ⏸ **Park** — kräver Mac | [tools/xcodebuild-mcp.md](tools/xcodebuild-mcp.md) |
| 2026-08-03 | **Greptile** — AI-kodgranskning | Chris Raroque | ⏸ **Park** — $30/mån | [tools/greptile-och-cmux.md](tools/greptile-och-cmux.md) |
| 2026-08-04 | **Strix** — AI-penetrationstest | issue #2 | ⏸ **Park** — kör riktiga exploits | [tools/strix.md](tools/strix.md) |
| 2026-08-04 | **Sentry** — kraschloggning | issue #11 | ⏸ **Park** — idén byggs på vår utkorg | [tools/sentry.md](tools/sentry.md) |
| 2026-08-03 | **cmux** — många sessioner | Chris Raroque | ⛔ **Skip** — löser problem jag inte har | [tools/greptile-och-cmux.md](tools/greptile-och-cmux.md) |
| 2026-08-04 | **mem0** — minne mellan sessioner | issue #6 | ⛔ **Skip** — kontexten ÄR minnet | [tools/mem0.md](tools/mem0.md) |
| 2026-08-04 | **Happy** — fjärrstyrning | issue #3 | ⛔ **Skip** — Remote Control gör det gratis | [tools/remote-control.md](tools/remote-control.md) |

## Metod och idéer

| Datum | Vad | Källa | Vad det gav | Fil |
|---|---|---|---|---|
| 2026-08-03 | **De fem dokumenten** — PRD, TDD, appflöde, designbrief, schema | Arnie Verma | Avslöjade att `DESIGN.md` saknades — det som blockerade fas 11B | [rules/fem-dokument.md](rules/fem-dokument.md) |
| 2026-08-03 | **Open source först** | Strange Advanced Marketing | Blev `CLAUDE.md` §7 i Gym-App | [rules/open-source-first.md](rules/open-source-first.md) |
| 2026-08-03 | **PR-granskningsloopen** | Chris Raroque | Loopa tills inget verkligt återstår | [workflows/pr-review-loop.md](workflows/pr-review-loop.md) |

## Inkorg — inte utredda ännu

| Issue | Vad | Notering |
|---|---|---|
| [#4](https://github.com/AdamBergkvist1/ai-workbench/issues/4) | Understand anything | 🕓 |
| [#5](https://github.com/AdamBergkvist1/ai-workbench/issues/5) | How to build an ai employee | 🕓 |
| [#8](https://github.com/AdamBergkvist1/ai-workbench/issues/8) | Use widgets to keep users | 🕓 Misstanke: går inte i en PWA |
| [#9](https://github.com/AdamBergkvist1/ai-workbench/issues/9) | Tips för att lyckas som ingenjör | 🕓 Idé, inte verktyg |
| [#10](https://github.com/AdamBergkvist1/ai-workbench/issues/10) | Billiga sidor för ett projekt | 🕓 |

---

## Hur en rad hamnar här

```
Telefonen              GitHub-issue          Gemini (valfritt)      Datorn
─────────              ────────────          ─────────────────      ──────
Ser en video    →      Länk + varför    →    Faktalagret       →    Fil + rad här
                       = INKORGEN            = kommentar            = ARKIVET
                                                                    issuen stängs
```

**Issuen är inkorgen, inte arkivet.** Den är billig att skapa från telefonen och stängs när
innehållet flyttat till en fil. Filen är det som blir kvar och går att söka i.

**Varför en fil per verktyg och inte per video:** ser du två videor om samma sak ska de mötas
i samma fil, inte ligga som två halva analyser. `tools/remote-control.md` bär redan både
Chris video och den officiella dokumentationen.

**Beslut skrivs aldrig om — de läggs till.** Att ett projekt valde bort något är information
värd att behålla. Se `workflows/analysmall.md`.
