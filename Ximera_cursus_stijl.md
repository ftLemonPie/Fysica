# Stijlgids Cursus DDO 5 (Ximera)

Dit document vat alles samen wat is afgesproken over de structuur, lay-out en syntax
van de Ximera-cursus fysica (Cursus DDO 5). Het staat in de git-repo (`Fysica/`)
en is de **enige bron van waarheid** voor de afspraken: Claude leest het rechtstreeks
uit de gekoppelde map. Nieuwe afspraken worden hier toegevoegd (en gecommit), niet
enkel in het geheugen van een chat.

---

## 0. Visie en vaste hoofdstukopbouw

**Doel.** Alle hoofdstukken van Cursus DDO 5 hebben dezelfde opbouw. De structuur is geïnspireerd op Serway (*Physics for Scientists and Engineers*): een inleiding, genummerde figuren, theorie met duidelijke begrippen, conceptvragen en voorbeelden, een samenvatting en oefeningen. De inhoud volgt het leerplan NatS (LPD). We gaan zo diep en ver mogelijk binnen het leerplan. Alles wat verder gaat dan het leerplan krijgt het label **Extra** en staat in een uitklapbare omgeving.

**Bronnen.** Interactie bepaalt het niveau en de inhoud. Serway levert de structuur en de meerwaarde. Serway-tekst wordt nooit overgenomen: we herschrijven alles naar eigen voorbeelden op middelbaar niveau.

### Vaste opbouw per hoofdstuk
1. **Inleiding** (`_inleiding.tex`): een korte probleemstelling of onderzoeksvraag, en de lijst **"Wat je na dit hoofdstuk moet kennen en kunnen"**, afgeleid uit het leerplan.
2. **Per theoriesectie:**
   - een genummerde figuur met bijschrift (`\label{fig:...}`), waar de tekst naar verwijst;
   - korte theorie, met begrippen in een `definition`, eigenschappen in een `proposition` en wetten en formules in een `proposition`;
   - aan het eind van de sectie minstens één korte **conceptvraag** (`question` met één juist antwoord) die de kern van de sectie toetst.
3. **Voorbeelden**: altijd het stramien Gegevens, Gevraagd, Oplossing. Optioneel een `remark` met titel "Denkstap": een conceptuele aanpak zonder formule, zoals het stramien van Serway (begrijpen, aanpak kiezen, uitwerken, controleren).
4. **Extra's**: alles buiten het leerplan krijgt "Extra:" in de titel en een `expandable=true`-omgeving. Voorbeeld: `\begin{remark}[expandable=true,title={Extra: potentiaal van een puntlading}]`.
5. **Samenvatting** (`_samenvatting.tex`): blokken met `\samenbox` voor de definities, de wetten en formules (met verwijzing naar de vergelijkingen via `\ref`) en de concepten.
6. **Oefeningen** (`_oefeningen`): reeks 1 (basis) en reeks 2 (moeilijker), van makkelijk naar moeilijk, met de bijbehorende `_1uur`-analyse.

### Kwaliteitscheck per hoofdstuk
- Elk LPD-doel van het hoofdstuk is aantoonbaar behandeld. Noteer per doel in welke sectie het staat.
- Elke sectie heeft een figuur (waar zinvol) en een conceptvraag.
- Geen em-dash, geen `\"`-accenten in titels, geen wiskunde in remarktitels.
- Alle `\ref`-verwijzingen werken (bij bouwen in VS Code controleren).

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
Bestanden van de **appendix** krijgen het voorvoegsel `appendix_`, zodat ze samen staan in de map: `appendix_<onderwerp>_<subonderdeel>.tex` (bv. `appendix_vectoren_som.tex`, `appendix_energie_arbeid.tex`). Verwijs ernaar met die volledige naam in `\verwijs`.
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
  - Magnetisme: `stroom` (stijl voor de stroomzin langs een draad), `\stroomuit{naam}{coord}` / `\stroomin{naam}{coord}` (draad loodrecht op het blad, stroom uit/in het blad, als node), `\staafmagneet[lengte]{naam}{midden}{hoek}` (N rood, Z grijs; maakt de punten `naam`, `naam-N`, `naam-Z`) en `\kompasnaald[lengte]{midden}{hoek}` (rode punt = N). `Mveldlijn` heeft geen `fill`, zodat ook kromme veldlijnen (`plot[smooth]`) niet worden opgevuld.
  - Veldlijnen met de gecentreerde pijl (`Eveldlijn`, `Mveldlijn`) geven bij sommige `scale`-waarden een *Dimension too large*-fout: teken zulke figuren liever op ware grootte (zonder `scale`). Exacte veldlijnpatronen (staafmagneet, spoel, ...) worden in Python berekend en als `plot[smooth] coordinates {...}` in de figuur gezet.
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
- Eigenschappen (bv. "loodrecht op de equipotentiaaloppervlakken") staan in een `proposition`, niet in een `remark`.
- Stellingen en wetten gebruik je als `proposition`, niet als `theorem`.
- Nergens een em-dash (—) in lopende tekst, ook niet in `remark`- of `example`-omgevingen. Gebruik een komma, dubbele punt of haakjes.
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

