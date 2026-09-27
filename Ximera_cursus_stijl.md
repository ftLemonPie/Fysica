```markdown
# Stijlgids Cursus DDO 5 (Ximera)

Dit document vat alles samen wat is afgesproken over de structuur, lay-out en syntax
van de Ximera-cursus fysica (Cursus DDO 5). Upload dit bestand (samen met
`xmPreamble.tex` en één volledig hoofdstuk als voorbeeld) als **project-kennis**
in een Claude Project, zodat nieuwe chats deze context automatisch hebben zonder
dat je alles opnieuw moet uitleggen of opnieuw tokens moet verbruiken aan uitleg.

---

## 1. Architectuur

- **`Cursus_DDO_5.tex`** (`\documentclass[nonewpage]{xourse}`) is het hoofdbestand.
  Het bevat zelf geen inhoud, maar rijgt alle losse ximera-bestanden aaneen via
  `\activity{bestand.tex}`.
- **Elk los bestand** (inleiding, theorie, samenvatting, oefeningen) is een apart
  bestand met `\documentclass{ximera}`.
- Structuur binnen een `\part{...}` (= één hoofdstuk):
  1. `\chapterstyle` + `\activity{..._inleiding.tex}` — theorie-inleiding, telt als hoofdstuk.
  2. `\sectionstyle` + een reeks `\activity{...}` — losse leerstof-onderdelen (geen chapterbreak).
     Lange onderwerpen worden bewust in **2 aparte bestanden** gesplitst voor modulariteit.
  3. Nog steeds `\sectionstyle` — een `..._samenvatting.tex`.
  4. `\chapterstyle` + `\activity{..._oefeningen_inleiding.tex}` — inleiding op de oefeningen.
  5. `\sectionstyle` + oefeningen-onderdelen, **opgesplitst per type/moeilijkheidsgraad**
     (bv. `vragen`, `basis`, `1lijn`, `driehoek`), telkens **van makkelijk naar moeilijk**.

### Bestandsnaamgeving

`<onderwerp>_<subonderdeel>.tex` voor theorie, `<onderwerp>oef_<type>.tex` voor
oefeningen (let op: **geen underscore** tussen onderwerp en `oef`).
Voorbeeld hoofdstuk "elektrisch veld":
```
elektrischveld_inleiding.tex
elektrischveld_puntlading.tex
elektrischveld_veldlijnen.tex
elektrischveld_materie_in_veld.tex
elektrischveld_samenvatting.tex
elektrischveldoef_inleiding.tex
elektrischveldoef_vragen.tex
elektrischveldoef_basis.tex
elektrischveldoef_1lijn.tex
elektrischveldoef_driehoek.tex
```

### `xmPreamble.tex`

Gedeelde preamble met o.a.:
- `siunitx` met Franse/Belgische locale (komma als decimaalteken)
- **TikZ-stijlen en macro's** (ladingen, vectoren, veldlijnen — zie ook §4):
  - Ladingen: `\poslading{naam}{coord}` / `\neglading{naam}{coord}` (definiëren meteen de node en tekenen de lading; optioneel ander label via `\poslading[label]{naam}{coord}`). Zijn de punten al gedefinieerd via `tkz-euclide` (`\tkzDefPoint`), gebruik dan rechtstreeks `\node[poslading] at (punt) {$+$};`.
  - Vectoren: `\drawvector[stijl]{startlabel}{doellabel}{lengte in cm}{label}` (standaardstijl `vector`) tekent een vector met een **eigen, vaste lengte** in de richting van het doelpunt. Optelling (parallellogrammethode, met stippellijn-hulplijnen): `\addvectors[stijl]{oorsprong}{eindpunt1}{eindpunt2}{label}`.
  - Stijlnaamgeving per grootheid: de volle-kleur-stijl heet naar de grootheid zelf (`positie`, `snelheid`, `kracht`, `versnelling`, `Evector`, `Mvector`), de bijhorende `...component`-variant heeft een lichtere vulling/tekstopacity voor deelvectoren (`snelheidcomponent`, `krachtcomponent`, `versnellingcomponent`, `Evectorcomponent`, `Mvectorcomponent`). Een resultante die zich moet onderscheiden van haar componenten krijgt de stijl `resulterendekracht` (zelfde kleurfamilie, iets donkerder/dikker) i.p.v. een willekeurige andere kleur.
  - Veldlijnen: `Eveldlijn` / `Mveldlijn` — via `decorations.markings` staat de pijl in het **midden** van de lijn, niet op het uiteinde.
  - `\R` is niet langer nodig om ladingcirkels te tekenen (dat zit vast in de `poslading`/`neglading`-stijl, `minimum size=6mm`), maar kan nog gebruikt worden voor verticale label-offsets boven een lading.
  - Bij een `tikzpicture[scale=X]` met X ≠ 1: voeg `transform shape` toe aan de opties, anders schalen de ladingsnodes niet mee met de rest van de figuur.
- `\samenbox{titel}{tekst}`, `\nl`, `\mylink`
- `tkz-euclide` voor driehoeken/hoeken (`\tkzDefPoint`, `\tkzDrawPolygon`, `\tkzFillAngle`, ...)

---

## 2. Documenttypes: verplichte structuur per type

### a) Hoofdstuk-inleiding (`_inleiding.tex`, chapterstyle)
```latex
\documentclass{ximera}
\title{...}
\author{Daan Lipkens}
\begin{document}
\begin{abstract} ... \end{abstract}
\maketitle
\label{hoofdstuk:...}
\section*{Inleiding}   % ONGENUMMERD
... lopende tekst, preview van het hoofdstuk ...
\end{document}
```

### b) Theorie-onderdeel (`_onderwerp.tex`, sectionstyle)
- `\section{}` / `\subsection{}` voor structuur.
- `definition` / `theorem` / `proposition` / `remark` met `[foldable=true,title={...}]`
  of `[expandable=true]` — **altijd voluit `=true`, nooit de kale vlag**.
- `\nl` direct na de opening van zo'n omgeving (nodig voor correcte newline).
- `example[foldable=true,title={...}]` voor uitgewerkte voorbeelden/toepassingen.
- Quisvragen: `\begin{question}` **rechtstreeks** in de tekst (zie §3, geen `onlineOnly`).

### c) Samenvatting (`_samenvatting.tex`)
```latex
\begin{abstract} ... \end{abstract}

