# Mobbin — designreferens från riktiga appar

**Källa:** Cole Caccamise, *"How to build an iOS app in 2026 (Complete Guide / with AI)"*
https://www.youtube.com/watch?v=7OiJtpeiUNw · 9 min · **sponsrad av Mobbin**
**Analyserad:** 2026-08-04

> **Beslutet nedan gäller Gym-App.** Fakta och begränsningar i filen är
> projektoberoende — domen är det inte. Se `workflows/analysmall.md`.

## Beslut per projekt

| Projekt | Beslut | Kort skäl | Villkor för omprövning |
|---|---|---|---|
| Gym-App | ⏸ **Park** | MCP:n kräver betald plan (~€10/mån) och **finns inte i vår session**. Metoden bakom kan användas gratis | När designrundan kräver mönster vi inte hittar fritt, eller när flera projekt behöver den samtidigt |

---
# FAKTA — gäller alla projekt

## Vad
Ett bibliotek med skärmdumpar och flöden från **publicerade** appar — inte mockuper.
Enligt Mobbin: 621 500+ skärmar och 142 200+ flöden. Sedan 2026-05-12 finns en officiell
**MCP-server** som låter Claude Code, Cursor och Codex söka direkt.

## Kostnad
Gratisplanen ger tillgång till biblioteket i webben. **MCP:n ingår INTE i gratisplanen** —
den kräver betald plan, Pro från ca **€10/månad** vid årsbetalning.

## Begränsningar
- **MCP kräver betalning.** Regel 2 säger gratis före betalt, så det är ett aktivt val.
- **Sponsrat innehåll.** Videon är betald av Mobbin, vilket inte gör påståendena falska men
  betyder att nackdelar inte kommer nämnas.
- Skärmdumpar från publicerade appar är **upphovsrättsskyddade bilder**. De får studeras;
  gränsen är densamma som i `CLAUDE.md` §7.2b — mönster är fria, kopior är det inte.

---

## 🎯 Metoden är det värdefulla, och den är gratis

Videons bästa del handlar inte om verktyget:

> *"Ett av de enklaste sätten att få din app att kännas som AI-slop är att be en AI-agent
> generera UI från en tom prompt."*

Och den avgörande formuleringen om hur Mobbin faktiskt används:

> *"Det viktiga är att jag **inte** ber den kopiera en skärm eller magiskt göra mitt UI
> snyggare. Jag ber den hitta publicerade exempel, **bryta ned deras struktur, och berätta
> vad mönstren är.** Sedan bygger jag något som passar min app — med mycket bättre kontext
> innan den börjar koda."*

**Det är exakt gränsen vi redan dragit** i `CLAUDE.md` §7.2b för AGPL-kod: studera mönster,
kopiera aldrig. Att samma gräns dyker upp igen från ett helt annat håll är ett gott tecken på
att den är rätt.

## Den andra meningen, som träffade en verklig lucka hos oss

> *"Jag la lite tid på att förstå hur den här typen av app faktiskt ska fungera. **Inte bara
> hur den ska se ut**, utan vad riktiga appar gör i de delar av flödet man inte tänker på
> först. Saker som **tomma tillstånd, laddningstillstånd, feltillstånd** och alla de små
> besluten som får en app att kännas färdig."*

**Det är precis vad Gym-App saknade, och det upptäcktes samma dag oberoende av videon:**

- Startskärmen är en rubrik och en knapp på 550 px svart — ett **tomt tillstånd** som aldrig
  designades
- En övning utan historik gav tre rader `0 kg × 8` — det **tomma fallet** i en app byggd
  kring spökdata
- Justeringsarket var 126 px högre än skärmen, så värdet låg utanför — ett fel som bara syns
  i ett tillstånd man når efter fyra klick

`DESIGN.md` §3 listar tomma tillstånd som "skissas när skärmarna byggs". **Det var för svagt.**
Videon säger att de ska undersökas *före*, och den har rätt — de är inte polering utan en del
av flödet.

## Vad vi gör i stället, tills vidare

Samma metod utan Mobbin: **hitta publicerade exempel, bryt ned strukturen, härled mönstren.**

Det är exakt vad som redan gjordes 2026-08-04 — referensbilderna i `docs/Reference-pics/`
lästes för mönster (Hevy: PB som chip, timer i flödet; MacroFactor: stor siffra + liten
etikett; Liftosaur: uppvärmning märks med ord, inte färg). Skillnaden mot Mobbin är att
sökningen är manuell och urvalet mindre — inte att metoden är en annan.