### Keuzevragen: welke omgeving?
- **Alle juiste antwoorden moeten aangeduid worden**: `selectAll` (dit is meestal het geval). Enkel correct als alle correcte antwoorden zijn aangeduid.
- **1 juist antwoord is genoeg** (ook bij meerdere `[correct]`-opties): `wordChoice` of `multipleChoice`. Beide werken hetzelfde qua nakijken; de keuze hangt van de lay-out af.
  - `wordChoice`: dropdown-menu, inline in een zin.
  - `multipleChoice`: alle opties onder elkaar, als apart antwoord.

### Hints: filosofie
- Een hint is een duw in de rug voor een **tussenstap** in een **lastig, meerstappen-probleem**,
  voor wie vastzit — **geen** rechtstreekse vermelding van de te gebruiken formule
  (dus niet: *"Gebruik $F=QE$."*).
- **Eenvoudige, éántraps-oefeningen hebben vaak helemaal geen hint nodig.**
- Bij hints wél toegestaan/gewenst: een conceptuele vraag die het denkproces op gang
  brengt (*"Wat gebeurt er met de richting van de kracht als je het teken van de lading omdraait?"*),
  of een aanwijzing over **welke tussenstap** nog ontbreekt (*"Je hebt nog $r_{23}$ nodig. Hoe vind je die in deze driehoek?"*).
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
- De **tolerantie** van een `\answer` is **2,5 % van het antwoord** (afgerond op een beduidend cijfer), zodat ook wie met afgeronde tussenwaarden werkt en dezelfde juiste methode gebruikt, het juiste antwoord krijgt. Voorbeeld: `tolerance=0.08` bij `3.3`.

### Eindantwoorden in oplossingen
- Elk eindantwoord in een oplossing staat in een `\boxed{}`.
- Eindantwoorden zijn in **standaardvorm**: juist aantal beduidende cijfers, wetenschappelijke schrijfwijze (`\cdot 10^{n}`) en S.I.-eenheden, bv. `\boxed{3{,}5\cdot 10^{1} \, \mathrm{N}}`. Enkel waar we bewust van S.I. afwijken, wijken we ook hier af.
- In het antwoordveld van de digitale check (`\answer{}`) staat het antwoord **niet** in wetenschappelijke notatie, maar als gewone decimale waarde met het juiste aantal beduidende cijfers, bv. `\answer{35}` voor `3{,}5\cdot 10^{1}`.
- Dit geldt voor alle documenten (oefeningen, theorie, samenvattingen).
- Eindantwoorden in S.I.-eenheden: zet cm, g of andere afgeleide eenheden om naar m, kg, N, s (bv. `\boxed{1{,}5\cdot 10^{-1} \, \mathrm{m}}`, niet `15 cm`). Het antwoordveld krijgt dan `0.15` met eenheid m.

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
- Bijzinnen staan tussen **komma's**, niet tussen haakjes. Haakjes gebruik je enkel voor een korte verduidelijking, bv. `(RP)` of `(met behoud van teken)`.
- In lopende tekst **geen em-dash (—) en geen curly quotes** ("" ''); enkel gewone
  koppeltekens/apostrofs of LaTeX-constructies. (In decoratieve `%———`-scheidingslijnen
  tussen oefeningen mag het wel.)
