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
