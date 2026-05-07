# Coding challenges — en potensiell funksjon for campen

Juice Shop har en innebygd funksjon som heter **coding challenges**. Den er i dag delvis aktivert (`codingChallengesEnabled: solved` i `config/default.yml`), men vi har ikke snakket om hvordan den kan brukes pedagogisk.

Dette notatet beskriver hva funksjonen er og hva som må vurderes hvis vi vil ta den aktivt i bruk.

## Kort oppsummert

Etter at eleven har løst en vanlig hacking-utfordring, kan de få en oppfølgingsoppgave i to faser:

1. **🔍 Find It** — Eleven får vist kildekoden til butikken og skal peke ut *hvor* sårbarheten sitter.
2. **🩹 Fix It** — Eleven får vist fire alternative fikser av samme kode og skal velge den riktige. Uansett hva de velger får de en forklaring på hvorfor fiksen er bra eller dårlig.

Dekker altså både offensiv (hacking) og defensiv (fiksing) sikkerhet i samme utfordring.

## Hvordan ser det ut for eleven?

**Find It:** Eleven ser flere kodesnutter fra prosjektet og klikker på den linjen/blokken hvor de tror sårbarheten er. Riktig valg markeres med 🔍 på Score Board.

**Fix It:** Eleven ser 4 alternative fikser som tekst — f.eks. for "Admin Section":

| Valg | Forslag |
|------|---------|
| 1 | Fjern admin-ruten helt og lag en separat admin-app (riktig) |
| 2 | Bytt ut `administration` med en Base64-obfuskert sti |
| 3 | Bruk enda mer obfuskert sti |
| 4 | Bytt `AdminGuard` til `LoginGuard` |

Eleven klikker på det de tror er riktig. Serveren svarer med ✅/❌ og en forklaring:

> ❌ "Obfuscating the path to the administration section does not add any security, even if it wasn't just a trivial Base64 encoding."

Riktig valg markeres med 🩹 på Score Board.

## Hva er bra med denne funksjonen?

- **Hele sikkerhetssyklusen** — hack først, forstå hvordan det fikses etterpå
- **Ikke kodeskriving** — multiple choice med forklaringer, ingen trenger å skrive kode selv
- **Pedagogiske forklaringer** — alle fire alternativer har begrunnelse, så eleven lærer også hvorfor noe *ikke* fungerer (f.eks. at obfuskering ikke er sikkerhet)
- **Passer VGS bra** — dekker kompetansemål i IT2 om "anvende prinsipper for sikker programvareutvikling"

## Hva er utfordringer?

- **Engelsk innhold** — kodesnutter og forklaringer er på engelsk. Oversettelse til norsk krever manuell jobb per challenge.
- **Dekker ikke alle oppgaver** — ca. 35 av 106 challenges har coding challenge-del. Oppgavene må plukkes ut spesifikt.
- **Tekniske krav** — TypeScript/Angular for frontend-oppgaver, Node.js/Express for backend. Best egnet for VGS, mer krevende for ungdomsskole.
- **Vedlikehold** — hvis vi endrer kildekoden, må tilhørende kodesnutter oppdateres. CI-jobben `coding-challenge-rsn` fanger opp hvis dette glemmes.

## Hva må vi gjøre hvis vi vil bruke det aktivt?

1. **Plukke ut hvilke coding challenges som passer.** Ikke alle 35 er like relevante — noen er enkle og pedagogiske, andre er svært tekniske.
2. **Vurdere oversettelse.** Enten oversette forklaringene, eller akseptere at denne delen er på engelsk.
3. **Legge til i læringsplanen.** Markere hvilke oppgaver som også har coding challenge-del, og eventuelt gi det en egen stjernevekt.
4. **Introdusere det for elevene.** Vise 🔍 og 🩹-ikonene på Score Board og forklare hva de betyr.

## Config-innstillinger

I `config/default.yml`:

| Verdi | Betydning |
|-------|-----------|
| `never` | Coding challenges er deaktivert |
| `solved` (vår nåværende) | Låses opp når eleven har løst hacking-delen |
| `always` | Alltid tilgjengelig, også uten å ha løst hacking |

## Referanser

- Kildekode: `data/static/codefixes/` i [tenk-tech-aksje-shop](https://github.com/sb1u-tenk-tech/tenk-tech-aksje-shop)
- Serverendepunkt: `routes/vulnCodeFixes.ts`
- Offisiell dokumentasjon: [pwning.owasp-juice.shop](https://pwning.owasp-juice.shop/companion-guide/latest/part5/code-snippets.html)
