# Analysmall för verktyg och idéer

Används på allt som kommer in via `inbox`-issues. Kopiera rubrikerna rakt av.

---

## ⚠️ Fakta är projektoberoende. Domen är det aldrig.

**Upptäckt 2026-08-04.** De första analyserna skrevs som om arbetsbänken bara hade ett
projekt. `mem0.md` sa rakt av "Skip" — men skälet var att Gym-App redan skickar hela
historiken i varje anrop. **För en chatbot utan den datamodellen vore mem0 kanske rätt val.**
Nästa projekt hade läst "Skip" och trott att frågan var avgjord.

Filen ska därför ha **två lager**:

| Lager | Innehåll | Gäller |
|---|---|---|
| **Fakta** | Vad det är, licens, kostnad, verkliga begränsningar, mätvärden | Alltid, alla projekt |
| **Beslut per projekt** | Adopt / Park / Skip med skäl och villkor | Ett projekt i taget |

En begränsning hör till Fakta bara om den gäller **oavsett** vem som använder verktyget
("kör verkliga exploits", "kräver Python", "iOS kräver relätjänsten"). Gäller den bara oss
("vi har ingen testmiljö") hör den till Beslut.

Nya rader läggs till i beslutstabellen — **gamla rader skrivs aldrig om.** Att ett projekt
valde bort något är information som är värd att behålla.

---

## Mall

```markdown
# <Namn>

**Källa:** <länk>
**Repo:** <url> — ⭐N · licens · språk · senast aktiv
**Analyserad:** <ÅÅÅÅ-MM-DD>

## Beslut per projekt

| Projekt | Beslut | Kort skäl | Villkor för omprövning |
|---|---|---|---|
| Gym-App | Skip | … | … |

*(Rader läggs till. Gamla skrivs aldrig om.)*

---
# FAKTA — gäller alla projekt

## Vad
En mening. Vad är det, konkret.

## Kontext
Vem byggde det och för vad? Vilken sorts projekt hade personen som
rekommenderade det? Deras förutsättningar är sällan mina.

## Kostnad
Gratis / free tier med gräns / betalt. Ange belopp och vad som ingår.

## Vad det skulle ersätta hos mig
Namnge det befintliga. Ersätter det ingenting är det ett tillägg, och ett
tillägg måste bära sin egen vikt.

## Passar för att
Konkret, kopplat till ett verkligt behov i ett verkligt projekt.

## Passar INTE för att
**Obligatoriskt.** Finns inget svar här är analysen inte gjord.

## Beslut och nästa steg
Adopt → vilken uppgift, i vilket projekt.
Park  → vad som måste vara sant för att ta upp det igen.
Skip  → varför det inte kommer tillbaka.
```

---

## Om besluten

**Adopt** — börjar användas nu. Ska ha en konkret uppgift kopplad till sig, annars är
det inte adopterat utan bara gillat.

**Park** — bra men fel läge. Kräver ett **villkor**, inte ett "sen": *"när jag har
betalande användare"*, *"när jag skaffar en Mac"*. Utan villkor blir Park en soptunna.

**Skip** — kommer inte tillbaka. Skälet skrivs ändå ned, så att jag slipper analysera
samma sak igen om ett halvår när nästa video dyker upp.
