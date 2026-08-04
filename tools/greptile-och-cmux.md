# Greptile och cmux

Två verktyg från samma video, båda avfärdade — men av olika skäl.

**Källa:** https://www.youtube.com/watch?v=9vPyxCucxqI
**Analyserad:** 2026-08-03

---

# Greptile — **Park**

> ⏰ **Villkor:** när jag har betalande användare eller jobbar i ett team som granskar
> varandras kod.


> **Beslutet nedan gäller Gym-App.** Fakta och begränsningar i filen är
> projektoberoende — domen är det inte. Se `workflows/analysmall.md`.

## Vad
AI-kodgranskning som kommenterar varje pull request automatiskt och sätter betyg 1–5.

## Kostnad
Ca **$30/månad**. 14 dagars test utan kort.

## Vad det skulle ersätta hos mig
`/code-review`, som ingår i det jag redan betalar för.

## Passar för att
Chris kör 60+ PR:er i månaden som soloutvecklare utan någon som granskar. Betyget 1–5 ger
dessutom en **maskinläsbar stoppregel** — man kan låta AI:n loopa tills den får 5/5. Det är
den smarta delen och den är värd att stjäla oavsett verktyg.

## Passar INTE för att
- Bryter mot min egen regel *gratis > betalt* när jag redan har en gratis motsvarighet.
- $30/mån för ett hobbyprojekt utan användare är fel prioritering.
- Chris betalar för trygghet i **produktion med riktiga användare**. Jag har inga.

## Vad jag gör i stället
Se `workflows/pr-review-loop.md` — samma loop, med `/code-review`.

---

# cmux — **Skip**

## Vad
En app för att köra många Claude Code-instanser samtidigt: sidopanel med alla projekt,
inbyggda notiser, och betydligt lägre minnesanvändning än att köra Claude Code inuti Cursor.

## Kostnad
Gratis.

## Passar för att
Chris kör 10–20 instanser parallellt. Då är minnesåtgång och notiser verkliga problem.

## Passar INTE för att
- Jag kör **ett projekt i taget**. Det löser ett problem jag inte har.
- Fokuserat på macOS. Jag är på Windows.
- Notisdelen — den enda biten jag faktiskt ville ha — får jag gratis via
  [remote control](remote-control.md) med push till telefonen.

## Kommer inte tillbaka om inte
Jag börjar köra flera projekt parallellt dagligen. Då är det minnesåtgången som avgör,
inte sidopanelen.
