# Regelblock: projektets fem dokument

**Källa:** Arnie Verma, TikTok
https://www.tiktok.com/@byarnieverma/video/7664369626804915476
Transkript hämtat med [`yt-dlp`](../tools/yt-dlp.md). Guidekällorna nedan kommer från en
kommentar av *Zion Ashir* på samma video — kommentarerna bar mer konkret information än
videon själv, vilket är återkommande.

**Analyserad:** 2026-08-03
**Beslut:** **Adopt** — Gym-App hade redan fem av sex, `DESIGN.md` saknades

---

## Påståendet

> "There's no point having your agents code until you have these five documents."

| # | Dokument | Vad det innehåller | Guide enligt kommentaren |
|---|---|---|---|
| 1 | **PRD** — produktkrav | Varje kärnfunktion, exakt vad som byggs, översikten av idén | Atlassian |
| 2 | **TDD** — teknisk design | "Bibeln" för tekniska beslut: stack, verktyg, API:er | Microsoft Learn |
| 3 | **App flow** | Varje skärm, användarresor, onboarding, vad varje knapp gör | Adobe |
| 4 | **Design brief** | Färgpalett, typografi, komponenter, ungefärlig form per skärm | Wavespace |
| 5 | **Backend schema** | Tabeller, fält, datatyper, relationer | Mindstudio |
| 6 | **Engineering plan** (bonus) | Små testbara uppgifter i rätt byggordning, med beroenden och acceptanskriterier | — |

## Motiveringen som faktiskt bär

För designbriefen: *"so that the AI doesn't just build something completely random."*

Det är den skarpaste meningen i videon och gäller alla sex. **Ett dokument som inte finns
blir inte ett tomrum — det blir ett antagande som AI:n fyller i åt dig**, tyst, och som du
upptäcker först när något ser fel ut.

## Vad det gav mig konkret

Mappat mot Gym-App fanns **fem av sex redan**, under andra namn:

| Videons dokument | Min fil |
|---|---|
| PRD | `docs/SPEC.md` |
| TDD | `docs/PLAN.md` |
| App flow | `docs/PLAN.md` §2 |
| **Design brief** | **saknades** |
| Backend schema | `supabase/migrations/` |
| Engineering plan | `docs/TASKS.md` |

**Det enda som saknades var designbriefen — och det var exakt det som blockerade fas 11B.**
Att jag kände mig ur synk med projektet ("är designen färdig eller inte?") hade en konkret
orsak: dokumentet som skulle svara på frågan fanns inte.

Kommentaren säger uttryckligen *"have a design.md"*. Filen heter nu `docs/DESIGN.md` och är
en förutsättning för 11B, inte en efterhandsdokumentation.

## Passar INTE för att

- **Sex dokument innan en rad kod är fel för ett litet projekt.** Videon riktar sig till
  någon som startar från noll. Ett veckoprojekt drunknar i det.
- **Ordningen är inte helig.** Videon antyder att man skriver dem uppifrån och ner före all
  kod. I Gym-App byggdes de riskabla delarna — offline-synk, parser, RLS — *innan* designen,
  och det var rätt: hade jag designat först hade jag designat skärmar för data jag inte
  visste om jag kunde få fram. **Bygg det osäkra först, designa det vars form beror på det.**
- Guidekällorna är olika bolags marknadsföringsmaterial. Strukturen är värd något; att följa
  någon specifik mall är det inte.

## Regeln jag tar med mig

**Innan ett nytt projekt startas: gå igenom listan och namnge var varje dokument bor.**
Ett "det behöver vi inte" är ett giltigt svar — men det ska vara uttalat, för annars är det
inte ett beslut utan en lucka.
