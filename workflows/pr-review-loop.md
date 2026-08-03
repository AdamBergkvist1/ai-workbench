# PR-granskningsloopen

Chris Raroques loop, med `/code-review` i stället för Greptile. Gratis, samma form.

**Status:** Adopterad 2026-08-03. Ännu inte körd skarpt — flyttas hit på riktigt efter
första verkliga körningen i Gym-App.

---

## Problemet den löser

Jag är ensam. Ingen granskar min kod. AI:n som skrev koden är dessutom **fel granskare av
sin egen kod** — den har redan bestämt sig för att lösningen är rätt, annars hade den inte
skrivit den. En granskning som möter diffen utan den förhistorien hittar andra saker.

---

## Så kör jag den — i ord

**Jag skriver inte terminalkommandon. Jag säger vad jag vill ha, Claude kör.**

### 1. Innan arbetet börjar

> Vi ska bygga <funktionen>. Lägg den på en egen branch.

Claude skapar branchen. Anledningen att det inte byggs direkt på `main`: en pull request
kräver två grenar att jämföra. Utan branch finns ingen diff att granska.

### 2. När funktionen är klar

> Öppna en pull request för det här.

### 3. Granskningen

> Kör `/code-review` på den här branchen. Gå igenom varje fynd, avgör vilka som är
> verkliga, åtgärda dem, och kör om granskningen tills inget verkligt återstår.
> Redovisa vad du valde att inte åtgärda och varför.

### 4. När det är rent

> Merga den.

**Det är hela flödet.** Fyra meningar. Inga kommandon jag behöver komma ihåg.

---

## Vad de tre orden betyder, för mig som inte kodar dagligen

**Branch** — en parallell kopia av projektet. Ändringar där påverkar inte den fungerande
versionen förrän jag säger till. Går något fel kastar jag branchen och inget har hänt.

**Pull request (PR)** — en begäran om att föra in branchens ändringar i huvudversionen.
Den visar exakt vad som ändrats, rad för rad. Det är den vyn granskningen läser.

**Merge** — att faktiskt föra in ändringarna. Efter det är de en del av appen.

Poängen med hela apparaten: **allt är återkallningsbart fram till merge.**

---

## Två saker som gör att det är värt något

**"Avgör vilka som är verkliga" är inte artighet.** En granskare som åtgärdar allt den
påpekas skapar brus: onödiga null-kontroller, defensiv kod för fall som inte kan inträffa,
abstraktioner ingen bad om. Kravet att **redovisa vad som medvetet inte åtgärdades** är det
som gör granskningen läsbar i efterhand — och det låter mig invända om jag inte håller med.

**Varför loopa och inte granska en gång?** För att den första fixen introducerar ny kod som
ingen tittat på. Det är därför Chris kör tills 5/5, inte tills "kommentarerna är besvarade".

Skillnaden mot hans variant, ärligt: **hans stoppregel är ett tal, min är omdöme.** Ett tal
går inte att förhandla med. Om loopen börjar snurra utan att bli bättre är det där problemet
sitter — och då ska stoppregeln skärpas, inte verktyget bytas.

---

## Varianter

- `/security-review` — samma loop, mot säkerhet. Värt en egen runda på allt som rör
  autentisering, RLS eller nycklar.
- `/code-review ultra` — tyngre flerstegsgranskning i molnet. Kostar extra och **startas
  bara av mig**, aldrig av Claude.
