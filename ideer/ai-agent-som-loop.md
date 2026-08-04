# "AI-anställd" — vad en agent faktiskt är

**Källa:** issue #5 — https://vm.tiktok.com/ZN8d5gBPp/
**Analyserad:** 2026-08-04

## Vad videon handlar om
Hur man bygger en "AI-anställd" som jobbar dygnet runt. Trots ramverket är den användbara
delen en **definition**, inte en produkt.

## Den enda meningen värd att spara

> En agent är en **loop**. Den ser ett mål, tar ett steg mot det, kollar vad som hände, tar
> nästa steg, och loopar tills jobbet är gjort. Plus att den kan **nå utanför sig själv** —
> plocka upp ett verktyg, söka, köra något, anropa en app, i stället för att bara prata.
>
> **En loop plus verktyg den kan nå. Det är en agent.**

Det är den klaraste formuleringen jag sett, och den avdramatiserar ordet. Ingen magi — en
loop med verktygsåtkomst.

## Varför det är värt något ändå

Definitionen är ett **filter**. Nästa gång något marknadsförs som "AI-agent" är frågan:
*loopar den, och kan den nå utanför sig själv?* Är svaret nej på någon av dem är det en
chatbot med bättre marknadsföring.

Den förklarar också varför PR-granskningsloopen i `workflows/pr-review-loop.md` fungerar:
den **är** en loop med verktyg — granska, åtgärda, granska igen, tills inget verkligt
återstår. Och varför stoppregeln är den svåra delen: en loop utan tydligt slutvillkor snurrar
i stället för att bli klar.

## Vad som talar emot
**Resten av videon är innehållsmarknadsföring.** "Jobbar medan du sover", "blir bättre varje
dag genom att träna på allt du gör" — det senare är inte hur en agent fungerar. En agent lär
sig inte av sig själv mellan körningar; det som ser ut som lärande är kontext någon matat in.

Formatet — *"spara den här, den är längre än mina vanliga"* — är ett engagemangsknep, inte
ett tecken på djup.

## Beslut
**Behåll definitionen. Kasta resten.** Ingen åtgärd i något projekt.
