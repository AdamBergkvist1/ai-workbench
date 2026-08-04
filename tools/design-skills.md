# Designskills för Claude

Fyra verktyg från samma video, fyra olika beslut.

**Källa:** issue #1 — https://vm.tiktok.com/ZN8d5VyRM/ (@nateherkai)
Transkript hämtat med [`yt-dlp`](yt-dlp.md), 2026-08-04.
**Analyserad:** 2026-08-04

---

## Vad videon faktiskt påstår

Transkriptet, komprimerat till fyra steg:

1. Installera skillsen **emil-design-eng** och **impeccable** — "de lär Claude moderna
   layouter, typografi, spacing och animationer"
2. Lägg till **taste**-skillen så Claude hämtar inspiration från riktiga sajter i stället
   för att göra generiska designer
3. Koppla på **Figma MCP** och **Playwright** så Claude kan designa, bygga och testa själv
4. Beskriv sajten du vill ha → "professionellt utseende på minuter"

Öppningsrepliken är *"Claude just killed web designers"* och avslutningen är
*"DM me this word on screen"*. Kontot är ett lead-magnet-konto; formatet är gjort för att
generera DM, inte för att väga verktyg mot varandra. **Det gör inte påståendena falska —
tre av fyra komponenter är riktiga och två av dem är bra — men det betyder att det inte
finns någon avvägning i videon. Den fanns aldrig där att hämta.**

Kommentaren i issuen pekar åt andra hållet: *"When I try these things they seem to
overcomplicate it and not produce a good design. But if I give Claude the freedom to create
it comes up with good stuff."* Den invändningen visade sig vara mätbart relevant — se
"Baslinjen" nedan.

---

## Baslinjen jag måste mäta emot först

**Anthropics egen `frontend-design`-skill finns redan.** Den är inbyggd i claude.ai/appen
och finns som gratis officiellt plugin till Claude Code (`/plugin`). Den är 55 rader, ren
markdown, och gör i princip det videon säger att man behöver tredjepartsskills för: förbjuder
generiska defaults, kräver medvetet typsnittspar, kräver en designplan innan kod.

Den listar till och med de tre utseenden AI-design klustrar kring och säger åt sig själv att
inte hamna där.

**Det här är "vad det skulle ersätta" för allt nedan.** Att jämföra Emil Kowalskis skill mot
*ingenting* är fel jämförelse — den ska jämföras mot en gratis skill jag redan har rätt till
och som jag inte har slagit på i Claude Code. Innan den är påslagen och körd en gång vet jag
inte vilket problem som återstår.

---

# 1. emilkowalski/skills — **Adopt**

## Vad
Åtta skills i ren markdown som kodar Emil Kowalskis regler för UI-polish, animation och
komponentdetaljer. Han byggde Sonner och Vaul och har jobbat på Vercel och Linear.

## Kontext
Riktar sig till frontend-utvecklare som bygger produktgränssnitt — samma sorts arbete som
fas 11B. Inte marknadsföringssajter. Det är den enda av de fyra komponenterna där
avsändarens förutsättningar liknar mina.

## Kostnad
Gratis. MIT. 24,7k stjärnor, 43 commits.

## Vad det skulle ersätta hos mig
Ingenting — det är ett **tillägg ovanpå** `frontend-design`. Tillägget bär sin egen vikt av
två skäl: det är specifikt om animation, vilket `frontend-design` bara nuddar vid, och
`prototype`-skillen bygger flera olika versioner av samma UI-bit bakom en väljare, vilket är
exakt formen på fas 11B-frågan "hur ska det se ut".

## Passar för att
- **Noll körbar kod.** Verifierat: `find skills -type f ! -name "*.md"` ger **0 filer**. Åtta
  skills, 2 213 rader markdown totalt, största filen 674 rader. Det är precis vad
  `open-source-first` menar med *data slår kod* — ingen supply-chain-risk, och litet nog att
  varje rad faktiskt går att läsa. Kravet i punkt 5 är uppfyllt på riktigt, inte på papper.
- `pick-ui-library` är en kurerad lista i stället för att låta AI:n hitta på ett eget
  toast-bibliotek. Samma funktion som min sökregel, fast förhandsbesvarad.
- Fyller den lucka `fem-dokument.md` pekade ut: designbriefen saknades, och den handlar om
  form och känsla — inte om arkitektur.