\begin{onlineOnly}%voor bladindeling
    \maketitle
\end{onlineOnly}

\newgeometry{left=3cm,bottom=0.1cm}
\pagestyle{empty}

\begin{conclusion}[title={Samenvatting}]\nl

\samenbox{Titel blok 1}{ ... }
\samenbox{Titel blok 2}{ ... }

\end{conclusion}

\restoregeometry
\pagestyle{plain}
```
**Let op:** `\maketitle` staat in `onlineOnly` (i.v.m. bladindeling bij afdrukken),
`\nl` na `\begin{conclusion}[...]`, en de marge is `left=3cm,bottom=0.1cm`
(**niet** een symmetrische `margin=...`).

### d) Oefeningen-inleiding (`oef_inleiding.tex`, chapterstyle)
Kort: titel, abstract, `\maketitle`, één inleidende zin over wat volgt. Geen `\section*{Inleiding}` nodig hier (dit is puur een korte aankondiging, geen theorie).

### e) Oefeningen-onderdelen (`oef_<type>.tex`, sectionstyle)
- Enkelvoudige oefening → alles in `\begin{exercise}...\end{exercise}`.
- Meerdelige oefening → gedeelde context/gegevens bovenaan in `exercise`,
  elke deelvraag in een eigen `\begin{question}...\end{question}` met eigen
  hint(s), antwoordveld en `solution`.
- Oplossingen volgen het vaste stramien: `\underline{Gegevens:}` (align-blok),
  `\underline{Gevraagd:}`, `\underline{Oplossing:}` met `align*`-berekening.
- **Oefeningen binnen één bestand staan van makkelijk naar moeilijk.**

---

## 3. Syntax-regels (harde eisen)

| Regel | Voorbeeld |
|---|---|
| Eenheden altijd romein, met dunne spatie | `4{,}0 \cdot 10^{6} \, \mathrm{N/C}` |
| Decimalen met komma in wiskundemodus | `2{,}0 \cdot 10^{-6}` |
| `foldable=true` / `expandable=true` voluit | nooit kale `[foldable]` |
| `\section*{Inleiding}` ongenummerd | enkel in hoofdstuk-inleidingen |
| **`onlineOnly` NOOIT rond quizinhoud** | geen `multipleChoice`/`wordChoice`/`hint`/`solution` in `onlineOnly` — dat moet zowel online als in de PDF zichtbaar zijn |
| `onlineOnly` wél voor: | video's, en `\maketitle` in samenvattingen (bladindeling) |
| Meerdelige oefening | gedeelde gegevens in `exercise`, elke deelvraag een eigen `question` |

### Hints: filosofie
- Een hint is een duw in de rug voor een **tussenstap** in een **lastig, meerstappen-probleem**,
  voor wie vastzit — **geen** rechtstreekse vermelding van de te gebruiken formule
  (dus niet: *"Gebruik $F=QE$."*).
- **Eenvoudige, éántraps-oefeningen hebben vaak helemaal geen hint nodig.**
- Bij hints wél toegestaan/gewenst: een conceptuele vraag die het denkproces op gang
  brengt (*"Wat gebeurt er met de richting van de kracht als je het teken van de lading omdraait?"*),
  of een aanwijzing over **welke tussenstap** nog ontbreekt (*"Je hebt nog $r_{23}$ nodig — hoe vind je die in deze driehoek?"*).

---

## 4. Afbeeldingen

- Pad per hoofdstuk: `pic5/elektriciteit/<onderwerp>/` (bv. `pic5/elektriciteit/veld/`).
- **Nooit** figuren uit Interactie of Serway scannen/overnemen (auteursrecht).
- Voorkeur: **originele TikZ-tekeningen**, rechtstreeks in de `.tex`-bestanden,
  met de stijlen en macro's uit `xmPreamble.tex` (`\poslading`/`\neglading`,
  `\drawvector`, `\addvectors`, `kracht`/`krachtcomponent`/`resulterendekracht`,
  `Evector`/`Evectorcomponent`/`Eveldlijn`, `Mvector`/`Mvectorcomponent`/`Mveldlijn`, ...).
  Dit vermijdt zowel auteursrechtproblemen als het beheer van losse beeldbestanden.
- Enkel wanneer een tekening echt te complex is voor TikZ, een `\includegraphics`
  placeholder met een `% TIP:`-commentaar naar een vergelijkbare (niet over te nemen) bronfiguur.

---

## 5. Bronnenbeleid

- **Hoofdbron**: *Interactie* (oud handboek, niet meer verkocht) — leidt de opbouw en
  voorbeeldtypes van elk hoofdstuk.
- **Aanvullend/inspiratie**: Serway, *Physics for Scientists and Engineers*, 7th ed. —
  voor niveau, "Quick Quiz"-stijl en extra oefeningen, maar dieper dan het leerplan vereist.
- Beide bronnen: **nooit letterlijk overnemen** (tekst, cijfers-configuraties of figuren).
  Altijd herschrijven/herwerken naar eigen voorbeelden op middelbare-schoolniveau.
- **Leerplanbeperking** (NatS, oktober 2024, LPD 2/3 F): elektrische krachtwerking en
  elektrisch veld blijven beperkt tot ladingen **in lijn** of **onder een rechte hoek
  (stelling van Pythagoras)**. Willekeurige (scalene) driehoeken met cosinusregel op
  een niet-rechte hoek horen niet tot de basisleerstof — enkel gelijkzijdige driehoek/vierkant
  als verdieping voor sterkere leerlingen, duidelijk gelabeld als extra.

---

## 6. Werkwijze die goed werkt

1. Eerst **bestaande bestanden nalezen en herschrijven** naar de conventies hierboven,
   pas daarna **nieuwe bestanden** toevoegen.
2. **Alle numerieke antwoorden vooraf verifiëren** (bv. met Python) vóór ze in een
   `.tex`-bestand komen.
3. Nieuwe TikZ-figuren **compileren en visueel controleren** (pdflatex + pdftoppm)
   vóór ze in het definitieve bestand komen.
4. Oefeningen binnen eenzelfde bestand **aantoonbaar oplopend** in moeilijkheidsgraad;
   bij twijfel een korte rationale geven voor de volgorde.

---

## 7. Tips om deze chat op te splitsen (tokens besparen)

**Kernprobleem:** één lange doorlopende chat herhaalt impliciet alle eerdere context
(bestandsinhoud, afspraken, gecompileerde figuren, ...) bij elk nieuw bericht, wat duur
en traag wordt.

### a) Gebruik een Claude Project
- Maak één **Project** aan voor deze cursus (bv. "Cursus DDO 5 – Fysica").
- Upload in de **project-kennis** (niet in een losse chat): dit stijldocument,
  `xmPreamble.tex`, en 1 volledig uitgewerkt hoofdstuk als referentievoorbeeld.
- Elke **nieuwe chat binnen dat Project** leest deze kennis automatisch in — je hoeft
  niet opnieuw uit te leggen hoe `\samenbox` werkt of dat `onlineOnly` niet rond
  quizvragen mag staan.
- Voeg eventueel **custom instructions** toe op projectniveau (bv. "Volg altijd
  Ximera_stijlgids_Cursus_DDO5.md strikt; verifieer rekenwerk in Python; schrijf oefeningen
  van makkelijk naar moeilijk").

### b) Splits per hoofdstuk, niet per cursus
- Start een **nieuwe chat per hoofdstuk** (of zelfs per documenttype: theorie vs.
  oefeningen vs. figuren), en upload enkel de bestanden die voor dát hoofdstuk relevant zijn
  — niet de volledige cursus of alle bronbestanden opnieuw.

### c) Splits type werk
- **Tekst/oefeningen schrijven** en **TikZ-figuren tekenen** vergen een ander soort
  iteratie (figuren hebben veel compileer-heen-en-weer nodig). Aparte chats hiervoor
  houden beide sneller en goedkoper.

### d) Geef feedback gebundeld
- Verzamel feedback over meerdere bestanden en geef die in **één bericht**, in plaats
  van per bestand een apart correctierondje te starten. Dat scheelt een volledige
  "herlees-en-antwoord"-cyclus per opmerking.

### e) Laat afspraken expliciet vastleggen
- Zinnen als *"onthoud dat..."* of *"doe dit voortaan zo..."* zorgen ervoor dat de
  afspraak in het geheugensysteem terechtkomt en in toekomstige chats **binnen
  hetzelfde Project** automatisch wordt toegepast, zonder dat je het opnieuw moet
  uitleggen. Herhaal dit wel expliciet bij belangrijke stijlregels — vertrouw niet
  blind op automatische onthouding voor kritieke afspraken; controleer ze af en toe
  door te vragen "wat onthoud je over de stijl van samenvattingen?".
- Dit stijldocument is de **robuustere back-up**: geheugen kan verouderen of gemist
  worden, een geüpload referentiebestand niet.

### f) Houd bestanden atomair
- Vraag per chat om **één of enkele bestanden** tegelijk, niet "maak het hele hoofdstuk".
  Kleinere, concrete taken zijn makkelijker te controleren en goedkoper te herdoen
  als er iets moet worden aangepast.
```