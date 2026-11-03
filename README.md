# Veel voorkomende errors
- na herstart: in terminal: "podman machine start" dan op extra klikken voor start server
- in ximera.4ht staat html code, in ximera.cls regels rond pdf

# Stijlafspraken
Alle afspraken over structuur, syntax, hints, eenheden, notatie, TikZ en werkwijze staan in
**[`Ximera_cursus_stijl.md`](Ximera_cursus_stijl.md)**. Dat is de enige bron van waarheid:
nieuwe afspraken komen daar, niet hier. De templates hieronder volgen die stijlgids.

Kort de belangrijkste:
- Eenheden romein met dunne spatie (`4{,}0\,\mathrm{N/C}`), decimale komma `2{,}0`.
- `foldable=true` / `expandable=true` voluit; `\nl` na de opening van theorieblokken.
- Nooit `onlineOnly` rond quizinhoud (multipleChoice, wordChoice, hint, solution).
- Hints: duw voor een tussenstap bij een meerstappenprobleem, nooit de formule verklappen.
- Geen em-dash of curly quotes in lopende tekst.
- Datumcommentaar bovenaan: `%verbeterd D/M/JJ` of `%nagekeken D/M/JJ`.
- Oefeningen in een bestand van makkelijk naar moeilijk.

# Templates
Hier is je "Ximera Fysica Toolkit". Je kan deze blokken code gewoon kopiëren, plakken en invullen!

### 1. Vraagstuk met numeriek antwoord en stappenplan

Dit is de gouden standaard voor je oefeningen. Het bevat een invulvak voor wetenschappelijke notatie, hints en de gestructureerde oplossing (Gegevens, Gevraagd, Oplossing).

-->latex
%———————————————————————————————————————
% OEFENING: [Korte beschrijving voor jezelf]
\begin{exercise}
    [Typ hier de opgave van het vraagstuk. Gebruik de juiste eenheden en wiskundige notatie, bv. $Q_1 = +2{,}0 \cdot 10^{-6} \, \mathrm{C}$.]
    
    % Invulvak (pas de tolerance aan indien nodig)
    \[ F_{\text{res}} = \answer[tolerance=0.05,onlineshowanswerbutton]{1.23} \cdot 10^{\answer{-4}} \, \mathrm{N} \]
    
    % Optioneel: Inline keuzemenu
    De kracht wijst naar: \wordChoice{
        \choice{links}
        \choice[correct]{rechts}
    }

    % Hints: enkel bij meerstappenproblemen, een duw voor een tussenstap
    % (nooit de formule verklappen; eenstapsoefeningen hebben vaak geen hint nodig)
    \begin{hint}
        [Welke tussenstap ontbreekt nog? bv. "Je hebt nog $r_{23}$ nodig: hoe vind je die?"]
    \end{hint}

    % Oplossing
    \begin{solution}\nl
        \underline{Gegevens:} % omgezet naar SI-eenheden
        \begin{align*}
            & [Symbool] = [Waarde] \, \mathrm{[Eenheid]} & & [Symbool] = [Waarde] \, \mathrm{[Eenheid]}\\
            & [Symbool] = [Waarde] \, \mathrm{[Eenheid]} & & 
        \end{align*}

        \underline{Gevraagd:} $[Symbool]$ \\

        \underline{Oplossing:}\\
        [Typ hier de uitwerking; eenheden in elke tussenstap meenemen]
        \begin{align*}
            [Formule] &= [Invullen] \\
            &= [Uitkomst] \, \mathrm{[Eenheid]}
        \end{align*}
        
        Conclusie: [Schrijf hier een korte eindzin].
    \end{solution}
\end{exercise}
%———————————————————————————————————————



### 2. Conceptuele vraag (Meerkeuze)

Ideaal voor theorievragen of kleine quizjes tussendoor.

-->Latex
%———————————————————————————————————————
% VRAAG: [Korte beschrijving]
\begin{question}
    [Typ hier je vraag. Bijvoorbeeld: Wat gebeurt er als we de afstand verdubbelen?]
    
    \begin{multipleChoice}
        \choice{Dit is een fout antwoord.}
        \choice[correct]{Dit is het juiste antwoord.}
        \choice{Dit is nog een fout antwoord.}
    \end{multipleChoice}

    \begin{hint}
        Geef een tip over de theorie (bv. evenredigheden).
    \end{hint}

    \begin{solution}\nl
        [Geef hier de verklaring waarom het juiste antwoord klopt.]
    \end{solution}
\end{question}
%———————————————————————————————————————



### 3. Uitgewerkt Voorbeeld in de theorie

Voor theoriestukken waar je een toepassing of rekenvoorbeeld wilt meegeven dat leerlingen kunnen uitklappen.

-->latex
%------------------------------------------------
% VOORBEELD: [Titel]
\begin{example}[foldable=true,title={Voorbeeld: [Titel van het voorbeeld]}]\nl
    [Typ hier de inleiding of de opgave van het voorbeeld.]
    
    \begin{solution}\nl
        [Werk hier het voorbeeld stap voor stap uit. Je kan hier ook afbeeldingen of TikZ in plaatsen.]
    \end{solution}