## Passar INTE för att
- **Det är till 80 % animation, inte design.** Rubriken i videon ("layouter, typografi,
  spacing") är övertolkad. Fem av åtta skills handlar uteslutande om rörelse.
- **Gym-App är en loggningsapp, inte en portfolio.** Vid ett gymset ska tummen träffa rätt
  och siffran uppdateras direkt. Animation som gör det långsammare gör appen sämre, hur
  vacker den än är. Emils egen 300 ms-regel är därför ett tak att kapa, inte ett mål.
- **Skillen innehåller en reklamrad.** `emil-design-eng` börjar med en instruktion att
  Claude ska svara med en hänvisning till hans betalkurs `animations.dev` innan den gör något
  annat. Ofarligt, men det är en instruktion i min agent som inte är min. Läst, inte antagen —
  jag klistrar in filerna manuellt och kan stryka den.
- **Installationsvägen är `npx skills add`.** Den kör kod. Filerna är markdown och kan kopieras
  för hand till `.claude/skills/` — det gör jag i stället. Regeln *nya beroenden kräver mitt
  uttryckliga ja* gäller även när "beroendet" är en installer.

## Beslut och nästa steg
**Adopt.** Konkret uppgift: **slå på `frontend-design`-pluginet i Claude Code först**, kör
`prototype` mot en enda skärm i Gym-App — passvyn — och låt den producera underlaget till
`docs/DESIGN.md`. Det är den fil som blockerar fas 11B.

Kopieras för hand från repot, inte via `npx`. `emil-design-eng` + `prototype` först;
resten av de åtta bara om de behövs.

---

# 2. pbakaus/impeccable — **Park**

> ⏰ **Villkor:** när fas 11B är körd med `frontend-design` + Emils skills och resultatet
> fortfarande ser generiskt ut. Då — och bara då — är det värt att bära den här vikten.

## Vad
Ett ramverk på 24 skills och ett tjugotal slash-kommandon (`/critique`, `/bolder`,
`/polish`, `/audit`…) som gör Claude till en opinionated designdirektör.

## Kontext
Byggt av Paul Bakaus, ex-Google. Riktat mot folk som producerar många gränssnitt och vill ha
en repeterbar kvalitetsprocess. Jag har ett projekt och en skärmuppsättning.

## Kostnad
Gratis. Apache 2.0. Över 10k stjärnor och 1,7 M installationer.

## Vad det skulle ersätta hos mig
`frontend-design` — som jag inte ens har slagit på än. Att ersätta något jag inte har testat
är inte ett beslut, det är ett hopp.

## Passar för att
- Går djupare än en stilguide: vertikal rytm, FOUT och `size-adjust`, när `clamp()` är fel
  svar. Det är teknisk precision, inte "använd fina typsnitt".
- `/teach-impeccable` skannar kodbasen och skriver en beständig kontextfil. Formen är rätt
  och identisk med slutsatsen i `fem-dokument.md`.
- Utvärderat av tredje part (Tessl), inte bara av upphovsmannen.

## Passar INTE för att
- **Storleken bryter mot min egen läsbarhetsregel.** Mätt: skill-nyttolasten är **3,3 MB över
  146 filer och ~51 600 ord**, med 36 referensfiler. Emils motsvarighet är 2 213 rader totalt.
  Punkt 5 i `open-source-first` säger att cherry-picken ska vara liten nog att varje rad hinner
  läsas — det här är tjugofem gånger för stort. En LLM-svepning över det ger falsk trygghet,
  vilket är sämre än ingen.
- **Den innehåller körbar kod, till skillnad från Emils.** Verifierat: **105 `.mjs`/`.js`-filer**
  i nyttolasten, varav fyra är **hooks** (`hook-before-edit.mjs`, `hook-admin.mjs`). Hooks kör
  automatiskt vid filredigering. Det är precis den kategori jag har en regel för — och regeln
  säger sandlåda och genomläsning först, inte installation direkt i projektet.
- **24 kommandon är fel form för mig.** `pr-review-loop.md` bygger på att jag säger fyra
  meningar och inte behöver minnas kommandon. Ett bibliotek av slash-kommandon jag ska välja
  mellan går åt motsatt håll.
- Två visuella skills som ger motstridiga instruktioner kan krocka. Kombineras den med Emils
  får jag två åsikter och ingen vet vilken som vann.

## Beslut och nästa steg
**Park** med villkoret ovan. Tas den upp igen: klona till `temp-sandbox/`, läs hooksen och
`scripts/` **innan** något installeras, och plocka referensfiler manuellt i stället för att
dra in hela ramverket.

---

# 3. taste-skill — **Park**

> ⏰ **Villkor:** när jag har 2–3 konkreta sajter eller appar vars formspråk jag vill åt.
> Utan referenser att peka på gör skillen ingenting.

## Vad
Läser en riktig sajt med webbläsare och extraherar både designtokens och *motiveringarna*
bakom dem — varför just den vitan, varför 1px inset-kant i stället för skugga.

## Kontext
Videon säger bara "the taste skill". **Det finns minst tre olika skills med det namnet**
(`senlindesign/taste-skill`, `leonxlnx/taste-skill`, `nexu-io/open-design`) med olika
upphovsmän och olika beteende. Videon namnger ingen. Det ensamt är ett skäl att inte
installera på rekommendation.

## Kostnad
Gratis. **`senlindesign/taste-skill` saknar LICENSE-fil** — verifierat, inte antaget. Ingen
licens är inte samma sak som fri licens.

## Vad det skulle ersätta hos mig
Att själv ta skärmdumpar av appar jag gillar och beskriva i ord vad jag vill ha. Den manuella
motsvarigheten fungerar redan och kostar tio minuter.

## Passar för att
- Löser rätt problem i princip: en agent med bara tokens kopierar siffror utan att förstå
  besluten, och tappar formen så fort mallen tar slut.
- Kräver Playwright, som **redan finns i Gym-App-stacken**. Ingen ny infrastruktur.

## Passar INTE för att
- **Jag har inga referenser.** Skillen tar en URL. Jag har ingen URL. Problemet i 11B är att
  jag inte vet hur det ska se ut — inte att jag vet det och saknar tokens.
- **Fel målgrupp.** Varianterna är uttryckligen byggda för landningssidor, portfolios och
  redesigner — inte för dashboards eller datatäta vyer. Gym-App är en datatät vy med tummen
  som pekdon.
- Att kopiera en annan sajts formspråk rakt av löser inte frågan `DESIGN.md` ska besvara.
  Det byter bara ut ett antagande mot någon annans.
- Oklart vilken av tre skills det gäller, och den mest sannolika saknar licens.

## Beslut och nästa steg
**Park.** Tas den upp igen: avgör först *vilken* skill det handlar om, och kontrollera
licensen innan något klonas.

---

# 4. Figma MCP — **Skip**

## Vad
Figmas officiella Dev Mode MCP-server. Låter Claude läsa strukturen i en Figma-fil direkt —
nodträd, constraints, variabler, tokens — i stället för att gissa utifrån skärmdumpar.

## Kontext
Byggd för team där en designer redan har producerat filer och en utvecklare ska implementera
dem. Det förutsätter en designer. Jag är båda, och jag designar i kod.

## Kostnad
**Inte gratis i praktiken.** Starter/Collab ger 6 anrop per månad. Riktig användning kräver
Dev- eller Full-seat på Professional, **ca $15–20/mån**.

## Vad det skulle ersätta hos mig
Ingenting. Det finns ingen Figma-fil att läsa.

## Passar för att
Om jag någon gång ritar Gym-Apps skärmar i Figma är det här bron från ritning till kod, och
den bron är verklig. Samma logik som gjorde `XcodeBuildMCP` intressant: AI:n verifierar mot
källan i stället för att jag beskriver den i ord.

## Passar INTE för att
- **Löser ett problem jag inte har.** Ingen Figma-fil finns. Verktyget läser designer; det
  skapar dem inte. Videon hoppar över exakt det steget.
- **Bryter mot *gratis > betalt*** — och till skillnad från Greptile finns här inte ens en
  gratis motsvarighet att jämföra med, eftersom det inte finns något att koppla till.
- Ett MCP äter kontextfönster löpande. Regeln *CLI framför MCP* gäller, och det här är MCP
  utan uppgift.
- Code Connect-uppsättningen är enligt användarna ett eget arbete i sig.

## Beslut och nästa steg
**Skip.** Kommer inte tillbaka om jag inte börjar designa i Figma innan jag kodar — vilket
vore ett större arbetsflödesbyte än det här verktyget motiverar. Nästa gång en video nämner
Figma MCP: det här är svaret, ingen ny analys behövs.

---

# 5. Playwright — redan i drift

Videons fjärde komponent. Finns i Gym-App-stacken sedan tidigare och är enligt
`xcodebuild-mcp.md` den enskilt största tidsvinsten i projektet. Inget att besluta.

---

## Det videon inte säger, och som är hela poängen

Videon: *"Now you just describe the website you want."*

Anthropics egen `frontend-design`-skill säger raka motsatsen i sin egen text — **briefens
egna ord vinner alltid**, och saknas briefen ska modellen hitta på en och redovisa den.

Det är samma sak som `fem-dokument.md` redan landat i, formulerat en gång till av någon
annan: **ett dokument som inte finns blir inte ett tomrum, det blir ett antagande som AI:n
fyller i åt dig.** Fyra skills ändrar inte det — de gör bara antagandet snyggare.

Kommentaren i issuen — att skillsen överkomplicerar och att fri hand ger bättre design —
går att förklara med det. Utan brief konkurrerar skillsen om att fylla tomrummet, och fyra
åsikter blir sämre än en. Med brief blir de begränsningar i stället för gissningar.

**Så: `docs/DESIGN.md` är fortfarande första steget, precis som innan den här videon fanns.
Skillen är verktyget som hjälper mig skriva den, inte det som ersätter den.**

## Ordningen

| Steg | Vad | Varför |
|---|---|---|
| 1 | Slå på `frontend-design`-pluginet i Claude Code | Gratis, officiellt, redan betalt för. Baslinjen jag saknar. |
| 2 | Kopiera in `emil-design-eng` + `prototype` för hand | MIT, ren markdown, litet nog att läsa |
| 3 | Kör `prototype` mot passvyn → `docs/DESIGN.md` | Det som faktiskt blockerar 11B |
| 4 | Fas 11B | Med brief, inte utan |
| 5 | Utvärdera om Impeccable behövs | Först nu finns ett mätvärde att jämföra mot |