- Datumcommentaar numeriek: `%verbeterd 9/9/26` of `%nagekeken 9/9/26`, geen voluit
  geschreven maandnamen.

### Kruisverwijzingen en voettekst
- **Verwijzingen naar een ander bestand** (een andere `\activity`) gebeuren met `\verwijs[tekst voor html]{label}{bestandsnaam zonder .tex}`, nooit met `\ref`/`\eqref`. Online wordt elke activity apart gecompileerd, waardoor `\ref` naar een label in een ander bestand `??` geeft. `\verwijs` geeft in de PDF een gewone `\ref` en online een link naar de pagina van het andere bestand. Voorbeeld: `zie~\verwijs[Permanente magneten]{sec:permanente-magneten}{magnetisme_permanente_magneten}`. Kies de tekst zo dat de zin online ook klopt (bv. `figuur~\verwijs[in Het magnetisch veld en veldlijnen]{fig:...}{magnetisme_veld}`).
- `\ref` blijft gewoon voor verwijzingen binnen hetzelfde bestand.
- Verwijzen naar een hoofdstuk dat nog niet bestaat: gewone tekst (bv. "in het hoofdstuk over deeltjesfysica"), geen label.
- Belangrijke `\section`-koppen krijgen een label, bv.
  `\section{Tribo-elektrisch effect}\label{sec:tribo-elektrisch-effect}`, zodat de
  hoofdstuk-inleiding ernaar kan verwijzen met `\ref{}`.
- Een stuk zonder eigen `\section` erft de voettekst van de vorige sectie: elk logisch
  inhoudsblok heeft dus een eigen `\section` nodig om de voettekst correct te resetten.

---

## 4. Afbeeldingen

- Pad per hoofdstuk: `pic5/elektriciteit/<onderwerp>/` (bv. `pic5/elektriciteit/veld/`).
- **Figuren uit de bronnen (Interactie, Serway) of van het internet** mogen gebruikt worden, mits de bron duidelijk vermeld staat in het bijschrift, bv. `\caption{... Bron: Interactie, T1 H3, p.~43.}`. Bij internetbeelden controleer je de licentie en vermeld je die ook.
- **Foto's van het internet**: enkel van Wikimedia Commons met een vrije licentie (CC BY, CC BY-SA, CC0 of publiek domein). Bestand in `xmPictures/pic5/<thema>/` met een Nederlandse naam; boven de figuur een commentaarregel `% bron: <url van de Commons-pagina>`; direct onder `\includegraphics` de macro `\fotobron{<auteur>}{<licentie>}{<url>}` (niet in het bijschrift, dat blijft inhoudelijk); en een regel in `5de/bibliografie_52.tex`, sectie *Bronnen van afbeeldingen*. Sjabloon: README, template 5. Geen scans uit Interactie of Serway (publieke repo en website) en geen foto's waarop een bekende persoon herkenbaar is.
- **Voorkeur**: een eigen TikZ-herwerking van de figuur, met de stijlen uit de preamble. Dat is op het gebied van auteursrecht de veiligste optie.
- **Werkwijze bij een nieuwe foto**: de bestandsnaam staat in `pic5/<onderwerp>/` (zie §4). Boven de `\includegraphics` komt een commentaarregel met de bron-URL (`% bron: https://commons.wikimedia.org/wiki/File:...`). In het bijschrift staan de auteur en de licentie, bv. `Bron: Jan Ainali, Wikimedia Commons, CC BY 3.0.`
- Een bronvermelding maakt een figuur niet automatisch toegelaten voor publicatie. Bij twijfel over het gebruik van een figuur in de gepubliceerde cursus, overleg je eerst.
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
- **Aanvullend/inspiratie**: Serway, *Physics for Scientists and Engineers*, 7th ed.,
  voor niveau, "Quick Quiz"-stijl en extra oefeningen, maar dieper dan het leerplan vereist.
- Beide bronnen: **nooit letterlijk overnemen** (tekst of cijfer-configuraties). Figuren zie §4.
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
