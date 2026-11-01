# Udvidelser i version 2.1

Alle funktioner kører i browseren. Aktiviteter vedligeholdes fortsat i Excel-filen på den fælles webadresse. Der er ingen ekstra konto, database eller applikationsserver.

## 1. Gentagne aktiviteter

Tilføj de valgfrie kolonner nedenfor **inde i `tblAktiviteter`**, eller hent den nye skabelon via **Kontrollér Excel**. Eksisterende arbejdsbøger uden disse kolonner virker fortsat. Kopiér dine egne data til skabelonen; erstat ikke den publicerede arbejdsbog med eksempeldata.

| Kolonne | Indhold |
| --- | --- |
| Gentagelse | Tom/Ingen, Dagligt, Ugentligt, Hver 2. uge, Månedligt eller en kombination som Første tirsdag |
| GentagTil | Sidste startdato inklusive. Tom betyder skoleårets sidste dag |
| Undtagelser | Startdatoer der skal springes over, som `2026-09-14;2026-10-12` |
| Frist | Valgfri dato; kan også bruges uden gentagelse |

Ved ugedage understøttes Første, Anden, Tredje, Fjerde og Sidste efterfulgt af mandag, tirsdag, onsdag, torsdag, fredag, lørdag eller søndag. Skabelonens korte rullemenu viser et udvalg; andre understøttede kombinationer kan skrives direkte.

Startdato er den tidligste tilladte start. Ugentligt og Hver 2. uge følger denne datos ugedag. Månedligt følger datoens dagnummer og springer måneder uden dette dagnummer over; en aktivitet den 31. flyttes ikke til den 30. En regel som Første tirsdag finder den første tirsdag i hver måned på eller efter Startdato. Slutdato angiver varigheden af hver forekomst, ikke gentagelsesperiodens slutning. Kun hele forekomster inden for skoleåret medtages.

Eksempel: Startdato `2026-09-07`, Slutdato `2026-09-07`, Gentagelse `Ugentligt`, GentagTil `2026-09-28`, Undtagelser `2026-09-14`. Det giver aktiviteter den 7., 21. og 28. september.

En Frist på fredagen før første aktivitet bliver også fredagen før hver efterfølgende aktivitet. Gentagelser bevarer lokal dansk tid over sommer-/vintertid. Hvis en forekomst rammer et ikke-eksisterende eller tvetydigt tidspunkt, viser kontrollen den konkrete dato. Flyt tidspunktet, angiv et gyldigt offset ved tvetydighed, eller udelad datoen via Undtagelser.

Der må højst være 2.000 aktiviteter inklusive gentagelser. Hver forekomst får et stabilt ID af rækkens ID og startdato. Bevar rækkens ID, når du retter indhold. Flytter du datoen, ændres forekomstens identitet; det påvirker delingslinks og kalenderimport. Gentagelser udvides også i print, PDF og ICS. Frister står som oplysninger i eksporten og er ikke særskilte kalenderaftaler.

Vil du aflyse en enkelt forekomst, udelades dens startdato i Undtagelser, og der kan oprettes en særskilt aktivitet med status Aflyst og en begrundelse.

## 2. Ændringsoversigt

**Ændringer** viser nye, ændrede, aflyste og fjernede aktiviteter siden den seneste version, browseren så ved sidste besøg. Nye ændringer opdages også, mens siden er åben. Første besøg etablerer et sammenligningsgrundlag. **Markér ændringer som set** nulstiller sammenligningen til den aktuelle version.

Grundlaget er lokalt for browseren og den konkrete Excel-filadresse. Det er ikke en fælles revisionslog. Kun offentliggjorte/aflyste aktiviteter i synlige skoleår medtages. Browseren gemmer ID, titel, skoleår, status og et kort fingeraftryk; beskrivelser gemmes ikke i historikgrundlaget. Ved bortfald af adgang eller en fjernet fil ryddes det lokale grundlag. Sletning af browserdata fjerner også historikken. Hvis lokal lagring er blokeret, virker sammenligningen kun i den åbne fane.

## 3. Aktivitetslinks

Åbn en aktivitet og vælg **Kopiér aktivitetslink**. Du kan også kopiere fra feltet Link til aktivitet. Linket kan deles i Teams eller mail og åbner det rigtige skoleår og aktivitetsdetaljerne, selv om modtagerens gemte filtre ville skjule aktiviteten.

Links giver ikke nye læserettigheder. En fjernet aktivitet eller en kladde giver en besked. Et link til en gentagelse gælder den konkrete forekomst.

