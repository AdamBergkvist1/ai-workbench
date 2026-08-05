Faktautvärdering (Gemini)
Namn och länk DESIGN.md (och biblioteket designmd.app)

Länk: https://designmd.app/

Vad det är Ett format och öppet filbibliotek med strukturerade designsystem-specifikationer (i Markdown och YAML) som AI-kodagenter läser för att generera konsekventa användargränssnitt.

Licens Okänd licens (plattformen beskrivs som "open-source library", men exakt licensbeteckning framgår inte tydligt).

Kostnad Gratis.

Stack och krav Kräver en kompatibel AI-kodagent (exempelvis Claude Code, Cursor, Windsurf eller Cline) samt att design-filen placeras i projektets repo där agenten kan läsa den.

Mognad Den officiella format-specifikationen är utvecklad av Google. Biblioteket på designmd.app innehåller över 460 dokumenterade designfiler. Verktyget har haft mycket hög aktivitet och spridning under våren 2026.

Vad videon påstår som inte stämmer Inget felaktigt identifierat utifrån kommentarerna, men en tittare förtydligar att processen (att bygga med formatet) fungerar bäst med terminalverktyget Claude Code snarare än vanliga chatt-klienter.

Begränsningar - Eftersom AI-modeller isolerar varje prompt måste DESIGN.md-filen alltid rymmas och skickas med i agentens kontextfönster för att designen ska hållas konsekvent.

Arbetsflödet tvingar fram att visuella designregler måste definieras som text och YAML-variabler, vilket inte passar användare som enbart vill arbeta i grafiska ritverktyg.

Vem det är byggt för Byggt för utvecklare och designers som använder AI för att koda gränssnitt och vill undvika generisk "AI-design" (design drift). Det är inte byggt för personer som uteslutande vill skapa UI manuellt utan AI-assistans.
