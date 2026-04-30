# Aksje-shop cheat sheets

Felles oppslagsverk for workshop-deltakerne i [tenk-tech-aksje-shop](https://github.com/sb1u-tenk-tech/tenk-tech-aksje-shop) (OWASP Juice Shop-fork).

Her samler vi sårbarheter vi finner, hvordan vi løste utfordringene og andre notater som kan være nyttige for de neste som prøver.

## Bidra

Alle kan pushe direkte til `main` — ingen PR-review nødvendig.

1. Klon repoet: `git clone git@github.com:sb1u-tenk-tech/aksje-shop-cheatsheets.git`
2. Kopier [`TEMPLATE.md`](TEMPLATE.md) inn i `cheatsheets/` med et beskrivende filnavn (f.eks. `cheatsheets/sql-injection-login.md`)
3. Fyll inn det du fant og hvordan du løste det
4. Commit og push:
   ```bash
   git add cheatsheets/
   git commit -m "Legg til cheat sheet for <utfordring>"
   git push
   ```

### Form og format

- **Én fil per utfordring eller tema** — del gjerne opp om du har flere funn
- **Åpent format** — du kan skrive akkurat så mye eller lite du vil
- **Skjermbilder**: legg i `cheatsheets/assets/` og lenk inn
- **Språk**: norsk eller engelsk — begge er greit

## Struktur

```
README.md              Denne filen
TEMPLATE.md            Mal for nye cheat sheets
cheatsheets/           Alle bidrag (én fil per utfordring)
  assets/              Bilder og vedlegg
```

## Relaterte lenker

- [tenk-tech-aksje-shop](https://github.com/sb1u-tenk-tech/tenk-tech-aksje-shop) — hovedrepoet for workshopen
- [OWASP Juice Shop pwning guide](https://pwning.owasp-juice.shop/) — offisiell løsningsguide (spoilers!)
