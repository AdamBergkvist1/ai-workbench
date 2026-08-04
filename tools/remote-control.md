# Claude Code Remote Control

**Källa:** Chris Raroque-videon + officiell dokumentation
https://code.claude.com/docs/en/remote-control
**Analyserad:** 2026-08-03
**Beslut:** **Adopt**


> **Beslutet nedan gäller Gym-App.** Fakta och begränsningar i filen är
> projektoberoende — domen är det inte. Se `workflows/analysmall.md`.

## Vad
Kopplar en Claude Code-session som körs **på min dator** till Claude-appen på telefonen
eller claude.ai/code. Koden körs kvar lokalt — telefonen är bara ett fönster in i sessionen.

## Kostnad
Gratis, ingår i Pro/Max. Kräver claude.ai-inloggning (fungerar inte med API-nyckel).

## Vad det ersätter hos mig
Att sitta kvar vid datorn enbart för att trycka "Allow" på behörighetsfrågor.

## Passar för att
Det är precis det jag frågade efter: **godkänna verktygsanrop från telefonen** medan
arbetet fortsätter på datorn. Med push-notiser får jag en signal när något behöver mig
i stället för att jag ska hålla koll själv.

## Passar INTE för att
- **Den lokala processen måste leva.** Stänger jag terminalen eller datorn dör sessionen.
  Det är alltså inte "kör vidare medan datorn sover".
- Är datorn utan nät i mer än ca 10 minuter timeoutar sessionen och processen avslutas.
- Behörighetsfrågor **kan inte kringgås** på distans. Det är ett medvetet säkerhetsval,
  och rätt sådant — men det betyder att jag måste svara, inte att det går automatiskt.
- Vissa kommandon är lokala bara, t.ex. `/plugin` och `/resume`.

## Uppsättning

1. Installera **Claude-appen** på telefonen och logga in med samma konto.
   (`/mobile` i Claude Code visar en QR-kod för nedladdning.)
2. Slå på automatisk anslutning så jag slipper komma ihåg det:
   - **Desktop-appen:** Inställningar → Claude Code → *Enable remote control by default*
   - **Terminal:** `/config` → *Enable Remote Control for all sessions* → `true`
3. Slå på push i `/config`:
   - **Push when actions required** ← den här är hela poängen (behörighetsfrågor)
   - **Push when Claude decides** ← notis när ett långt jobb blir klart
4. Enstaka session utan att ändra förval: `claude --remote-control` i projektmappen,
   eller `/remote-control` mitt i en pågående session.

Telefonen: **Claude-appen → Code** i navigeringen → sessionen ligger där med grön prick.

## Om notiserna uteblir
- `/config` visar *No mobile registered* → öppna appen på telefonen så den uppdaterar sin
  push-token.
- iOS: Fokuslägen och notissammanfattningar kan hålla inne pushen.
  Inställningar → Notiser → Claude.
- Notiser hoppas över medan jag är aktiv i terminalen på datorn — med flit.

## Relaterat, värt att kolla senare
**Dispatch** — skicka en uppgift från telefonen som startar en session på datorn.
Andra hållet jämfört med remote control: här startar jag jobbet från telefonen.
https://code.claude.com/docs/en/desktop