\end{example}
%------------------------------------------------



### 4. Theorieblokken (Definities, Wetten, Opmerkingen)

Gebruik deze omgevingen om belangrijke theorie te accentueren. Ximera geeft ze automatisch een mooie opmaak in de online versie en in de PDF.

-->latex
% Definitie (met of zonder extra titel)
\begin{definition}[title={Optionele titel}]\nl
    [Typ hier de definitie. Zet sleutelwoorden in \textbf{vet}.]
\end{definition}

% Stelling of Wet
\begin{theorem}[title={Wet van [Naam]}]\nl
    [Typ hier de stelling of de wet.]
    \begin{equation}
        [Formule]
    \end{equation}
\end{theorem}

% Opmerking (met of zonder uitklap-optie)
\begin{remark}[expandable=true,title={Let op!}]\nl
    [Plaats hier een belangrijke tip, valkuil of extra context.]
\end{remark}



### 5. Afbeeldingen invoegen

Dit is de veiligste manier om afbeeldingen in te voegen, zodat ze zowel in de PDF als op de webpagina mooi in het midden staan en een bijschrift hebben.

-->latex
%---------------------------
% AFBEELDING: [Beschrijving]
\begin{figure}[ht!]
    \begin{center}
        \includegraphics[width=0.6\textwidth]{[Pad/naar/je/afbeelding.jpg]}
    \end{center}
    \caption{[Typ hier het bijschrift van de figuur.]}
    \label{fig:[korte_naam]}
\end{figure}
%---------------------------



### 6. Video's integreren

Omdat YouTube-video's online mooi kunnen afspelen, maar in een geprinte PDF gewoon verdwijnen, gebruiken we deze combinatie om beide weergaven perfect te maken.

-->latex
%---------------------------
% VIDEO: [Beschrijving]
\begin{onlineOnly}
    \youtube{[YouTube-ID, bv. dQw4w9WgXcQ]}
\end{onlineOnly}
\pdfOnly{
    \begin{center}
        \mylink{https://youtu.be/[YouTube-ID]}{Link naar de video over [onderwerp].}
    \end{center}
}
%---------------------------


# TODO
Na elke afgewerkte of nagekeken stap: deze TODO **en** de stand van zaken voor de leerlingen
bijwerken (`5de/inleiding_stand_51.tex` voor 1 uur, `5de/inleiding_stand_52.tex` voor 2 uur).

## Stand van zaken 5de jaar (3/11/26)
| Hoofdstuk | 2 uur (`Cursus_DDO_5.tex`) | 1 uur (`Cursus_5de_1uur.tex`) |
|---|---|---|
| H1 elektrische krachtwerking | geschreven, nagekeken | geschreven, nagekeken |
| H2 elektrisch veld | geschreven, nagekeken | geschreven, nagekeken |
| H3 potentiaal | geschreven, nog niet nagekeken | nog aan te passen en na te kijken |
| H4 gemengde schakelingen | n.v.t. | geschreven, nog niet nagekeken |
| Appendix vectorrekenen, standaardvorm | geschreven | geschreven |

## te doen volgende keer

- [x] style md aanpassen
- [ ] H3 potentiaal (2 uur): theorie en oefeningen nalezen, extra oefeningen maken
- [ ] H3 potentiaal (1 uur): aanpassen en nakijken (`_1uur`-analyse)
- [ ] H4 gemengde schakelingen (1 uur) nakijken
- [ ] extra quiskes in H2, extra oefeningen H1



## Errors
- [ ] \mylink: doet nog niet wat het zou moeten doen. QR met onderschrift in pdf en een klikbare hyperlink online. --> beter oplossing zoeken
    - [x] \mylink geeft in html geen klikbare link
    - [x] onderschrift QRcode lukt niet goed
    - [ ] verbeteren
    - [ ] zelfde met \youtube in pdf
- [ ] \choiceTrue enzo werkt niet: https://tex.stackexchange.com/questions/76416/how-to-type-multiple-choice-questions-with-more-than-one-correct-choice
- [ ] \SI{}{} werkt in pdf, maar in HTML heeft het x als vermenigvuldiging


## toekomst
- [ ] AI prompts voor oefenignen
- [ ] Herhalignsoefeningen per H en per deel
- [ ] oefeningen toelatingsproeven
- [ ] Appendix nummering herstarten romeins.
- [ ] verwijzingen nakijken.
- [ ] ref laat label zien in html
- [ ] download pdf zonder antwoorden --> ?
- [ ] beter manier afbeelding in title
- [ ] hoe afval bestandjes kuisen? (map op pc komt vol te zitten)
- [ ] logo aanpassen site
- [ ] kleuren voor vectoren vast leggen? of zo laten --> zo laten. Te veel werk, te veel kans om eens te vergissen en leerlingen moeten ook altijd 
vectoren benoemen.
- [ ] in hoe_fysica_te_studeren_5 en 6 staat nog een fact omgeving
- [ ] Appendix
    -[ ] nummering anders