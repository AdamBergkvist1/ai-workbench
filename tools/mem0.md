# mem0 — minneslager för AI-agenter

**Källa:** issue #6 — https://vm.tiktok.com/ZN8d5km8K/ (@howtowebdev)
**Repo:** https://github.com/mem0ai/mem0 — ⭐62 501 · Apache-2.0 · Python · aktiv 2026-08-04
**Analyserad:** 2026-08-04
**Beslut:** **Skip** för Gym-App

> **Notera för framtida sökningar:** transkriptet säger *"memo"*. Repot heter **`mem0`** —
> tal-till-text renderar "mem zero" som "memo". Sök på beskrivningen, inte på ljudet.

## Vad
Ett minneslager som låter en LLM-app minnas sina användare mellan sessioner: preferenser,
fakta, sammanhang. Repots egen beskrivning: *"Universal memory layer for AI Agents"*.

## Kostnad
Open source (Apache-2.0). Självhostad kostar drift; molnvarianten kostar pengar. Kräver
dessutom embeddings, vilket är API-anrop per lagrad och hämtad minnespost.

## Vad det skulle ersätta hos mig
Två tänkbara saker, och **båda är redan lösta** — vilket är hela slutsatsen.

**(a) Att Claude minns mellan sessioner.** Det är inte vad mem0 gör. mem0 ger *min app*
minne om *mina användare*. Problemet vi faktiskt hade — att dokumentationen gled ifrån
verkligheten mellan sessioner — löstes 2026-08-03 med `npm run status` plus en `HANDOFF.md`
som mäts i stället för att minnas. Ett minneslager hade inte hjälpt: felet var inte glömska,
det var **opröfvade påståenden**.

**(b) Att Gym-Appens AI-coach minns användaren.** Redan löst strukturellt i uppgift 8.0.
Edge Function får hela katalogen, senaste utförandet per övning, typiskt viktspann, bästa
e1RM och det pågående passets set — i varje anrop.

## Passar för att
Om appen någon gång får en fritt samtalande coach där användaren berättar saker som inte
ryms i datamodellen ("jag har ont i axeln sedan i mars", "jag gillar inte marklyft"), då är
det precis det mem0 finns för.

## Passar INTE för att
- **Fel problem.** Vår kontext är redan komplett och **exakt**. mem0 byter exakt kontext mot
  *ungefärlig* hämtning via embeddings. Det är en försämring när datan får plats — och den
  får plats: payloaden är mätt under 20 000 tecken med ett test som vaktar den.
- **Fel stack.** Python-tjänst mot vår TypeScript-i-webbläsaren + Supabase.
- **⚠️ En andra kopia av träningsdatan.** Vi har byggt RLS så att varje rad är låst till
  `auth.uid()`, och verifierat isoleringen 11 av 11. Ett externt minneslager betyder att
  samma data också ligger någon annanstans, utanför de policyerna. **Ett andra ställe att
  läcka från är en verklig kostnad**, inte en teoretisk.
- Offline-first: ett nätberoende minneslager är värdelöst i en gymkällare, och vår AI-väg
  är redan konstruerad för att stå tillbaka när nätet saknas.

## Beslut
**Skip.** Kommer tillbaka först om appen får fritext-coachning där användaren berättar saker
som datamodellen inte fångar. Då är det rätt verktyg — men då är det också ett nytt problem,
inte det här.
