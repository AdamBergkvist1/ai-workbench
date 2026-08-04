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
| 2026-08-04 | **iOS-widgets** — retention | issue #8 | ⛔ **Skip** — PWA kan inte, dörren är stängd | [tools/ios-widgets.md](tools/ios-widgets.md) |

## Metod och idéer

| Datum | Vad | Källa | Vad det gav | Fil |
|---|---|---|---|---|
| 2026-08-03 | **De fem dokumenten** — PRD, TDD, appflöde, designbrief, schema | Arnie Verma | Avslöjade att `DESIGN.md` saknades — det som blockerade fas 11B | [rules/fem-dokument.md](rules/fem-dokument.md) |
| 2026-08-03 | **Open source först** | Strange Advanced Marketing | Blev `CLAUDE.md` §7 i Gym-App | [rules/open-source-first.md](rules/open-source-first.md) |
| 2026-08-03 | **PR-granskningsloopen** | Chris Raroque | Loopa tills inget verkligt återstår | [workflows/pr-review-loop.md](workflows/pr-review-loop.md) |
| 2026-08-04 | **Solo-app till första intäkten** | Cole Caccamise | 🎯 Reklamfilmstestet — in i fas 11B | [ideer/solo-app-till-intakt.md](ideer/solo-app-till-intakt.md) |
| 2026-08-04 | **Vad en AI-agent faktiskt är** | issue #5 | En loop plus verktyg. Resten är marknadsföring | [ideer/ai-agent-som-loop.md](ideer/ai-agent-som-loop.md) |
| 2026-08-04 | **CS-karriär, sexmånadersplan** | issue #9 | Ingen åtgärd. Projekt slår certifikat | [ideer/ingenjorskarriar-roadmap.md](ideer/ingenjorskarriar-roadmap.md) |

## Inkorg — inte utredda ännu

| Issue | Vad | Blockerat av |
|---|---|---|
| [#4](https://github.com/AdamBergkvist1/ai-workbench/issues/4) | Understand anything | 🔎 **Kunde inte identifieras.** Videon säger "open source prompt framework", men ingen sökning hittar ett matchande repo. Behöver namnet eller länken |
| [#10](https://github.com/AdamBergkvist1/ai-workbench/issues/10) | Billiga sidor för ett projekt | 🔇 **Videon saknar undertexter** och issuen har ingen beskrivning. Behöver en rad om vad den handlade om |

**Båda är öppna av ärlighet, inte av lättja.** En gissad analys hade sett likadan ut som en
riktig — och det är precis felet som fick Gemini att utvärdera en sponsor i stället för en
video.

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
