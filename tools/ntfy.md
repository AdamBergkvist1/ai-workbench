# ntfy — push-notiser utan egen infrastruktur

**Källa:** issue #7 — https://vm.tiktok.com/ZN8d5yGKK/
**Repo:** https://github.com/binwiederhier/ntfy
**Analyserad:** 2026-08-03, nedskriven 2026-08-04
**Beslut:** **Adopt** för Gym-App — beslutad, ej byggd

> Denna fil skrevs för att `Gym-App/docs/HANDOFF.md` hänvisade till "analys i ai-workbench"
> som inte fanns. En hänvisning till ett dokument som saknas är värre än ingen hänvisning:
> den ser ut som att frågan är utredd.


> **Beslutet nedan gäller Gym-App.** Fakta och begränsningar i filen är
> projektoberoende — domen är det inte. Se `workflows/analysmall.md`.

## Vad
Skickar push-notiser till telefonen via ett HTTP-anrop. Open source, självhostbar, med
**native appar för iOS och Android**.

## Kostnad
Gratis på `ntfy.sh`. Självhostning är möjlig men **iOS kräver i praktiken relästjänsten** för
att push ska fungera — så gratisvarianten är också den enklaste.

## Problemet det löser hos oss

`HANDOFF.md` §2 dokumenterar en mätning: två larm på 180 s med appen stängd gav `wasHidden:
ja` och bara 11–20 sekunders fel. Sidans JavaScript **körde** alltså i bakgrunden och
`showNotification()` lyckades — men **iOS presenterade aldrig notisen** förrän appen kom i
förgrunden.

Följden blev att Wake Lock bär vilotimern: telefonen måste ligga framme med tänd skärm.

## Varför invändningen mot Web Push inte gäller ntfy

Web Push avfärdades för att den kräver nät **i det ögonblick larmet ska gå** — "precis vad
ett gym saknar". Två saker river den invändningen:

1. **Adam har alltid wifi eller mobilnät på gymmet.** Bekräftat 2026-08-03. Premissen var fel.
2. **ntfy stöder fördröjd leverans server-side.** Appen skickar begäran **när setet bockas
   av** — då är den framme och har nät — och ntfy:s server levererar när vilan tar slut.
   **Telefonens JavaScript behöver aldrig köra i bakgrunden.** Det var hela problemet.

Och eftersom ntfy har en **native iOS-app** presenteras notisen som en riktig notis, inte som
en webbnotis iOS håller inne.

## Passar för att
- Löser exakt det uppmätta felet, och gör Wake Lock till en bekvämlighet igen i stället för
  bärande.
- Inget nytt npm-beroende: ett `fetch` med en header räcker.
- Gratis och open source. Uppfyller regel 2.

## Passar INTE för att
- **Kräver nät när setet loggas.** Utan nät går ingen begäran iväg och vilan faller tillbaka
  på Wake Lock. Det är en degradering, inte ett haveri — men den ska vara medveten.
- **Kräver att ntfy-appen är installerad** och prenumererar på rätt ämne. Ett installationssteg
  till för varje ny användare.
- **Ämnesnamn är i praktiken hemligheter.** Vem som helst som kan gissa ämnet kan både läsa
  och skicka notiser på det. Namnet måste vara långt och slumpat, och **får inte innehålla
  något om användaren**. Notistexten ska heller inte innehålla träningsdata utöver det
  nödvändiga — "Vilan är slut" räcker.

## Beslut
**Adopt, ej byggd.** Ligger som kvarvarande småuppgift i `Gym-App/docs/HANDOFF.md` §8.
Byggs efter fas 11B — designrundan ska inte blandas med ny infrastruktur.
