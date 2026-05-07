# Login Admin

**Kategori:** Injeksjon (SQL)
**Vanskelighetsgrad:** ⭐⭐
**Mål:** Logg inn som administrator uten å kjenne passordet.

## Hint

Hintene gir gradvis mer hjelp. Prøv hint 1 først, og gå videre bare om du står fast.

### Hint 1
Når du logger inn, sender nettsiden det du skriver til en database. Hvis du skriver noe spesielt i e-post-feltet, kan du *lure* databasen til å slippe deg inn uten riktig passord.

### Hint 2
Prøv å skrive `' OR 1=1--` (med apostrof foran) som e-post. Skriv hva som helst som passord. Hva skjer?

### Hint 3
Dette kalles SQL-injeksjon – du la inn ekstra instruksjoner som databasen tolket som en kommando. `1=1` er alltid sant, så databasen svarer "ja, slipp dem inn som første bruker i listen" – og det er admin.
