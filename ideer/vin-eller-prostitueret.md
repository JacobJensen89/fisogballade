# Idé: Vin eller prostitueret (spil nr. 2 til Fis og ballade)

Status: **på pause**. Der er ikke bygget noget. Ingen ændringer i `index.html`, `sw.js` eller Rewind.
Regel fra Jacob: der bygges intet, før han giver direkte tilladelse.

## Hvad spillet er

Spillerne får en tekst og gætter, om den handler om en **vin** eller en **prostitueret**.
Det sjove er, at teksterne er svære at skille fra hinanden. Det er anmeldelser og beskrivelser,
ikke bare navne.

Mit oprindelige bud (stadig kun et forslag): én telefon på bordet, alle bestemmer sig i det skjulte,
nedtælling 3-2-1, og så viser alle samtidig én finger for vin og to for prostitueret. Appen afslører
svaret, og der er evt. valgfri pointtælling.

## Beslutninger

- Appen er **kun til voksne** (18+). README er rettet (commit `4d8a623`).
- **Opfundne anmeldelser af prostituerede dur ikke.** Jacob siger, at legen kun virker med den ægte tone.
- Teksterne skal renses for **navn, billeder, lokation og telefonnummer**. Jacob siger, at han har
  tilladelse fra de største danske escortsider til at bruge anmeldelser og beskrivelser om dem selv.
  Jeg har ikke kunnet tjekke aftalen. Gem den skriftligt.
- Jeg må ikke gemme noget fra siderne, uden at Jacob siger det.

## Hvad jeg fandt

- **annoncelight.dk** er åben (robots.txt har ingen begrænsninger), men har ingen kundeanmeldelser.
  `/search/anmeldelser` er en søgeside med annoncer. Hver annonce har en titel (ca. 50-150 tegn) og
  et uddrag på ca. 190 tegn. Det er escorternes egne tekster, fyldt med emojis, versaler, tider,
  byer, alder og telefonnumre. De er for tydelige til legen som de står. De roligere ("naturlig",
  "unik", "oplev") kan bruges, hvis de beskæres og renses. Rensningen skal gøres manuelt tekst for tekst.
- **eroguide.dk** (forum med anmeldelser, ifølge Jacob) er spærret af Cloudflare (403,
  "Attention Required!"). Jeg har ikke set nogen anmeldelser dér. Jeg omgår ikke spærringen.
- **nympho.dk, totalescort.dk og escortguide.dk** er ikke undersøgt. Jacob afviste at tilføje dem
  til miljøet.
- **Udenlandske kilder** (kun fundet via søgning, intet åbnet): The Erotic Review, Company of Men,
  Flashback (SE), Werkenntdenbesten og tyske freier-fora. Jacob har sagt, at han har tilladelser, og
  at de kan rettes til.
- **Vin:** gode åbne kilder er Wikidata (CC0), Wikipedia og Open Food Facts. Kaggle-datasæt har uklar
  licens, og vinanmeldelser fra Vivino, Vinmonopolet og Systembolaget er ikke afklaret.

## Åbne spørgsmål

- Hvilke sider dækker aftalen præcist, og kan de sende en eksport (fil) i stedet for, at vi henter siderne?
- Skal tekster oversættes eller omskrives, eller må de stå uændret efter rensning?
- Danske, franske/italienske eller blandede navne? Point eller ingen point? Hvor mange spillere?
- Hvordan renser vi fri tekst for kælenavne, bydele, nationalitet og specifikke detaljer?

## Forslag til næste skridt

1. Bed eroguide (og evt. de andre sider) om en **eksport**: tekstfil eller regneark.
2. Eller indsæt 3-4 eksempler, så vi kan vurdere tonen.
3. Lav et lille testsæt (6-8 prostitueret-kort og 6-8 vinbeskrivelser) og spil et par runder.
4. Først derefter: bygning som selvstændigt modul, uden at røre Rewind. Husk at skifte `CACHE` i `sw.js`.

## Praktisk

- Sessionens miljø `fisogballade` (personligt) tillader kun `annoncelight.dk` og `www.eroguide.dk`.
  Det kan slettes under miljøindstillingerne.
- **Pas på:** GitHub Pages serverer rodmappen, så denne fil bliver offentlig, hvis grenen lægges i `main`.
  Fjern den eller flyt den, før den gør.
