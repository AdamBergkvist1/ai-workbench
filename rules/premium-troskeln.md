# Regelblock: premiumtröskeln — tillstånd, sömmar och fel

Generisk version. Klistras in i `CLAUDE.md` (eller `AGENTS.md`) i **varje** projekt med ett
gränssnitt.

**Källa:** Tim Gabe, *The Psychology of Premium Apps*, YouTube, 10 min —
https://www.youtube.com/watch?v=8EAYZe6y3I8
Transkript hämtat ur webbläsarens transkriptpanel 2026-10-18 (yt-dlp blev rate-limitad från
molnet; panelen fungerade).

**Analyserad:** 2026-10-18
**Först skarpt använd i:** — (ingen ännu)

---

## Varför regeln finns

`se-appen-sjalv.md` säger: titta på skärmen, beskriv den inte. Den regeln är sann men
ofullständig — den riktar blicken mot **lyckade skärmar i vila**. Det är precis de skärmar
AI redan gör bra.

Videons tes är att utseendet har slutat skilja produkter åt. Vem som helst kan plocka fram
något som ser proffsigt ut på en dag, så det som avgör om något känns dyrare ligger någon
annanstans: i **tillstånden**, i **sömmarna mellan skärmar**, och i **felen**. Tre ställen
som har det gemensamt att de inte syns på en skärmdump av lyckade läget.

Det är därför regeln hör hemma bredvid `se-appen-sjalv` och inte i stället för den.

---

## Vad som faktiskt är belagt

Videon slänger ur sig studier i hög takt. Jag har kollat upp de bärande.

| Påstående i videon | Vad källan faktiskt säger |
|---|---|
| "Ungefär en fjärdedel av AI:ns designresonemang når aldrig gränssnittet" | **Stämmer, och är värre än så.** [Design Theater](https://arxiv.org/abs/2607.22928) (Imteyaz m.fl., arXiv juli 2026): 24 uppgifter, 120 genererade gränssnitt, fem verktyg. Över 25 % av verktygens egna uttalade motiveringar nådde inte koden. **Funktionskraven var sämst: 34 % missar, och fyra av fem verktyg byggde 6 % eller mindre av de funktionella principerna.** |
| Service recovery-paradoxen — ett välhanterat fel kan ge nöjdare användare än inget fel | **Bara villkorat.** [Magnini m.fl. 2007](https://digitalcommons.longwood.edu/business_facpubs/210) hittar effekten när felet inte upplevs som allvarligt, användaren inte drabbats förut, och orsaken ses som tillfällig och utanför företagets kontroll. **Ett återkommande fel ger motsatt effekt.** Studien är dessutom rollspel med studenter i en enda tjänst. |
| Chromes dinosaurie spelas ~270 miljoner gånger i månaden | Stämmer, [Googles egen siffra](https://blog.google/products/chrome/chrome-dino/). Men det är ett sidospår: den är kul, inte en återhämtning. Den löser inte nätproblemet. |
| En dålig upplevelse räcker för att ungefär en tredjedel ska lämna | PwC, *Experience Is Everything* (2018), 32 %. Enkät om varumärken i allmänhet, inte om appar du redan betalat för. |
| En navigationsflytt mitt i en uppgift mer än fördubblade tiden | Den närmaste riktiga studien är *Navigational Consistency in Websites* (HCII 2009). **Observera:** [Kalbach & Bosenick](https://jodi-ojs-tdl.tdl.org/jodi/article/view/jodi-111/93) hittade ingen skillnad mellan meny till vänster och till höger. Det belagda är alltså **konsekvensen**, inte att någon viss placering är rätt. Byt inte sida för att videon sa det. |

**Och det största förbehållet:** videon är en tratt till gratis strategisamtal, nämnd två
gånger, och siffrorna +60 % / +79 % är byråns egen case-siffra utan kontrollgrupp. Metoden
håller ändå — men "premium" är delvis säljramen, inte en slutsats.

---

## Regeln

```markdown
## Tre pass innan ett gränssnitt kallas klart

Lyckade skärmar i vila är det AI redan gör bra. Det som avgör om något känns
genomarbetat ligger i tillstånden, i sömmarna och i felen. Gå de tre passen —
och skilj på att ett läge FUNGERAR och att det är FORMGIVET.

**1. Tillståndspasset.** Gå kärnflödet steg för steg. På varje steg ska
användaren kunna svara på tre frågor utan att gissa: vad hände just nu, går
det att ta tillbaka, och vad är nästa steg. Saknas ett svar är det ett fynd.
Mätt i Design Theater-studien är det här AI missar mest — funktionskraven, inte
formen.

**2. Sömpasset.** Använd produkten en längre stund som en riktig användare,
inte skärm för skärm. Användaren ser den sist byggda skärmen bredvid den först
byggda. Skriv ner varje ställe där det slutar kännas som samma produkt: två
formuleringar för samma sak, två mönster för samma handling, en knapp som
flyttat. Är samma situation löst på två sätt — välj ett och använd det på
båda ställena.

**3. Brytpasset.** Gå sönder med flit: stäng av nätet mitt i ett flöde, låt ett
externt anrop misslyckas, töm varje lista, ladda om mitt i ett tillstånd,
tryck två gånger, lägg appen i bakgrunden. Formge de lägena lika noga som de
lyckade. Ett fel som bara är HANTERAT säger "det kraschade inte". Ett fel som
är FORMGIVET säger vad som hände, vad användaren kan göra nu, och lämnar ingen
ensam.

**Att verifiera ett felläge är inte att formge det.** Står det i loggen att ett
avbrott är "verifierat utan ändrad formgivning" är passet inte gjort.

**Hitta inte på fynd.** Är ett läge redan bra, säg det och gå vidare. En lista
där allt är ett problem är lika oanvändbar som ingen lista.
```

---

## Hur det hänger ihop med resten

- **`se-appen-sjalv`** ger ögonen. Det här regelblocket säger vart de ska riktas.
- **Fynd blir uppgifter först, kod sedan.** Passen producerar en lista, inte en commit.
  I projekt med en uppgiftslista (Gym-App `docs/TASKS.md`, Party Portal `roadmap.md`)
  skrivs fyndet som en punkt innan något byggs.
- **Pass 3 är billigast.** De flesta hoppar över det helt, vilket gör det till det ställe
  där minst arbete ger störst skillnad. Börja där om tiden är kort.
- Vill du köra passen på kommando finns skillen `premium`.
