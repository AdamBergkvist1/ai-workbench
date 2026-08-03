# Regelblock: open source först

Generisk version. Klistras in i `CLAUDE.md` i nya projekt. Projektspecifika siffror
(bundle-storlek, öppna uppgifter) läggs till per projekt.

**Först skarpt använd i:** Gym-App, 2026-08-03.

---

```markdown
# SYSTEMREGLER: OPEN SOURCE FÖRST

## Grundhållningen

**Leta alltid först. Bygg själv bara när du kan säga varför.**

Att söka efter befintliga lösningar är ett standardsteg i varje ny funktion, inte
något som sparas till de stora uppgifterna. Innan du skriver den första raden av
något nytt: sök på GitHub efter vad som redan finns, och redovisa vad du hittade —
även när svaret blir "inget som passar". Att inte ha letat är aldrig ett godtagbart
skäl.

Målet är att kopiera allt eller stora delar och sedan skriva om det så det passar
oss. Det är inte fusk; det är det normala arbetssättet.

**Motvikten väger lika tungt.** Regeln gäller komplexa lösta problem — inte "skriv
aldrig kod själv":

- En plattformsprimitiv (scroll-snap, <dialog>, CSS grid, IntersectionObserver) slår
  alltid ett bibliotek som gör samma sak.
- Om alternativet till 40 egna rader är 200 kB i bundlen är de 40 raderna rätt svar.
- Men "jag kan nog bygga det bättre" är inget skäl förrän det jämförts mot något
  konkret. Har du inte letat vet du inte, och då gäller sökregeln.

**Gratis > betalt.** Free tier och open source före prenumeration, alltid.

**Data slår kod.** Det mest värdefulla — och säkraste — man hämtar utifrån är ofta
datamängder: ordlistor, ikonuppsättningar, färgskalor, domändata. Ingen körbar kod
betyder ingen supply-chain-risk. Leta där först.

**Fråga communityt.** Reddit, GitHub Issues och Stack Overflow visar vilka repos som
faktiskt används och var de går sönder — stjärnor säger inget om underhåll.

## Vad du redovisar när du hittat kandidater

2–3 alternativ med licens · senaste commit · stjärnor · gzipad storlek · antal
transitiva beroenden. Därefter en rekommendation. Sedan väntar du på beslut.

## Att införliva extern kod

Den verkliga supply-chain-risken sitter i `npm install` — postinstall-skript kör
godtycklig kod på maskinen innan en enda rad hunnit läsas. Att *läsa* främmande filer
är ofarligt. Flödet utgår från det:

1. Läs på GitHub först med `gh`. Avgör passform innan något laddas ner.
2. Klona till `temp-sandbox/` (gitignorerad). Aldrig direkt i källkoden.
3. `npm install` i sandlådan sker ALLTID med `--ignore-scripts`.
4. Kopiera källkod hellre än att lägga till ett beroende. En komponent som klistras
   in och läses igenom är granskad på riktigt. Ett beroende är det inte.
5. Cherry-picken ska vara liten nog att varje rad hinner läsas. Går det inte är den
   för stor — det är den enda säkerhetsgaranti som betyder något. En LLM-svepning
   över tiotusen rader främmande kod ger falsk trygghet, vilket är sämre än ingen.
6. Skriv om till projektets standard. Notera ursprung och licens i en kommentar
   överst i filen.
7. Verifiera med projektets fulla testsvit. Ta sedan bort sandlådan.

**Nya beroenden kräver mitt uttryckliga ja.**
```

---

## Varför regeln ser ut så här

Den ursprungliga formuleringen jag fick föreslagen var *"bygg inte det som redan är byggt"*,
rakt av. Den hade underkänt två beslut i Gym-App som var **rätta**:

- **Rullhjulen** (11A.9) byggdes på `scroll-snap` i stället för ett bibliotek, eftersom
  webbläsarens egen scroll ger rätt känsla på iOS gratis och biblioteket hade lagt hundratals
  kB på en bundle som redan var 614 kB.
- **Sparklinjen** (fas 9) ritades som rå SVG i stället för att dra in ett diagrambibliotek.

Utan motvikten gör regeln appen tyngre, inte bättre.

Men den ursprungliga poängen står kvar och är viktig: **i båda fallen letade jag aldrig.**
Besluten blev rätt av tur och magkänsla, inte av jämförelse. Det är den bristen regeln
faktiskt ska täppa till — inte att kod skrivs för hand.
