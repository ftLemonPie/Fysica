{\rtf1\ansi\ansicpg1252\cocoartf2870
\cocoatextscaling0\cocoaplatform0{\fonttbl\f0\fnil\fcharset0 .AppleSystemUIFontMonospaced-Regular;}
{\colortbl;\red255\green255\blue255;\red108\green0\blue181;\red247\green248\blue245;\red11\green11\blue11;
\red118\green116\blue110;\red32\green36\blue45;\red91\green98\blue116;\red15\green112\blue1;}
{\*\expandedcolortbl;;\cssrgb\c50588\c0\c76078;\cssrgb\c97647\c97647\c96863;\cssrgb\c4314\c4314\c4314;
\cssrgb\c53725\c52941\c50588;\cssrgb\c16863\c18824\c23137;\cssrgb\c43137\c46275\c52941;\cssrgb\c0\c50196\c0;}
\paperw11900\paperh16840\margl1440\margr1440\vieww11520\viewh8400\viewkind0
\deftab720
\pard\pardeftab720\partightenfactor0

\f0\fs24 \cf2 \cb3 \expnd0\expndtw0\kerning0
\outl0\strokewidth0 \strokec2 #\cf4 \strokec4  \cf2 \strokec2 Stijlgids Cursus DDO 5 (Ximera)\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \cb3 \strokec4 \'a0\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \cb3 \strokec4 Dit document vat alles samen wat is afgesproken over de structuur, lay-out en syntax\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \cb3 \strokec4 van de Ximera-cursus fysica (Cursus DDO 5). Upload dit bestand (samen met\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \cb3 \strokec4 `xmPreamble.tex` en \'e9\'e9n volledig hoofdstuk als voorbeeld) als **project-kennis**\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \cb3 \strokec4 in een Claude Project, zodat nieuwe chats deze context automatisch hebben zonder\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \cb3 \strokec4 dat je alles opnieuw moet uitleggen of opnieuw tokens moet verbruiken aan uitleg.\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \cb3 \strokec4 \'a0\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf6 \cb3 \strokec6 ---\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \cb3 \strokec4 \'a0\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf2 \cb3 \strokec2 ##\cf4 \strokec4  \cf2 \strokec2 1. Architectuur\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \cb3 \strokec4 \'a0\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf6 \cb3 \strokec6 - \cf4 \strokec4 **`Cursus_DDO_5.tex`** (`\\documentclass[nonewpage]\{xourse\}`) is het hoofdbestand.\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf7 \cb3 \strokec7   \cf4 \strokec4 Het bevat zelf geen inhoud, maar rijgt alle losse ximera-bestanden aaneen via\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf7 \cb3 \strokec7   \cf4 \strokec4 `\\activity\{bestand.tex\}`.\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf6 \cb3 \strokec6 - \cf4 \strokec4 **Elk los bestand** (inleiding, theorie, samenvatting, oefeningen) is een apart\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf7 \cb3 \strokec7   \cf4 \strokec4 bestand met `\\documentclass\{ximera\}`.\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf6 \cb3 \strokec6 - \cf4 \strokec4 Structuur binnen een `\\part\{...\}` (= \'e9\'e9n hoofdstuk):\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf7 \cb3 \strokec7   \cf6 \strokec6 1. \cf4 \strokec4 `\\chapterstyle` + `\\activity\{..._inleiding.tex\}` \'97 theorie-inleiding, telt als hoofdstuk.\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf7 \cb3 \strokec7   \cf6 \strokec6 2. \cf4 \strokec4 `\\sectionstyle` + een reeks `\\activity\{...\}` \'97 losse leerstof-onderdelen (geen chapterbreak).\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf7 \cb3 \strokec7      \cf4 \strokec4 Lange onderwerpen worden bewust in **2 aparte bestanden** gesplitst voor modulariteit.\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf7 \cb3 \strokec7   \cf6 \strokec6 3. \cf4 \strokec4 Nog steeds `\\sectionstyle` \'97 een `..._samenvatting.tex`.\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf7 \cb3 \strokec7   \cf6 \strokec6 4. \cf4 \strokec4 `\\chapterstyle` + `\\activity\{..._oefeningen_inleiding.tex\}` \'97 inleiding op de oefeningen.\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf7 \cb3 \strokec7   \cf6 \strokec6 5. \cf4 \strokec4 `\\sectionstyle` + oefeningen-onderdelen, **opgesplitst per type/moeilijkheidsgraad**\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf7 \cb3 \strokec7      \cf4 \strokec4 (bv. `vragen`, `basis`, `1lijn`, `driehoek`), telkens **van makkelijk naar moeilijk**.\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf2 \cb3 \strokec2 ###\cf4 \strokec4  \cf2 \strokec2 Bestandsnaamgeving\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \cb3 \strokec4 `<onderwerp>_<subonderdeel>.tex` voor theorie, `<onderwerp>oef_<type>.tex` voor\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \cb3 \strokec4 oefeningen (let op: **geen underscore** tussen onderwerp en `oef`).\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \cb3 \strokec4 Voorbeeld hoofdstuk "elektrisch veld":\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf8 \cb3 \strokec8 ```\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf8 \cb3 \strokec8 elektrischveld_inleiding.tex\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf8 \cb3 \strokec8 elektrischveld_puntlading.tex\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf8 \cb3 \strokec8 elektrischveld_veldlijnen.tex\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf8 \cb3 \strokec8 elektrischveld_materie_in_veld.tex\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf8 \cb3 \strokec8 elektrischveld_samenvatting.tex\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf8 \cb3 \strokec8 elektrischveldoef_inleiding.tex\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf8 \cb3 \strokec8 elektrischveldoef_vragen.tex\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf8 \cb3 \strokec8 elektrischveldoef_basis.tex\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf8 \cb3 \strokec8 elektrischveldoef_1lijn.tex\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf8 \cb3 \strokec8 elektrischveldoef_driehoek.tex\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf8 \cb3 \strokec8 ```\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \cb3 \strokec4 \'a0\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf2 \cb3 \strokec2 ###\cf4 \strokec4  \cf2 \strokec2 `xmPreamble.tex`\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \cb3 \strokec4 Gedeelde preamble met o.a.:\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf6 \cb3 \strokec6 - \cf4 \strokec4 `siunitx` met Franse/Belgische locale (komma als decimaalteken)\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf6 \cb3 \strokec6 - \cf4 \strokec4 TikZ-stijlen: `charge+`, `charge-`, `force` (oranje pijl), `vector` (groene pijl), `\\R` (straal ladingcirkel)\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf6 \cb3 \strokec6 - \cf4 \strokec4 `\\samenbox\{titel\}\{tekst\}`, `\\nl`, `\\mylink`\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf6 \cb3 \strokec6 - \cf4 \strokec4 `tkz-euclide` voor driehoeken/hoeken (`\\tkzDefPoint`, `\\tkzDrawPolygon`, `\\tkzFillAngle`, ...)\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf6 \cb3 \strokec6 ---\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \cb3 \strokec4 \'a0\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf2 \cb3 \strokec2 ##\cf4 \strokec4  \cf2 \strokec2 2. Documenttypes: verplichte structuur per type\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \cb3 \strokec4 \'a0\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf2 \cb3 \strokec2 ###\cf4 \strokec4  \cf2 \strokec2 a) Hoofdstuk-inleiding (`_inleiding.tex`, chapterstyle)\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf8 \cb3 \strokec8 ```latex\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf8 \cb3 \strokec8 \\documentclass\{ximera\}\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf8 \cb3 \strokec8 \\title\{...\}\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf8 \cb3 \strokec8 \\author\{Daan Lipkens\}\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf8 \cb3 \strokec8 \\begin\{document\}\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf8 \cb3 \strokec8 \\begin\{abstract\} ... \\end\{abstract\}\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf8 \cb3 \strokec8 \\maketitle\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf8 \cb3 \strokec8 \\label\{hoofdstuk:...\}\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf8 \cb3 \strokec8 \\section*\{Inleiding\}   % ONGENUMMERD\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf8 \cb3 \strokec8 ... lopende tekst, preview van het hoofdstuk ...\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf8 \cb3 \strokec8 \\end\{document\}\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf8 \cb3 \strokec8 ```\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \cb3 \strokec4 \'a0\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf2 \cb3 \strokec2 ###\cf4 \strokec4  \cf2 \strokec2 b) Theorie-onderdeel (`_onderwerp.tex`, sectionstyle)\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf6 \cb3 \strokec6 - \cf4 \strokec4 `\\section\{\}` / `\\subsection\{\}` voor structuur.\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf6 \cb3 \strokec6 - \cf4 \strokec4 `definition` / `theorem` / `proposition` / `remark` met `[foldable=true,title=\{...\}]`\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf7 \cb3 \strokec7   \cf4 \strokec4 of `[expandable=true]` \'97 **altijd voluit `=true`, nooit de kale vlag**.\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf6 \cb3 \strokec6 - \cf4 \strokec4 `\\nl` direct na de opening van zo'n omgeving (nodig voor correcte newline).\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf6 \cb3 \strokec6 - \cf4 \strokec4 `example[foldable=true,title=\{...\}]` voor uitgewerkte voorbeelden/toepassingen.\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf6 \cb3 \strokec6 - \cf4 \strokec4 Quisvragen: `\\begin\{question\}` **rechtstreeks** in de tekst (zie \'a73, geen `onlineOnly`).\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf2 \cb3 \strokec2 ###\cf4 \strokec4  \cf2 \strokec2 c) Samenvatting (`_samenvatting.tex`)\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf8 \cb3 \strokec8 ```latex\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf8 \cb3 \strokec8 \\begin\{abstract\} ... \\end\{abstract\}\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \cb3 \strokec4 \'a0\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf8 \cb3 \strokec8 \\begin\{onlineOnly\}%voor bladindeling\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf8 \cb3 \strokec8     \\maketitle\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf8 \cb3 \strokec8 \\end\{onlineOnly\}\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \cb3 \strokec4 \'a0\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf8 \cb3 \strokec8 \\newgeometry\{left=3cm,bottom=0.1cm\}\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf8 \cb3 \strokec8 \\pagestyle\{empty\}\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \cb3 \strokec4 \'a0\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf8 \cb3 \strokec8 \\begin\{conclusion\}[title=\{Samenvatting\}]\\nl\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \cb3 \strokec4 \'a0\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf8 \cb3 \strokec8 \\samenbox\{Titel blok 1\}\{ ... \}\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf8 \cb3 \strokec8 \\samenbox\{Titel blok 2\}\{ ... \}\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \cb3 \strokec4 \'a0\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf8 \cb3 \strokec8 \\end\{conclusion\}\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \cb3 \strokec4 \'a0\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf8 \cb3 \strokec8 \\restoregeometry\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf8 \cb3 \strokec8 \\pagestyle\{plain\}\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf8 \cb3 \strokec8 ```\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \cb3 \strokec4 **Let op:** `\\maketitle` staat in `onlineOnly` (i.v.m. bladindeling bij afdrukken),\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \cb3 \strokec4 `\\nl` na `\\begin\{conclusion\}[...]`, en de marge is `left=3cm,bottom=0.1cm`\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \cb3 \strokec4 (**niet** een symmetrische `margin=...`).\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \cb3 \strokec4 \'a0\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf2 \cb3 \strokec2 ###\cf4 \strokec4  \cf2 \strokec2 d) Oefeningen-inleiding (`oef_inleiding.tex`, chapterstyle)\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \cb3 \strokec4 Kort: titel, abstract, `\\maketitle`, \'e9\'e9n inleidende zin over wat volgt. Geen `\\section*\{Inleiding\}` nodig hier (dit is puur een korte aankondiging, geen theorie).\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \cb3 \strokec4 \'a0\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf2 \cb3 \strokec2 ###\cf4 \strokec4  \cf2 \strokec2 e) Oefeningen-onderdelen (`oef_<type>.tex`, sectionstyle)\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf6 \cb3 \strokec6 - \cf4 \strokec4 Enkelvoudige oefening \uc0\u8594  alles in `\\begin\{exercise\}...\\end\{exercise\}`.\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf6 \cb3 \strokec6 - \cf4 \strokec4 Meerdelige oefening \uc0\u8594  gedeelde context/gegevens bovenaan in `exercise`,\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf7 \cb3 \strokec7   \cf4 \strokec4 elke deelvraag in een eigen `\\begin\{question\}...\\end\{question\}` met eigen\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf7 \cb3 \strokec7   \cf4 \strokec4 hint(s), antwoordveld en `solution`.\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf6 \cb3 \strokec6 - \cf4 \strokec4 Oplossingen volgen het vaste stramien: `\\underline\{Gegevens:\}` (align-blok),\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf7 \cb3 \strokec7   \cf4 \strokec4 `\\underline\{Gevraagd:\}`, `\\underline\{Oplossing:\}` met `align*`-berekening.\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf6 \cb3 \strokec6 - \cf4 \strokec4 **Oefeningen binnen \'e9\'e9n bestand staan van makkelijk naar moeilijk.**\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf6 \cb3 \strokec6 ---\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \cb3 \strokec4 \'a0\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf2 \cb3 \strokec2 ##\cf4 \strokec4  \cf2 \strokec2 3. Syntax-regels (harde eisen)\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \cb3 \strokec4 \'a0\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \cb3 \strokec4 | Regel | Voorbeeld |\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \cb3 \strokec4 |---|---|\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \cb3 \strokec4 | Eenheden altijd romein, met dunne spatie | `4\{,\}0 \\cdot 10^\{6\} \\, \\mathrm\{N/C\}` |\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \cb3 \strokec4 | Decimalen met komma in wiskundemodus | `2\{,\}0 \\cdot 10^\{-6\}` |\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \cb3 \strokec4 | `foldable=true` / `expandable=true` voluit | nooit kale `[foldable]` |\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \cb3 \strokec4 | `\\section*\{Inleiding\}` ongenummerd | enkel in hoofdstuk-inleidingen |\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \cb3 \strokec4 | **`onlineOnly` NOOIT rond quizinhoud** | geen `multipleChoice`/`wordChoice`/`hint`/`solution` in `onlineOnly` \'97 dat moet zowel online als in de PDF zichtbaar zijn |\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \cb3 \strokec4 | `onlineOnly` w\'e9l voor: | video's, en `\\maketitle` in samenvattingen (bladindeling) |\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \cb3 \strokec4 | Meerdelige oefening | gedeelde gegevens in `exercise`, elke deelvraag een eigen `question` |\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \cb3 \strokec4 \'a0\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf2 \cb3 \strokec2 ###\cf4 \strokec4  \cf2 \strokec2 Hints: filosofie\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf6 \cb3 \strokec6 - \cf4 \strokec4 Een hint is een duw in de rug voor een **tussenstap** in een **lastig, meerstappen-probleem**,\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf7 \cb3 \strokec7   \cf4 \strokec4 voor wie vastzit \'97 **geen** rechtstreekse vermelding van de te gebruiken formule\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf7 \cb3 \strokec7   \cf4 \strokec4 (dus niet: *"Gebruik $F=QE$."*).\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf6 \cb3 \strokec6 - \cf4 \strokec4 **Eenvoudige, \'e9\'e9ntraps-oefeningen hebben vaak helemaal geen hint nodig.**\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf6 \cb3 \strokec6 - \cf4 \strokec4 Bij hints w\'e9l toegestaan/gewenst: een conceptuele vraag die het denkproces op gang\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf7 \cb3 \strokec7   \cf4 \strokec4 brengt (*"Wat gebeurt er met de richting van de kracht als je het teken van de lading omdraait?"*),\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf7 \cb3 \strokec7   \cf4 \strokec4 of een aanwijzing over **welke tussenstap** nog ontbreekt (*"Je hebt nog $r_\{23\}$ nodig \'97 hoe vind je die in deze driehoek?"*).\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf6 \cb3 \strokec6 ---\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \cb3 \strokec4 \'a0\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf2 \cb3 \strokec2 ##\cf4 \strokec4  \cf2 \strokec2 4. Afbeeldingen\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \cb3 \strokec4 \'a0\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf6 \cb3 \strokec6 - \cf4 \strokec4 Pad per hoofdstuk: `pic5/elektriciteit/<onderwerp>/` (bv. `pic5/elektriciteit/veld/`).\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf6 \cb3 \strokec6 - \cf4 \strokec4 **Nooit** figuren uit Interactie of Serway scannen/overnemen (auteursrecht).\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf6 \cb3 \strokec6 - \cf4 \strokec4 Voorkeur: **originele TikZ-tekeningen**, rechtstreeks in de `.tex`-bestanden,\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf7 \cb3 \strokec7   \cf4 \strokec4 met de stijlen uit `xmPreamble.tex` (`charge+`, `charge-`, `force`, `vector`).\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf7 \cb3 \strokec7   \cf4 \strokec4 Dit vermijdt zowel auteursrechtproblemen als het beheer van losse beeldbestanden.\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf6 \cb3 \strokec6 - \cf4 \strokec4 Enkel wanneer een tekening echt te complex is voor TikZ, een `\\includegraphics`\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf7 \cb3 \strokec7   \cf4 \strokec4 placeholder met een `% TIP:`-commentaar naar een vergelijkbare (niet over te nemen) bronfiguur.\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf6 \cb3 \strokec6 ---\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \cb3 \strokec4 \'a0\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf2 \cb3 \strokec2 ##\cf4 \strokec4  \cf2 \strokec2 5. Bronnenbeleid\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \cb3 \strokec4 \'a0\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf6 \cb3 \strokec6 - \cf4 \strokec4 **Hoofdbron**: *Interactie* (oud handboek, niet meer verkocht) \'97 leidt de opbouw en\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf7 \cb3 \strokec7   \cf4 \strokec4 voorbeeldtypes van elk hoofdstuk.\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf6 \cb3 \strokec6 - \cf4 \strokec4 **Aanvullend/inspiratie**: Serway, *Physics for Scientists and Engineers*, 7th ed. \'97\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf7 \cb3 \strokec7   \cf4 \strokec4 voor niveau, "Quick Quiz"-stijl en extra oefeningen, maar dieper dan het leerplan vereist.\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf6 \cb3 \strokec6 - \cf4 \strokec4 Beide bronnen: **nooit letterlijk overnemen** (tekst, cijfers-configuraties of figuren).\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf7 \cb3 \strokec7   \cf4 \strokec4 Altijd herschrijven/herwerken naar eigen voorbeelden op middelbare-schoolniveau.\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf6 \cb3 \strokec6 - \cf4 \strokec4 **Leerplanbeperking** (NatS, oktober 2024, LPD 2/3 F): elektrische krachtwerking en\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf7 \cb3 \strokec7   \cf4 \strokec4 elektrisch veld blijven beperkt tot ladingen **in lijn** of **onder een rechte hoek\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf7 \cb3 \strokec7   \cf4 \strokec4 (stelling van Pythagoras)**. Willekeurige (scalene) driehoeken met cosinusregel op\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf7 \cb3 \strokec7   \cf4 \strokec4 een niet-rechte hoek horen niet tot de basisleerstof \'97 enkel gelijkzijdige driehoek/vierkant\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf7 \cb3 \strokec7   \cf4 \strokec4 als verdieping voor sterkere leerlingen, duidelijk gelabeld als extra.\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf6 \cb3 \strokec6 ---\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \cb3 \strokec4 \'a0\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf2 \cb3 \strokec2 ##\cf4 \strokec4  \cf2 \strokec2 6. Werkwijze die goed werkt\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \cb3 \strokec4 \'a0\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf6 \cb3 \strokec6 1. \cf4 \strokec4 Eerst **bestaande bestanden nalezen en herschrijven** naar de conventies hierboven,\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf7 \cb3 \strokec7    \cf4 \strokec4 pas daarna **nieuwe bestanden** toevoegen.\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf6 \cb3 \strokec6 2. \cf4 \strokec4 **Alle numerieke antwoorden vooraf verifi\'ebren** (bv. met Python) v\'f3\'f3r ze in een\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf7 \cb3 \strokec7    \cf4 \strokec4 `.tex`-bestand komen.\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf6 \cb3 \strokec6 3. \cf4 \strokec4 Nieuwe TikZ-figuren **compileren en visueel controleren** (pdflatex + pdftoppm)\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf7 \cb3 \strokec7    \cf4 \strokec4 v\'f3\'f3r ze in het definitieve bestand komen.\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf6 \cb3 \strokec6 4. \cf4 \strokec4 Oefeningen binnen eenzelfde bestand **aantoonbaar oplopend** in moeilijkheidsgraad;\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf7 \cb3 \strokec7    \cf4 \strokec4 bij twijfel een korte rationale geven voor de volgorde.\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf6 \cb3 \strokec6 ---\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \cb3 \strokec4 \'a0\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf2 \cb3 \strokec2 ##\cf4 \strokec4  \cf2 \strokec2 7. Tips om deze chat op te splitsen (tokens besparen)\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \cb3 \strokec4 \'a0\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \cb3 \strokec4 **Kernprobleem:** \'e9\'e9n lange doorlopende chat herhaalt impliciet alle eerdere context\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \cb3 \strokec4 (bestandsinhoud, afspraken, gecompileerde figuren, ...) bij elk nieuw bericht, wat duur\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \cb3 \strokec4 en traag wordt.\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \cb3 \strokec4 \'a0\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf2 \cb3 \strokec2 ###\cf4 \strokec4  \cf2 \strokec2 a) Gebruik een Claude Project\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf6 \cb3 \strokec6 - \cf4 \strokec4 Maak \'e9\'e9n **Project** aan voor deze cursus (bv. "Cursus DDO 5 \'96 Fysica").\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf6 \cb3 \strokec6 - \cf4 \strokec4 Upload in de **project-kennis** (niet in een losse chat): dit stijldocument,\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf7 \cb3 \strokec7   \cf4 \strokec4 `xmPreamble.tex`, en 1 volledig uitgewerkt hoofdstuk als referentievoorbeeld.\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf6 \cb3 \strokec6 - \cf4 \strokec4 Elke **nieuwe chat binnen dat Project** leest deze kennis automatisch in \'97 je hoeft\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf7 \cb3 \strokec7   \cf4 \strokec4 niet opnieuw uit te leggen hoe `\\samenbox` werkt of dat `onlineOnly` niet rond\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf7 \cb3 \strokec7   \cf4 \strokec4 quizvragen mag staan.\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf6 \cb3 \strokec6 - \cf4 \strokec4 Voeg eventueel **custom instructions** toe op projectniveau (bv. "Volg altijd\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf7 \cb3 \strokec7   \cf4 \strokec4 Ximera_stijlgids_Cursus_DDO5.md strikt; verifieer rekenwerk in Python; schrijf oefeningen\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf7 \cb3 \strokec7   \cf4 \strokec4 van makkelijk naar moeilijk").\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf2 \cb3 \strokec2 ###\cf4 \strokec4  \cf2 \strokec2 b) Splits per hoofdstuk, niet per cursus\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf6 \cb3 \strokec6 - \cf4 \strokec4 Start een **nieuwe chat per hoofdstuk** (of zelfs per documenttype: theorie vs.\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf7 \cb3 \strokec7   \cf4 \strokec4 oefeningen vs. figuren), en upload enkel de bestanden die voor d\'e1t hoofdstuk relevant zijn\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf7 \cb3 \strokec7   \cf4 \strokec4 \'97 niet de volledige cursus of alle bronbestanden opnieuw.\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf2 \cb3 \strokec2 ###\cf4 \strokec4  \cf2 \strokec2 c) Splits type werk\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf6 \cb3 \strokec6 - \cf4 \strokec4 **Tekst/oefeningen schrijven** en **TikZ-figuren tekenen** vergen een ander soort\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf7 \cb3 \strokec7   \cf4 \strokec4 iteratie (figuren hebben veel compileer-heen-en-weer nodig). Aparte chats hiervoor\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf7 \cb3 \strokec7   \cf4 \strokec4 houden beide sneller en goedkoper.\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf2 \cb3 \strokec2 ###\cf4 \strokec4  \cf2 \strokec2 d) Geef feedback gebundeld\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf6 \cb3 \strokec6 - \cf4 \strokec4 Verzamel feedback over meerdere bestanden en geef die in **\'e9\'e9n bericht**, in plaats\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf7 \cb3 \strokec7   \cf4 \strokec4 van per bestand een apart correctierondje te starten. Dat scheelt een volledige\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf7 \cb3 \strokec7   \cf4 \strokec4 "herlees-en-antwoord"-cyclus per opmerking.\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf2 \cb3 \strokec2 ###\cf4 \strokec4  \cf2 \strokec2 e) Laat afspraken expliciet vastleggen\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf6 \cb3 \strokec6 - \cf4 \strokec4 Zinnen als *"onthoud dat..."* of *"doe dit voortaan zo..."* zorgen ervoor dat de\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf7 \cb3 \strokec7   \cf4 \strokec4 afspraak in het geheugensysteem terechtkomt en in toekomstige chats **binnen\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf7 \cb3 \strokec7   \cf4 \strokec4 hetzelfde Project** automatisch wordt toegepast, zonder dat je het opnieuw moet\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf7 \cb3 \strokec7   \cf4 \strokec4 uitleggen. Herhaal dit wel expliciet bij belangrijke stijlregels \'97 vertrouw niet\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf7 \cb3 \strokec7   \cf4 \strokec4 blind op automatische onthouding voor kritieke afspraken; controleer ze af en toe\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf7 \cb3 \strokec7   \cf4 \strokec4 door te vragen "wat onthoud je over de stijl van samenvattingen?".\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf6 \cb3 \strokec6 - \cf4 \strokec4 Dit stijldocument is de **robuustere back-up**: geheugen kan verouderen of gemist\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf7 \cb3 \strokec7   \cf4 \strokec4 worden, een ge\'fcpload referentiebestand niet.\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf4 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf2 \cb3 \strokec2 ###\cf4 \strokec4  \cf2 \strokec2 f) Houd bestanden atomair\cf4 \cb1 \strokec4 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf6 \cb3 \strokec6 - \cf4 \strokec4 Vraag per chat om **\'e9\'e9n of enkele bestanden** tegelijk, niet "maak het hele hoofdstuk".\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf7 \cb3 \strokec7   \cf4 \strokec4 Kleinere, concrete taken zijn makkelijker te controleren en goedkoper te herdoen\cb1 \
\pard\pardeftab720\partightenfactor0
\cf5 \strokec5 \
\pard\pardeftab720\partightenfactor0
\cf7 \cb3 \strokec7   \cf4 \strokec4 als er iets moet worden aangepast.\cb1 \
}