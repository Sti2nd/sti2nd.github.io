---
layout: post
title:  "Smartspeil del 1: Maskinvaren"
date:   2020-01-15 08:18:12 +0100
categories: [smartspeil, magisk speil, magic mirror norsk, magic mirror norge]
permalink: /smartspeil-del-1-maskinvaren/
---
## Introduksjon

Helt siden jeg for flere år siden oppdaget smartspeil har jeg hatt lyst til å lage et. Smartspeil er for de som ikke vet det et delvis gjennomsiktig speil med en skjerm bak. Et <a href="https://www.google.com/search?q=magic+mirror" target="_blank" rel="noopener noreferrer">søk på Google Bilder etter "magic mirror"</a> gir mange eksempler. Det var først når jeg begynte å jobbe og fant ut at jeg hadde litt fritid å slå i hjel at jeg endelig klarte å lage et.

Dette innlegget beskriver hvordan jeg bygde det fysiske smartspeilet, mens jeg planlegger å lage en del 2 som beskriver programvaren.

### Hvorfor lage et smartspeil

Mine grunner til at jeg ville ha smartspeil var:

1. Det kan være nyttig ved å vise informasjon om kollektivtrafikken
    - Spesielt tog som plutselig kan bli innstilt hadde vært fint å få vite om før man tar en bomtur til togstasjonen. Jeg har opplevd at tog har blitt innstilt fra jeg sjekket ruteplanleggeren under frokost til jeg var på stasjonen 20 minutter senere.
2. Det er superkult i seg selv! Det ser unektelig fænsi ut med dynamisk innhold på et speil, uansett hva innholdet er.
3. Virket som et overkommelig og gøy prosjekt med et kult resultat.
    - Av det jeg har sett er smartspeil dyre å kjøpe fra de få selskapene som lager dem. Det er altså billigere å lage det selv, og jeg regnet med at det kom til å være litt gøy å lage selv også. Dessuten får man akkurat hva man vil ha 🤩
    - Moro lenge! Etter man er ferdig med maskinvaren kan man fortsette å utvide programvaren med nye funksjoner. For eksempel hadde jeg en visjon om å bruke ansiktsgjenkjenning til å vise raskeste rute til jobb bare man så på speilet. Jeg bor nemlig i et kollektiv, så jeg synes ikke jeg kan hardkode min rute til jobb.

## Hvordan skal smartspeilet se ut

Det finnes mange tutorials for hvordan man kan bygge sitt magiske speil; jeg valgte å ta utgangspunkt i de norske artiklene jeg har funnet og lest opp gjennom åra [ [NRK beta][1], [Cato Antonsen][4], [Didrik Sæther][2], [kode24 HackTechGo!][3] ]. Mye av byggingen ble naturligvis improvisasjon.

Det absolutt viktigste var å gjøre prosjektet så enkelt og raskt at jeg faktisk ville fullføre siden jeg tross alt hadde brukt to-tre år på å starte. Jeg hadde fra før av omtrent null kunnskap om trearbeid og elektronikk, men tenkte at jeg skulle klare å bygge ramma fra bunnen av omtrent sånn som [Cato Antonsen][4] gjorde det.

Min plan var å henge opp speilet i gangen der hvor ytterdøra er, siden jeg trodde det var der det ville gjøre mest nytte for seg. Å unngå våtrom virket også som et godt valg for å gjøre byggingen enklest mulig.

### Størrelsen

Jeg tenkte å bruke en eksisterende 24 tommers monitor bak speilet, men ville at speilet skulle være større enn bare 24 tommer. Jeg måtte altså bestemme meg hvor mye større speilet skulle være og hvor skjermen skulle være bak speilet. I noen av smartspeilene jeg har sett på nett er skjermen sentrert i midten av speilet. Jeg har aldri skjønt hva som er poenget med å ha et speil hvis det er vanskelig å unngå at det er tekst midt i ansiktet sitt når man speiler seg, så det skulle jeg unngå! Jeg bestemte meg for at skjermen skulle være plassert i portrettmodus bak den ene siden av speilet og den andre siden forbeholdt å speile seg. På den måten kan man fylle opp skjermen med så mye tekst som man vil og fortsatt ha plass til å speile seg.

