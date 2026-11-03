# Stijlgids Cursus DDO 5 (Ximera)

Dit document vat alles samen wat is afgesproken over de structuur, lay-out en syntax
van de Ximera-cursus fysica (Cursus DDO 5). Het staat in de git-repo (`Fysica/`)
en is de **enige bron van waarheid** voor de afspraken: Claude leest het rechtstreeks
uit de gekoppelde map. Nieuwe afspraken worden hier toegevoegd (en gecommit), niet
enkel in het geheugen van een chat.

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

### Twee tracks: volledig en 1 uur

- Naast de volledige cursus (`Cursus_DDO_5.tex`) bestaat een lichtere variant
  (`Cursus_5de_1uur.tex`) voor de 1-uursklassen, met bestanden met suffix `_1` / `_1uur`.
- Uitgecommentarieerde stukken in die bestanden zijn **bewuste leerplanreducties**, geen fouten.
- Elk nieuw hoofdstuk krijgt een expliciete **`_1uur`-analyse**: per bestand
  hergebruiken, inkorten of weglaten.

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
- Bij een meerdelige oefening blijft de vraagtekst zelf kort; procedurele instructies
  zoals *"maak eerst een tekening van ..."* horen in een `\hint`, niet in de hoofdvraag.

### Eenheden in opgaven en oplossingen
- De opgave mag "vriendelijke" eenheden met voorvoegsel gebruiken (`$+1{,}5\,\mathrm{\mu C}$`,
  `$3{,}0\,\mathrm{dm}$`); in het `\underline{Gegevens:}`-blok wordt omgezet naar SI (C, m).
- **Varieer de voorvoegsels** over opeenvolgende oefeningen (mC, µC, nC, cm, dm, ...),
  niet steeds dezelfde eenheid of notatie.
- Altijd `\,` vóór `\mathrm`, ook bij voorvoegsels: `4{,}0\,\mathrm{dm}`, niet `4{,}0\mathrm{dm}`.
- Eenheden **in elke tussenstap** meenemen, niet enkel bij het eindantwoord:
  `\sqrt{(0{,}899\,\mathrm{N})^2 + (0{,}899\,\mathrm{N})^2}`.

### Afronding, antwoordvelden en tolerantie
- Antwoorden altijd op het **juiste aantal beduidende cijfers** (afgeleid uit de gegevens), ook in het antwoordveld: `3{,}3 \, \mathrm{m/s^2}`, niet `3{,}27 \, \mathrm{m/s^2}`. In de `\answer{}` schrijf je de decimale punt (`3.3`).
- De **tolerantie** van een `\answer` kies je zo dat zowel het correct afgeronde antwoord als het niet-afgeronde tussenresultaat worden aanvaard, zodat leerlingen die (niet) afronden toch een juist antwoord krijgen. Voor een antwoord `3.3` is dat `tolerance=0.05`.

### Eindantwoorden in oplossingen
- Elk eindantwoord in een oplossing staat in een `\boxed{}`.
- Eindantwoorden zijn in **standaardvorm**: juist aantal beduidende cijfers, wetenschappelijke schrijfwijze (`\cdot 10^{n}`) en S.I.-eenheden, bv. `\boxed{3{,}5\cdot 10^{1} \, \mathrm{N}}`. Enkel waar we bewust van S.I. afwijken, wijken we ook hier af.
- In het antwoordveld van de digitale check (`\answer{}`) staat het antwoord **niet** in wetenschappelijke notatie, maar als gewone decimale waarde met het juiste aantal beduidende cijfers, bv. `\answer{35}` voor `3{,}5\cdot 10^{1}`.
- Dit geldt voor alle documenten (oefeningen, theorie, samenvattingen).

### Stelsels van vergelijkingen oplossen
- Oplossingen lossen een stelsel op via **substitutie**, niet door vergelijkingen op te tellen. Leerlingen gebruiken vooral substitutie, dus die aanpak volgen we ook in de uitwerkingen.

### Leesbaarheid van uitwerkingen
- Schrijf voor leerlingen: korte zinnen, een consistente stijl binnen één uitwerking (onpersoonlijk, gebiedende wijs of "we", niet door elkaar) en de naam van de methode waar je ze gebruikt (bv. substitutie).
- Zet voor elke stap in een uitwerking kort de reden: waarom gebruik je deze vergelijking of wet?
- Controleer elke tekst op spelling en taal, en laat geen symbolen zonder uitleg staan.

### Notatie (mechanica)
| Grootheid | Notatie | Vector |
|---|---|---|
| Dynamische / statische wrijving | `F_{w,d}`, `F_{w,s}` (evt. `F_{w,d,A}`, `F_{w,s,\max}`) — nooit `f` | `\vec{\mathbf{F}}_{w,d}` |
| Normaalkracht | `F_N` — nooit `N` | `\vec{\mathbf{F}}_{N}` |
| Trek-/spankracht | `F_t` — nooit `T` | `\vec{\mathbf{F}}_{t}` |

### Typografie en commentaar
- In lopende tekst **geen em-dash (—) en geen curly quotes** ("" ''); enkel gewone
  koppeltekens/apostrofs of LaTeX-constructies. (In decoratieve `%———`-scheidingslijnen
  tussen oefeningen mag het wel.)
- Datumcommentaar numeriek: `%verbeterd 9/9/26` of `%nagekeken 9/9/26`, geen voluit
  geschreven maandnamen.

### Kruisverwijzingen en voettekst
- Belangrijke `\section`-koppen krijgen een label, bv.
  `\section{Tribo-elektrisch effect}\label{sec:tribo-elektrisch-effect}`, zodat de
  hoofdstuk-inleiding ernaar kan verwijzen met `\ref{}`.
