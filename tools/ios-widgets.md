# iOS-widgets som retentionsverktyg

**Källa:** issue #8 — https://vm.tiktok.com/ZN8d5AYRT/ (@chris.raroque)
**Analyserad:** 2026-08-04

> **Beslutet nedan gäller Gym-App.** Fakta och begränsningar i filen är
> projektoberoende — domen är det inte. Se `workflows/analysmall.md`.

## Beslut per projekt

| Projekt | Beslut | Kort skäl |
|---|---|---|
| Gym-App | ⛔ **Skip** | En PWA kan inte lägga en widget på iOS hemskärm. Tekniskt omöjligt, inte bortprioriterat |

## Vad
En widget på hemskärmen som visar appens data direkt, i stället för att skicka en push-notis.
Chris kör det i tre appar: vatten i kaloriräknaren, schema i planeraren, utgifter i
budgetappen.

## Påståendet, och det är bra
> Push-notiser **försvinner**. En widget **ligger kvar** — och den tar upp minst fyra
> app-platser på hemskärmen.

Det är en verklig skillnad. En notis är en händelse som måste fångas i ögonblicket; en widget
är en yta som finns kvar. För en app byggd kring en daglig vana kan det vara mer värt än
ännu en påminnelse.

## Begränsningar — gäller alla

- **Kräver en native app.** iOS WidgetKit är stängt för webbappar. En installerad PWA kan
  ligga på hemskärmen men **kan inte leverera en widget**.
- **Egen kodbas att underhålla.** Widgeten är ett separat mål med egen datadelning och egen
  uppdateringsbudget — iOS bestämmer själv hur ofta den får uppdateras.
- **Ingen interaktivitet utöver enkla tryck.** En widget visar; den loggar inte.

## Vem det är byggt för
Native iOS-utvecklare med appar byggda kring en daglig vana. **Inte** för webbappar, och inte
för appar man öppnar när man har ett ärende.

## Varför Skip för Gym-App
Gym-App är en PWA. Beslutet togs i `PLAN.md` §2.1 och står fast. **Det här är alltså inte ett
val vi gör bort — det är en dörr som är stängd.**

Värt att notera: Gym-App har inte heller problemet. Man öppnar den **när man står vid
skivstången**, inte för att en påminnelse dök upp. Retention är inget bekymmer för en app man
själv byggt åt sig själv.

⏰ **Villkor för att ta upp igen:** om Gym-App någon gång blir native iOS. Då hör den ihop med
`tools/xcodebuild-mcp.md`, som är parkerad på samma villkor.