![Magic Mirror 4:3 aspect ratio](/assets/magimirror_4-3-ratio.png)
Først tenkte jeg at størrelsesforholdet 4:3 ville være perfekt, men etter å ha tegnet det opp i Paint (illustrasjonen over) ble jeg redd for at man skulle se på speilet som et imperfekt kvadrat. Siden 16:9 gjorde at speilet hadde blitt omtrent 1 meter langt, endte jeg opp med å bruke 3:2. Målene på det synlige speilet endte da opp på 54,5cm x 82cm.

#### Tykkelsen

Ett siste mål jeg jobbet mot var å bygge hele konstruksjone mindre enn 10cm tykt. Jeg var ganske sikker på at jeg skulle klare å ha maks 7.5cm i dybden.

## Delene / maskinvaren

En rask oversikt:

- Speil: Pilkington MirroView™. Dimensjon: 555mm x 830mm Kostnad: 3100kr.
- Skjerm: BenQ 24" GW2470H. Dimensjon: 545mm x 320mm. Kostet rundt 1000kr på salg for noen år siden.
- Ramme: Spesiallaget fra Artifix på Sagene. Kostnad: 1500kr

### Speil



### Skjerm

Det jeg vektla når det kom til skjerm var at den skulle ha ok svartnivå og være relativt tynn. Hvis svartnivået er dårlig kan man se overgangen fra skjerm til ikke skjerm gjennom speilet. Dette kalles "bleeding" og er en av grunnene til at en heldekkende skjerm kan være bedre. Jeg hadde to monitorer fra før av, begge billige, og tenkte at den beste måten å vite om en skjerm var tynn nok var å demontere den og sjekke. Siden min BenQ-skjerm hadde bedre svartnivå enn den enda billigere AOC-skjermen, ofret jeg den. Å demontere skjermen var det andre jeg gjorde sånn at jeg fant ut hvor tynn hele konstruksjonen kunne bli.

_Den nøyaktige modellen jeg bruker selges ikke lenger, så jeg tror den som er nærmeste lik min nå er BenQ 24 GW470ML._

#### Demontering av skjerm

Siden min skjerm hadde et buet plastpanel på baksiden var den tykk. Først skrudde jeg av foten. Så lirket jeg av plastikkpanelet bak på skjermen. Da var den eneste plastikken igjen en svart ramme i kanten foran på skjermen. Alle knappene til skjermen satt på et langt tynt kort (se bilde), og kortet dro jeg enkelt opp fra rammen. Med en kniv klarte jeg å jekke av rammen som satt rundt fronten av skjermen. På baksiden av skjermen var det nå en firkantet metallkonstruksjon.

![Disassemble screen 1](/assets/disassemble_screen_1.jpg)

Originalt tenkte jeg ikke demontere skjermen mer, men siden jeg så mitt snitt til å få et enda tynnere smartspeil gjorde jeg det allikevel.

![Disassemble screen 2](/assets/disassemble_screen_2.jpg)

I metallfirkanten befant det seg to kretskort. Kretskortene ble skrudd ut uten at jeg trengte å fjerne noen ledninger.

![Disassemble screen 3](/assets/disassemble_screen_3.jpg)

I bilde over ser vi skjermen ferdig demontert. Siden jeg nå kunne plassere kretskortene ved siden av skjermen i stedet for oppå, ville skjermen kunne bli så tynn som 3cm (eller 4cm?)!

[1]: https://nrkbeta.no/2017/02/08/slik-bygde-vi-et-magisk-smart-speil/
[2]: https://grensesnittet.computas.com/smartspeil-uten-kanter/
[3]: https://www.kode24.no/guider/slik-bygger-du-et-smartspeil/70550032
[4]: https://www.bouvet.no/bouvet-deler/utbrudd/magic-mirror-version-1