- Een stuk zonder eigen `\section` erft de voettekst van de vorige sectie: elk logisch
  inhoudsblok heeft dus een eigen `\section` nodig om de voettekst correct te resetten.

---

## 4. Afbeeldingen

- Pad per hoofdstuk: `pic5/elektriciteit/<onderwerp>/` (bv. `pic5/elektriciteit/veld/`).
- **Nooit** figuren uit Interactie of Serway scannen/overnemen (auteursrecht).
- Voorkeur: **originele TikZ-tekeningen**, rechtstreeks in de `.tex`-bestanden,
  met de stijlen en macro's uit `xmPreamble.tex` (`\poslading`/`\neglading`,
  `\drawvector`, `\addvectors`, `kracht`/`krachtcomponent`/`resulterendekracht`,
  `Evector`/`Evectorcomponent`/`Eveldlijn`, `Mvector`/`Mvectorcomponent`/`Mveldlijn`, ...).
  Dit vermijdt zowel auteursrechtproblemen als het beheer van losse beeldbestanden.
- Nooit lokale `\tikzset{charge+/...}`, `force/...`-definities in losse figuren:
  altijd de gedeelde preamble-stijlen gebruiken.

### TikZ-regels
- Ladingen eerst plaatsen (`\poslading`/`\neglading`), pas daarna `\drawvector` of
  `\draw[kracht]` die eraan verankeren (de macro's maken de node aan).
- `\drawvector`: positieve lengte = naar het doel (aantrekking), negatieve lengte =
  ervan weg (afstoting). Vaste hoek via een hulppunt, bv. `(q1)+(60:1)`. Startanker mag
  een randpunt zijn (`Q1.west`).
- `\addvectors` gebruikt de **eindpunten** van de getekende vectoren, niet hun startlabels.
- Schaalconventie: coördinaten = **10× de echte afstand in meter**, zodat de
  ladingcirkels proportioneel kloppen.
- Bij `scale=X` (X ≠ 1) altijd `transform shape` toevoegen.
- Labels naast een lading (Q1, Q2, ...) op **2,5 mm / 6 pt** afstand, bv.
  `\tkzLabelPoint[below left=2.5mm](A){$Q_{1}$}`.

### Krachtendiagrammen in oplossingen
- Lichamen als **puntmassa** (een punt) met label ernaast (bv. $m_1$), zodat vectoren
  niet achter blokken verdwijnen.
- Krachten ontbinden in componenten waar dat helpt (bv. helling).
- **Assen** (positie-assen `x`/`y`) zijn lang genoeg om niet op een korte vector te lijken, en worden **lichter gedrukt** (`draw=black!50, text=black!50`) zodat ze niet concurreren met de krachtvectoren. Dit geldt voor elke as, ook als er maar één as getekend is.
- **Genummerde vergelijkingen** in een oplossing krijgen een label via `\tag{blok 1}` (of `\tag{...}` naar keuze) binnen de `align*`-omgeving, zodat ernaar verwezen kan worden in de uitwerking.
- Gekozen assen (x/y met positieve zin) naast de tekening, met de vermelding
  *"Schets (niet op schaal)"*.
- Geen vectoren die enkel uit een pijlpunt bestaan: liever niet op schaal, met een
  leesbare minimumlengte.

### Oefeningen op basis van veldlijnfiguren
- **Rekenoefeningen** op een veldlijnentekening: enkel met een **homogeen veld**.
- Zuiver **conceptuele** vragen (redeneren, geen rekenwerk) mogen ook andere
  veldlijnbeelden gebruiken (puntlading, dipool).

### Uitzondering
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
- Ook de potentiaal van een puntlading ($V = kQ/r$) is **"Extra"** (verdieping),
  duidelijk zo gelabeld.
- Altijd eerst het leerplan checken vóór er inhoud wordt toegevoegd.
- Bronmateriaal (scans Interactie, Serway, leerplan) staat in een aparte map
  **naast** de repo (`~/Ximera/Bronnen/`, per hoofdstuk), **nooit in de repo**
  (auteursrecht: die gaat naar GitHub).

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
5. Testcompilaties (TikZ-controles) gebeuren in een aparte scratchmap, niet in de
   cursusmap. De echte PDF/HTML-builds gebeuren via de VS Code-taken (PDF/HTML/Bake).
6. Claude bewerkt de `.tex`-bestanden rechtstreeks in de map; Daan bekijkt de
   wijzigingen als diff in VS Code (Source Control) en commit zelf.
   **Commit vóór een sessie**, zodat de diff nadien enkel Claudes wijzigingen toont.
7. **Stand van zaken bijhouden**: telkens een hoofdstuk (of een `_1uur`-versie) geschreven,
   aangepast of nagekeken is, meteen bijwerken:
   - `5de/inleiding_stand_51.tex` (1 uur) en/of `5de/inleiding_stand_52.tex` (2 uur),
     voor de leerlingen (+ datumcommentaar aanpassen);
   - de TODO en de tabel "Stand van zaken" in `README.md`.

---

## 7. Tips om tokens te besparen

- **Eén chat per hoofdstuk of per bestand(groep)**, niet één lange doorlopende chat.
  Noem in de chat welke bestanden en welk bronhoofdstuk relevant zijn; Claude leest
  dan enkel die uit de map.
- **Tekst/oefeningen** en **TikZ-figuren** in aparte chats: figuren vragen veel
  compileer-heen-en-weer.
- **Feedback bundelen** in één bericht in plaats van per bestand een correctierondje.
- **Atomaire taken**: één of enkele bestanden per keer, niet "maak het hele hoofdstuk".
- **Nieuwe afspraken in dit bestand vastleggen** (vraag: *"zet dit in de stijlgids"*).
  Het geheugen is een hulpmiddel; deze stijlgids in de repo is de robuuste referentie.
