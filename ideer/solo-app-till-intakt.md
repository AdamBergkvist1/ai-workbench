# Från soloutvecklare till första intäkten

**Källa:** Cole Caccamise, *"How I Code Apps SOLO That ACTUALLY MAKE MONEY (Full Guide)"*
https://www.youtube.com/watch?v=WoKmZNN6qLo · 15 min · publicerad 2026-07-26
**Analyserad:** 2026-08-04

> ⚠️ **Den här videon sponsras av Higgsfield, men handlar inte om det.** Higgsfield nämns en
> enda gång, i ett reklamavbrott. Se avsnittet längst ned — det var ett fel värt att spara.

## Vad videon handlar om
Hur han byggde en iOS-app på under två veckor med AI och fick in **$500 första månaden**,
efter år av appar som ingen använde.

## Vem som säger det
Cole Caccamise. Appen heter **Lift Byte** (undertexterna skriver också "Lift Light" — namnet
är osäkert). Det är en iOS-app för **kaloriräkning och träningsloggning**, med
differentiatorn att den **rekommenderar vikt utifrån din historik** när du kört fast.

## Påståendena

**Om idén**
- Att idén redan är tagen är **skäl att bygga, inte att avstå.** Att folk betalar för
  MyFitnessPal och Hevy bevisar att marknaden finns.
- Lös ett problem ur ditt eget liv som är **verkligt smärtsamt**.

**Om MVP:n**
- Första versionen ska lösa kärnproblemet med **en enda funktion**.
- 🎯 **Testet: "vad är den enda sak du skulle visa i en reklamfilm?"** Det tvingar fram vilken
  del av appen som måste vara tydligast och mest tillfredsställande att använda.
- Skeppa så fort det fungerar *hyfsat*, för att få riktig återkoppling.

**Om AI-kodning**
- Cursor och Codex. Förstå koden AI skriver — annars blir det säkerhetshål, oförlängbart, och
  en stor AI-räkning.
- Slappare på experimentella funktioner, långsam på känsliga delar.

**Om efter lanseringen — hans hårdaste lärdom**
- Han la **sex månader och tusentals dollar** på fler funktioner efter lansering och
  genererade **exakt $0**.
- Nu rör han produkten **bara** vid buggrapporter eller konkreta önskemål. Resten av tiden går
  till marknadsföring.

## Vad som är belagt
$500 första månaden. 50 DM:s per dag till kreatörer, mindre än 10 % blir samarbeten. Några
hundra dollar på Apple Search Ads gav en till två betalda trials. **Han säger själv att
ingendera kanalen är lönsam ännu.**

## Vad som är enbart påstått
Att influencer-marknadsföring blir en stor intäktskälla "när jag blir bättre på det". Det är
en förhoppning, inte ett resultat — och han är öppen med det.

## Förutsättningar rådet bygger på
**Att du vill ha betalande användare.** Merparten av videon — marknadsföring, DM:s, Apple
Search Ads, UGC-kreatörer — förutsätter en kommersiell app i App Store.

## Vad som talar emot, för mig
**Två tredjedelar av videon gäller inte Gym-App.** Den är en personlig app med en användare,
inte en produkt. Hela distributionsdelen är irrelevant, och den delen är videons tyngdpunkt.

Dessutom bygger han **native iOS**, vilket gör hans App Store-resonemang ogiltigt för en PWA
— samma sak som gjorde Sentry-loopen snävare för oss (`tools/sentry.md`).

---

## Det jag faktiskt tar med mig

**🎯 Reklamfilmstestet, in i fas 11B.** *"Vad är den enda sak du skulle visa i en
reklamfilm?"* — det är samma fråga som designbriefens hierarki försöker svara på, men
skarpare formulerad. För Gym-App är svaret nästan säkert **att bocka av ett set med ett
tryck och se vilan starta**. Det är det ögonblicket allt annat ska underordna sig, och det
är precis vad `DESIGN.md` §2 gör setraden störst för.

**Att bygga vidare är inte alltid arbete.** Hans sex månader för $0 är samma fälla som fanns
i vår plan: att polera vidare i stället för att köra ett riktigt pass (`10.4`). För oss
handlar det inte om intäkter utan om **verifiering** — men mekanismen är identisk. Varje gång
appen faktiskt använts har ett strukturellt fel dykt upp.

**Lift Byte är intressant som jämförelse, inte som förebild.** Den gör precis det Gym-App
avstår från (kalorier) och precis det Gym-App har data för men inte bygger — att föreslå vikt
utifrån historiken. Värd att titta på igen om `12.7` (personligt anpassat 1RM) blir aktuell.

---

## Felet det här avslöjade — spara det

Prompten i `workflows/gemini-utvardering.md` bad Gemini utvärdera *"ett verktyg som nämns i
en video"*. Det tvingar fram ett verktyg **även när videon inte handlar om något**. Gemini
hittade det enda verktyg som nämndes — sponsorn Higgsfield — och skrev en fullständig,
välformaterad, självsäker analys av **fel sak**.

Inget i svaret var uppenbart fel. Det var bara inte videon.

**Prompten har nu ett steg 0** som avgör om videon över huvud taget handlar om ett verktyg,
och som uttryckligen säger att sponsrat innehåll inte är videons ämne. Plus en **metodmall**
för videor som den här.

**Lärdomen är den återkommande:** ett svar som ser komplett ut är inte bevis för att frågan
var rätt ställd.
