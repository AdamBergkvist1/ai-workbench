# PR-granskningsloopen

Chris Raroques loop, med `/code-review` i stället för Greptile. Gratis, samma form.

**Status:** Adopterad 2026-08-03. Ännu inte körd skarpt — flyttas hit på riktigt efter
första verkliga körningen i Gym-App.

---

## Problemet den löser

Jag är ensam. Ingen granskar min kod. AI:n som skrev koden är dessutom **fel granskare av
sin egen kod** — den har redan bestämt sig för att lösningen är rätt, annars hade den inte
skrivit den. En granskning som utgår från diffen med färska ögon hittar andra saker.

## Loopen

```
1. Bygg klart en funktion på en egen branch
2. Öppna pull request
3. Kör granskningen
4. Åtgärda allt som är verkligt (inte allt som påpekas)
5. Kör granskningen igen
6. Upprepa tills inget verkligt återstår
7. Merge
```

Poängen är **steg 6**. Att granska en gång och fixa en gång är inte samma sak — den första
fixen introducerar ny kod som ingen har tittat på.

## Så gör jag det konkret

```bash
git checkout -b funktion/nagot
```

Bygg. Committa. Sedan:

```bash
gh pr create --fill
```

Därefter, i Claude Code:

> Kör `/code-review` på den här branchen. Gå igenom varje fynd, avgör vilka som är
> verkliga, åtgärda dem, och kör om granskningen tills inget verkligt återstår.
> Redovisa vad du valde att inte åtgärda och varför.

Slutligen:

```bash
gh pr merge --squash
```

## Två saker som gör skillnad

**"Avgör vilka som är verkliga" är inte artighet.** En granskare som åtgärdar allt den
påpekas skapar brus: onödiga null-kontroller, defensiv kod för fall som inte kan inträffa,
abstraktioner ingen bad om. Kravet att **redovisa vad som medvetet inte åtgärdades** är det
som gör granskningen läsbar i efterhand.

**Chris stoppregel är ett betyg (5/5). Min är "inget verkligt återstår".** Hans är mer
objektiv — ett tal går inte att förhandla med. Min kräver omdöme, vilket är svagare. Om
loopen börjar snurra utan att bli bättre är det där problemet sitter, och då ska stoppregeln
skärpas hellre än att verktyget byts.

## Varianter

- `/security-review` — samma loop, men mot säkerhet. Värt en egen runda på allt som rör
  autentisering, RLS eller nycklar.
- `/code-review ultra <PR#>` — tyngre flerstegsgranskning i molnet. Kostar extra och startas
  bara av mig, aldrig av Claude.
