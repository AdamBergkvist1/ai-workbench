# Regelblock: AI:n ska se appen, inte få den beskriven

Generisk version. Klistras in i `CLAUDE.md` i **varje** projekt med ett gränssnitt.

**Först skarpt använd i:** Gym-App, 2026-08-04.

---

## Varför regeln finns

Playwright sattes upp i Gym-App 2026-08-03 — men användes bara som **regressionsvakt**
(kontroll att inget klipptes av på 375 px). Under hela designrundan som följde ritade jag
mot en textbrief och referensbilder **utan att någonsin titta på appen**.

Adam fick beskriva i ord vad som såg fel ut. Det var precis det arbetet verktyget skulle
avskaffa.

**När jag till slut tittade tog det fem minuter att hitta tre fel som briefen missade helt:**

1. Vikten hade förvalet `0`, så varje ny övning gav tre rader `0 kg × 8` att rätta
2. `FÖRRA`-kolumnen var radens bredaste och visade ett streck när historik saknades — det
   såg ut som ett renderingsfel
3. Justeringsarkets fyra sifferhjul visade `0 0 0 0` utan att någonstans visa det
   **sammansatta talet**. Man kunde inte se vilken vikt man ställde in

Punkt 3 ändrade ett beslut: jag var på väg att utvärdera bort rullhjulen. **Felet satt inte
i hjulen utan i att siffran saknades.** Det hade inte gått att härleda ur någon beskrivning.

---

## Regeln

```markdown
## Se gränssnittet — beskriv det inte

Playwright är inte bara en testsvit. Den är ögon.

**Innan du föreslår en designändring, och innan du säger dig vara klar med en:**
kör `npm run shots` och TITTA på bilderna. Att läsa DOM eller beräknade stilar
är inte samma sak — hierarki, tomhet och visuell tyngd syns bara i en bild.

**Skriptet ska bygga upp riktigt tillstånd, inte bara tomma vyer.** Tomma
tillstånd har alltid gått att se. Det är skärmen man faktiskt arbetar i som
aldrig granskas, och det är där felen bor.

**Kör före och efter en ändring.** Ett före/efter avslöjar sådant ingen av oss
tänkte fråga om.

**Är en skärmdump omöjlig att ta — säg det rakt ut.** Att designa vidare utan
att se är hur man ritar rätt saker på fel skärm.
```

---

## Teknisk fälla värd att känna till

**En inbyggd webbläsarpanel i ett AI-verktyg kan bara fotograferas när panelen faktiskt
visas.** En dold panel renderar inga bildrutor — skärmdumpen ger timeout — och den tar
oftast inte emot syntetiska klick heller.

Det gör den olämplig som grund för ett arbetsflöde: den fungerar när någon råkar ha rätt
fönster framme.

**Playwright har inte det problemet.** Den ritar sidan i minnet oavsett vad som visas, och
klickar headless. Ett `npm run shots`-skript som startar dev-servern, klickar sig fram till
ett verkligt tillstånd och sparar PNG-filer fungerar alltid, i CI likaväl som lokalt.

Välj motor efter var appen faktiskt körs — WebKit för iOS Safari, Chromium för desktop —
med den andra som reserv. **En skärmdump från fel motor är oändligt mycket bättre än ingen.**