## 4. Gemte visninger

**Gemte visninger** husker som standard seneste skoleår, visning, årgangsfiltre, søgning og periode på den aktuelle enhed. Hukommelsen kan slås fra. På mobil bruges Liste ved første besøg; efterfølgende bruges din gemte visning.

Giv en visning et navn og vælg **Gem visning**. Der kan gemmes op til 12 navngivne visninger pr. Excel-filadresse. Det samme navn overskriver den eksisterende visning. Vælg en gemt visning og brug **Åbn visning** eller **Slet visning**. Visningerne deles ikke mellem enheder og indeholder ingen særskilt konto.

## 5. Kommende aktiviteter og frister

Vælg **Kommende** og en periode på 7, 14 eller 30 dage. Oversigten tager udgangspunkt i dags dato i Danmark og viser både igangværende aktiviteter og kommende starter/frister. Perioden omfatter i dag og de følgende dage op til den valgte periodes slutning, eksklusive slutdatoen.

Frister kan gøre en senere aktivitet synlig, før dens startdato ligger i perioden. Frister markeres tydeligt; en overskredet frist på en ellers kommende eller igangværende aktivitet markeres som overskredet. Aflyste aktiviteter og kladder vises ikke her. Skoleår, årgangsfiltre og søgning gælder stadig.

Print/PDF/ICS bruger fortsat hele det valgte skoleår og de aktive årgangs-/søgefiltre, som eksportlinjen angiver. Perioden på 7/14/30 dage indsnævrer alene Kommende og infoskærmens kommende-oversigt.

## 6. Konfliktkontrol

**Konflikter** viser mulige overlap i den valgte visning. To offentliggjorte aktiviteter overlapper, hvis deres tidsrum har fælles tid, og de har mindst ét af følgende:

- Samme årgang; Fælles regnes som relevant for alle årgange.
- Samme udfyldte lokale.
- Samme udfyldte ansvarlige.

Et arrangement der slutter kl. 10 og et der begynder kl. 10, overlapper ikke. Heldagsaktiviteter optager hele dagen. Lokale og ansvarlige sammenlignes uden forskel på store/små bogstaver og ekstra mellemrum, som hele feltværdier. Forskellige stavemåder af det samme navn genkendes ikke automatisk. Kladdestatus og aflysninger tælles ikke.

Overlap er advarsler; ferieperioder, fællesarrangementer og parallelle forløb kan være tilsigtede. Kontrollen reserverer ikke lokaler. Der vises højst 200 konfliktpar ad gangen; brug filtrene for at indsnævre listen.

## 7. Kontrollér Excel før publicering

Åbn **Kontrollér Excel**, og vælg den redigerede lokale fil. Den samme Excel-læser og de samme valideringsregler som ved almindelig indlæsning bruges, inklusive gentagelser, formler, datoer, kryptering og filstørrelse.

En gyldig fil får antal aktiviteter/skoleår, konfliktadvarsler, sammenligning med den indlæste fil og en forhåndsvisning af de første 20 synlige aktiviteter. Ved fejl vises første konkrete fejl med felt/række, hvor det er muligt. Ret fejlen og vælg filen igen for at kontrollere videre.

Filen behandles lokalt og uploades ikke. Den fælles kilde ændres ikke. Når kontrollen er tilfredsstillende, skal du selv gemme eller uploade filen til den publicerede Excel-adresse. Brug Opdater nu bagefter.

## 8. Infoskærm

Vælg **Infoskærm** for stor skrift og automatisk skift mellem kommende aktiviteter og hele årshjulet. Kommende vises med seks aktiviteter ad gangen; efter hvert årshjul vises næste side. Skoleår, periode og årgangsfiltre følger de valgte indstillinger; den aktuelle søgning gælder i den åbne fane.

Du kan ændre skifteintervallet, sætte skift på pause, skifte manuelt eller vælge Fuld skærm. Ved browserindstillingen reduceret bevægelse starter automatisk skift på pause. Fuld skærm afhænger af browseren/Teams; almindelig vinduesvisning virker også. **Afslut infoskærm** eller Escape går tilbage.

Adresselinjen får `screen=1` og de valgte skoleår/årgange/periode. Bogmærk eller kopiér denne adresse for at åbne direkte i infoskærmstilstand igen. Søgningen gemmes ikke i skærmlinket. Ved ændringer i Excel opdateres indholdet som normalt. Når fanen er skjult, skiftes der ikke automatisk mellem visninger.
