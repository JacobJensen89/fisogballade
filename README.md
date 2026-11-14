# Fis og ballade

Samling af små selskabsspil kun til voksne. Én PWA, én telefon, ingen server, ingen konto.
Første spil: **Rewind**. Flere spil kommer senere som egne moduler på forsiden.

## Hvad Rewind er

1. Optageren ser et kendt navn (engelsk) og siger det højt. Knappen holdes nede, mens man taler.
2. Appen spiller optagelsen baglæns. Optageren siger den baglæns lyd, så godt det kan lade sig gøre.
3. Appen vender efterligningen om og spiller den forlæns i højttaleren. De andre gætter.
4. Optageren trykker "Vis svar". Navnet vises, og originalen kan høres.

Telefonen bliver hos optageren hele runden. Gætterne lytter kun.

## Filer

| Fil | Hvad |
| --- | --- |
| `index.html` | Hele appen i én fil (HTML, CSS, JavaScript). Ingen byggetrin |
| `manifest.webmanifest` | Navn, farver og ikoner, så den kan installeres |
| `sw.js` | Offline-fil. **Skift `CACHE`-navnet, hver gang en fil ændres** |
| `icons/` | App-ikoner (192, 512, maskable, Apple) |
| `fonts/` | Big Shoulders Display og Atkinson Hyperlegible (OFL-licens), lokale kopier |
| `.nojekyll` | Får GitHub Pages til at servere filerne uændret |

Alle stier er relative, så appen virker både på `brugernavn.github.io/repo-navn/` og på eget domæne.

## Det skal du gøre (Claude Code)

1. Læg alle filer i roden af repoet (`index.html` skal ligge i roden) og commit.
2. Slå GitHub Pages til: Settings → Pages → Deploy from a branch → `main` → `/ (root)`. Vent til adressen er oppe.
3. Tjek, at siden åbner over https, og at `sw.js`, manifest, ikoner og alle fire skrifter returnerer 200.
4. Send adressen til Jacob.

Ret ikke i spillets opførsel eller design uden at spørge Jacob først.

## Test på Android (Jacob, Chrome)

- [ ] Mikrofonen: Chrome spørger om adgang første gang man vælger en kategori
- [ ] Optag et navn, og hør at det spilles baglæns
- [ ] Sig den baglæns lyd, og hør at efterligningen spilles forlæns
- [ ] "Hør navnet" læser engelske navne højt med en acceptabel udtale (fx Hermione Granger, Minerva McGonagall)
- [ ] Knapperne føles som at trykke: de trykkes ned og bliver mørkere med det samme. Ingen vibration
- [ ] "Installer app" / "Føj til startskærm" giver eget ikon og åbner uden adresselinje
- [ ] Flytilstand: appen åbner stadig, når den er åbnet én gang med net
- [ ] Navnet under ikonet bliver ikke afkortet. Gør det, så ret `short_name` i manifestet (fx "Fis & ballade")

## Beslutninger der er truffet

- Kun engelske navne i version 1 (dansk oplæsning er usikker). 5 kategorier: Harry Potter, Film, Musik, Sport, TV og kendisser, plus Bland alle. 15 navne pr. kategori, skal udvides til ca. 30 efter test. Ingen politikere
- Målgruppen er kun voksne (18+). Udtrykket er et festspil, ikke en børneapp. Det gælder alle spil i appen
- Ingen vibration. Feedback ved tryk er visuel: knappen skubbes ned og mørkner inden 0,1 sekund
- Ingen point, konti, historik, deling eller reklamer i version 1

## Design

- Idé: kassettebånd og "spol tilbage". Navnet vises spejlvendt på baglæns-skærmen, og lydbølgen løber i lydens retning
- Farver: Nat `#1A1D4A`, Nat lys `#262A5E`, Etiket `#F3EEDC`, Tåge `#AEB0D6`, Kassettegul `#F5C518`, REC `#E8413C`
- REC-rød har kun 4,0:1 kontrast og må kun bruges til stor, fed tekst og knapper. Al anden tekst skal have mindst 4,5:1 (WCAG AA)
- Knapper mindst 48 px høje. Primærknappen er 72 px og sidder i nederste tredjedel
- Navne: Big Shoulders Display. Al anden tekst: Atkinson Hyperlegible

## Kendte begrænsninger og åbne punkter

- Testet i simuleret browser, men ikke på rigtig telefon. Lydkvalitet og mikrofon er endnu ikke afprøvet
- iPhone er ikke testet. Safari optager i et andet format (mp4), og lyden kan være slukket af ringetonekontakten
- Spillet kan kun optage 0,5–6 sekunder pr. optagelse
- Webadresse er ikke valgt
- Kommende spil skal lægges som selvstændige moduler, så Rewind ikke skal røres
