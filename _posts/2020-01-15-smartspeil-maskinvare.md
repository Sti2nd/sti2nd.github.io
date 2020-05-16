---
layout: post
title:  "Smartspeil del 1: Maskinvaren"
description: "Hvordan jeg bygget et smartspeil."
date:   2020-01-15 08:18:12 +0100
categories: [hackerspace]
tags: [smartspeil, magisk speil, magic mirror norsk, magic mirror norge, technical, makerspace, hackerspace]
permalink: /smartspeil-del-1-maskinvaren/
lang: nb_NO
image: /assets/smartspeil-maskinvare/finished_close_up.jpg
author: "Stian Jørgensrud"
---

Denne posten beskriver med bilder hvordan jeg bygget et smartspeil.

![Finished close up](/assets/smartspeil-maskinvare/finished_close_up.jpg)

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

Det finnes mange tutorials for hvordan man kan bygge sitt magiske speil; jeg valgte å ta utgangspunkt i de norske artiklene jeg har funnet og lest opp gjennom åra: [NRK beta][1], [Cato Antonsen][4], [Didrik Sæther][2], [kode24 HackTechGo!][3]. Mye av byggingen ble naturligvis improvisasjon.

Det absolutt viktigste var å gjøre prosjektet så enkelt og raskt at jeg faktisk ville fullføre siden jeg tross alt hadde brukt to-tre år på å starte. Jeg hadde fra før av omtrent null kunnskap om trearbeid og elektronikk, men tenkte at jeg skulle klare å bygge ramma fra bunnen av omtrent sånn som [Cato Antonsen][4] gjorde det. Jeg ville også gjøre det relativt billig og tenkte på plastglass som speil.

Min plan var å henge opp speilet i gangen der hvor ytterdøra er, siden jeg trodde det var der det ville gjøre mest nytte for seg. Å unngå våtrom virket også som et godt valg for å gjøre byggingen enklest mulig.

### Størrelsen

Jeg tenkte å bruke en eksisterende 24 tommers monitor bak speilet, men ville at speilet skulle være større enn bare 24 tommer. Jeg måtte altså bestemme meg hvor mye større speilet skulle være og hvor skjermen skulle være bak speilet. I noen av smartspeilene jeg har sett på nett er skjermen sentrert i midten av speilet. Jeg har aldri skjønt hva som er poenget med å lag et speil hvis det kommer til å være tekst midt i ansiktet sitt når man speiler seg, så det skulle jeg unngå! Jeg bestemte meg for at skjermen skulle være plassert i portrettmodus bak den ene siden av speilet, og den andre siden skulle være forbeholdt å speile seg. På den måten kan man fylle opp skjermen med så mye tekst som man vil og fortsatt ha plass til å speile seg!

![Magic Mirror 4:3 aspect ratio](/assets/smartspeil-maskinvare/magimirror_4-3-ratio.png)
Først tenkte jeg at størrelsesforholdet 4:3 ville være perfekt, men etter å ha tegnet det opp i Paint (illustrasjonen over) ble jeg redd for at man skulle se på speilet som et imperfekt kvadrat. Siden 16:9 gjorde at speilet hadde blitt omtrent 1 meter langt, endte jeg opp med å bruke 3:2. Målene på det synlige speilet endte da opp på 54,5cm x 82cm. I ettertid tenker jeg at 3:2 sannsynligvis ville sett bra ut det også.

#### Tykkelsen

Ett siste mål jeg jobbet mot var å bygge hele konstruksjone mindre enn 10cm tykt. Jeg var ganske sikker på at jeg skulle klare å ha maks 7.5cm i dybden.

## Delene / maskinvaren

En rask oversikt:

- Speil: Pilkington MirroView™. Dimensjoner: 555mm x 830mm Kostnad: 3100kr.
- Skjerm: BenQ 24" GW2470H. Dimensjoner: 545mm x 320mm. Kostet rundt 1000kr på salg for noen år siden.
- Ramme: Spesiallaget fra Artifix på Sagene. Kostnad: 1500kr

### Speil

En essensiell del av et smartspeil er det delvis gjennomsiktige speilet. Hele greia er at det skal se ut som et speil, men at man samtidig ser det dynamiske innholdet på baksiden. Gjennomsiktige speil er også kjent som enveisspeil, toveisspeil, spionspeil og argusspeil, alt etter hvilken glassmester du spør 😜

#### Speilteori

To viktige ting å få med seg.

1\. Speil = vindu ?

Dette er bare et definisjonsspørsmål, men hvis et speil er gjennomsiktig, er det ikke da et vindu? Det meste av glass er gjennomsiktig og gir refleksjon samtidig. Det vi kan gjøre er å skaffe oss et glass, og så lenge det er lysere på vår side av glasset enn den andre vil vi se oss selv sterkere enn den andre siden. Jeg har lest et sted at det burde minst være 5 ganger lysere på din side for å få en bra speileffekt.

2\. Gjennomsiktighet vs. refleksjon.

I et speil kommer mesteparten av lyset tilbake uten å ha blitt forvrengt, så vi vil helst bruke et materiale som har mest mulig av denne egenskapen. Samtidig må skjermen bak speilet vårt kunne sende lys gjennom speilet, så materialet vi bruker som speil må også tillate nok lys å passere gjennom slik at vi ser skjermen bak godt nok. Men når gjennomsiktigheten øker, går refleksjonen ned (sannsynligvis i et omvendt lineært forhold). Det er altså (etter det jeg skjønner) umulig å ha et materiale som reflekterer 100% av lyset (et ekte speil) og samtidig slipper lys igjennom.

Det kommer alltid til å være et kompromiss (trade-off) mellom gjennomsiktighet og refleksjon. Jo tydeligere man vil se skjermen, jo mindre lys kommer til å bli reflektert og jo mørkere kommer speilet til å se ut. Vil man at refleksjonen skal ligne mest mulig på et ekte speil må man ha høy refleksjon, men da vil skjermen se svakere ut. Alt handler om lys. Basert på speilene til nettsiden [Two way mirrors][5] gjettet jeg på at et speil med 70% refleksjon og 30% gjennomsiktighet er det beste.

#### Materialer som speil

Jeg vurderte materialene glass og plast.

##### Plast

Plast kan være så gjennomsiktig at det rett og slett kan brukes som glass! Plexiglass er et kjent navn og en underkategori av akrylglass (som også er plastglass). Et akrylglass kombinert med en folie kan lage et fint speil, og hvis folien er litt gjennomsiktig et enveisspeil.

Fordeler med plastglass:

- Lett
- Billig
- Kan bearbeides (kuttes, drilles) selv

Ulemper med plastglass:

- Riper lett
- Bøyer seg hvis arealet blir for stort

##### Glass

Glass kan, som vi vet, være gjennomsiktig. Kombinert med folie eller tilsatt noe (metall?) kan refleksjonen øke (på bekostning av gjennomsiktighet).

Fordeler med glass:

- Stivt.
  - Vanskelig å ripe.
  - Bøyer seg ikke på store speil.
- Høy kvalitet
  - Høy klarhet (gjennomsiktighet)
  - Varer lenge

Ulemper med glass:

- Tungt
- Dyrt
- Kan knuse
- Kan ikke bearbeides selv

Jeg ville ha et materiale som så bra ut med 54,5cm x 82cm og hadde lest at akrylglass kunne begynne å bøye seg når det ble så stort. Valget falt på glass. Jeg sendte e-post til noen glassmestere og spurte om de hadde noen glass til mitt bruk og ba om å få oppgitt verdier for refleksjon og gjennomsiktighet. Til slutt sammenlignet jeg pris og refleksjon og gjennomsiktighet på tilbudene og endte opp med et glass laget spesielt til smartspeil, [Pilkington MirroView™][6]. Kjøpte fra glassmesteren Altiglass. Speilet har en gjennomsiktighet på 25% og refleksjon på 64%, og er litt dyr (men faktisk ikke det dyreste tilbudet jeg fikk). Verdiene på Pilkington sine MirrorView produkter står på side 66 (68 i pdf-leser) i brosjyren [Glassfakta 2018](https://www.pilkington.com/nb-no/no/produkter/funksjonsglass/spesialglass/pilkington-mirroview#brosjyrer).

### Ramme

Jeg hadde ringt rundt til forskjellige byggevareforretninger og sjekket dimensjonene på konstruksjonstrevirke for å finne noe som passet. Et problem som gjensto å løse var at jeg nesten ikke eide verktøy. Jeg planla å kutte de fire plankene som skulle utgjøre ramma i 45 grader på hver ende, men jeg hadde bare en sag i barnestørrelse som var forferdelig å jobbe med. Planen var også å frese et spor til speilet som [Cato Antonsen][4] hadde gjort, men det var i hvertfall umulig uten verktøy. Jeg sjekket ut makerspace i Oslo for å se om de kunne hjelpe meg, og det kunne de, men jeg måtte ta kurs for å frese. Og bil hadde jeg heller ikke til å frakte materialer frem og tilbake. På dette tidspunktet hadde jeg planlagt litt og litt i flere måneder og anskaffet speil. Siden juleferien kom og jeg var lei av lite fremgang bestemte jeg meg for at det var viktigere å få startet enn å bruke enda flere måneder på å lage en ramme fra bunnen av. Jeg er jo ingen snekker men en informatiker! Jeg stakk bort til Artifix på Sagene og fikk bestilt en ramme som jeg kunne hente (med kollektivtrafikk) noen dager senere, ferdig malt!

![Black frame example](/assets/smartspeil-maskinvare/black_frame.jpg)

_Illustrasjon av hvordan en ramme kan se ut fra [bgafotobutikk](https://www.bgafotobutikk.no/). Min ramme var mørkegrå._

En bekymring jeg fikk var at ramma var veldig lett, så jeg håpet på at ramma ikke ville svikte og speilet knuse.

### Skjerm

Det jeg vektla når det kom til skjerm var at den skulle ha ok svartnivå og være relativt tynn. Hvis svartnivået er dårlig kan man se overgangen fra skjerm til ikke skjerm gjennom speilet. Dette kalles "bleeding" og er en av grunnene til at en heldekkende skjerm kan være bedre. Jeg hadde to monitorer fra før av, begge billige, og tenkte at den beste måten å vite om en skjerm var tynn nok var å demontere den og sjekke. Siden min BenQ-skjerm hadde bedre svartnivå enn den enda billigere AOC-skjermen, ofret jeg den. Å demontere skjermen var det andre jeg gjorde sånn at jeg fant ut hvor tynn hele konstruksjonen kunne bli. En monitor er typisk også mindre utsatt for screen burn-in.

![BenQ 24" LED GW2470H](/assets/smartspeil-maskinvare/benq_screen.jpg)

_Illustrasjon fra [Komplett](https://komplett.no) av hvordan BenQ-skjermen ser ut_

BenQ skjermen hadde en lysstyrke på 250 cd/m². Siden jeg forestilte meg å bare vise hvit tekst og hadde lagt penger i et speil med relativt god gjennomsiktighet satset jeg på at den var lyssterk nok.

#### Demontering av skjerm

Siden min skjerm hadde et buet plastpanel på baksiden var den tykk. Først skrudde jeg av foten. Så lirket jeg av plastikkpanelet bak på skjermen. Da var den eneste plastikken igjen en svart ramme i kanten foran på skjermen. Det er viktig å få skjermen så tett innpå speilet som mulig slik at man ikke ser skjermbildet dobbelt, så plastrammen foran på skjermen tok jeg også av. Alle knappene til skjermen satt på et langt tynt kort (se bilde), og kortet dro jeg enkelt opp fra rammen. Med en kniv klarte jeg å jekke av rammen som satt rundt fronten av skjermen. På baksiden av skjermen var det nå en firkantet metallkonstruksjon.

![Disassemble screen 1](/assets/smartspeil-maskinvare/disassemble_screen_1.jpg)

Originalt tenkte jeg ikke demontere skjermen mer, men siden jeg så mitt snitt til å få et enda tynnere smartspeil gjorde jeg det likevel.

![Disassemble screen 2](/assets/smartspeil-maskinvare/disassemble_screen_2.jpg)

I metallfirkanten befant det seg to kretskort. Kretskortene ble skrudd ut uten at jeg trengte å fjerne noen ledninger.

![Disassemble screen 3](/assets/smartspeil-maskinvare/disassemble_screen_3.jpg)

I bilde over ser vi skjermen ferdig demontert. Siden jeg nå kunne plassere kretskortene ved siden av skjermen i stedet for oppå, ville skjermen kunne bli så tynn som 3cm.

## Montering

På dette tidspunktet hadde jeg alle delene jeg trengte for å starte: en demontert skjerm, ramme, speil og noen planker.

La oss teste at speilet og ramma passer sammen!

![Testing the mirror inside the frame](/assets/smartspeil-maskinvare/test_mirror_in_frame.jpg)

Ramma var to millimeter lenger og bredere enn speilet, så speilet passet fint oppi. Legg merke til at du kan se mønsteret på dyna gjennom speilet.

Neste steg var å få på plass skjermen; det var to kretskort jeg måtte gjøre noe med. For å unngå å lime rett på kretskortet (selv om det ikke er noe galt i det så lenge man vet at limet er riktig) bestemte jeg meg for å skru på kretskortene på en tynn treplate som jeg først dekket med elektrisk teip.

![Plank covered in electric tape](/assets/smartspeil-maskinvare/plank_electric_tape.jpg)

![Screen still works after disassemblying](/assets/smartspeil-maskinvare/screen_still_works.jpg)

Etter å ha festet kretskortene på platen funket fortsatt skjermen! Alltid nervepirrende å sjekke om man har ødelagt noe.

Det siste jeg ville gjøre med skjermen var å teipe kantene som var av metall med den elektriske teipen. Det ville beskytte mot å ripe glasset samtidig som det gjorde kanten svart.

![Tape on the screen edge](/assets/smartspeil-maskinvare/tape_screen_edges.jpg)

Og da var jeg klar til å teste skjermen sammen med ramma og speilet:

![Screen, frame and mirror test](/assets/smartspeil-maskinvare/screen_frame_mirror_test.jpg)

Begynner å ligne på noe 😍

For å være sikker på at forholdet mellom lys og mørke er det beste velger noen å bygge en bakside på rammen slik at hele konstruksjonen blir en (lystett) boks, mens andre fester svarte materialer bak eller rett på speilet. Jeg gikk på Clas Ohlson og fant noe som heter [D-C-Fix dekorplast](https://www.clasohlson.com/no/D-C-Fix-dekorplast/p/40-6089) i fargen "Tre svart". Jeg mistenkte at den var helfarget svart på baksiden, som viste seg å stemme. Den fester seg selv og skal forhåpentligvis kunne fjernes igjen også uten å legge igjen for mye lim. Til meg selv i fremtiden: har sett at det er lett å fjerne hvis man bruker hårføner når man drar av, og limet skal kunne tas vekk med vann. Også bra å at jeg har et speil av glass i tilfelle jeg må skrape litt. I bildet under har jeg lagt på D-C Fix på speilet med en plass til skjermen:

![D-C Fix applied to the mirror](/assets/smartspeil-maskinvare/d-c_fix_applied.jpg)

Jeg borret noen bittesmå luftehull i ramma på toppen og bunnen. I tillegg visste jeg at veggen jeg hang speilet på hadde riller som også ville lufte. Jeg hadde en versjon av Raspberry Pi som kunne bli varm.

![Air holes in the frame](/assets/smartspeil-maskinvare/air_holes.jpg)

For å holde speilet og skjermen på plass i rammen (så de ikke veltet bakover) skjærte jeg til to planker. Her ser man den som sitter nederst:

![Plank to hold mirror and screen](/assets/smartspeil-maskinvare/plank_to_hold_mirror_and_screen.jpg)

Mellom planken og det under brukte jeg noe skumgummi-lignende materiale som jeg stjal fra søpla til de jeg bor med.

![Foam to hold mirror and screen](/assets/smartspeil-maskinvare/foam_to_hold_mirror_and_screen.jpg)

Legg også merke til at jeg forsterket ramma ved å skru inn vinkeljern i alle hjørnene. Speilet veide en del kilo og jeg stolte ikke på at stiftene og limet som var i ramma fra før ville holde. Før jeg skrudde inn begge plankene bak speilet passet jeg på at raden med knapper fra skjermen stakk ut nederst.

På dette tidspunktet (med begge plankene bak skrudd inn) kunne jeg snu speilet igjen.

![First test no screen](/assets/smartspeil-maskinvare/first_test_no_screen.jpg)

Jeg bestemte meg for å teste om skjermen fortsatt fungerte og hvordan det ville se ut.

![First test NRK](/assets/smartspeil-maskinvare/first_test_nrk.jpg)

![First test black screen](/assets/smartspeil-maskinvare/first_test_black_screen.jpg)

Skjermen fungerte! Først hadde jeg plassert skjermen helt nederst i venstre hjørne, og dette fikset jeg raskt med å fylle på med skumgummi før jeg tok bildene over.

![First test screen bleeding](/assets/smartspeil-maskinvare/first_test_screen_bleeding.jpg)

Fra siden er det litt bleeding fra skjermen som man best ser på kanten på senga. Å få vekk alt er umulig uten OLED, men det er veldig mye dyrere. Sett forfra legger man ikke merke til det, så jeg var veldig fornøyd. Egentlig overrasket over hvor bra dette så ut!

Det jeg gjorde deretter, var å lime fast brettet med kretskortene på speilet (altså oppå dekorplasten). Så limte jeg fast Raspberry Pi. Og da oppdaget jeg at jeg hadde glemt å lage et innsøkk til ledningene, som jeg da gjorde og egentlig burde gjort før jeg limte fast ting. Jeg hadde også kjøp et kamera til Raspberry Pi som jeg lagde et hull til i dekorplasten og limte fast.

![Finished backside](/assets/smartspeil-maskinvare/finished_backside.jpg)

I bilde over ser vi den ferdige baksiden av smartspeilet. Raden med knapper til skjermen teipet jeg i første omgang fast nederst. Opphenget jeg gikk for var `Triangelkrok Large - 5-pack` fra BGA Fotobutikk som hang på x-krok med dobbel (to) spiker. Jeg teipet ledninger på kryss og tvers så de holdt seg på plass. Ellers kan man legge merke til at siden konstruksjonen bare er 5 cm tykk fikk jeg ikke plass til en skjøteledning inni ramma. Det kommer to strømledninger ut fra speilet.

Og her kommer endelig bilder av smartspeilet hengt opp i all sin prakt i gangen, med programvaren [Magic Mirror](https://magicmirror.builders/) kjørende.

![Finished front side](/assets/smartspeil-maskinvare/finished_front_angle.jpg)

![Finished right angle](/assets/smartspeil-maskinvare/finished_right_angle.jpg)

![Finished left angle](/assets/smartspeil-maskinvare/finished_left_angle.jpg)

Kanskje jeg skriver en del 2 om programvare og muligheter for smartspeilet senere. Takk for følget!

[1]: https://nrkbeta.no/2017/02/08/slik-bygde-vi-et-magisk-smart-speil/
[2]: https://grensesnittet.computas.com/smartspeil-uten-kanter/
[3]: https://www.kode24.no/guider/slik-bygger-du-et-smartspeil/70550032
[4]: https://www.bouvet.no/bouvet-deler/utbrudd/magic-mirror-version-1
[5]: https://www.twowaymirrors.com/diy-smart-mirror/
[6]: https://www.pilkington.com/nb-no/no/produkter/funksjonsglass/spesialglass/pilkington-mirroview

---
_Sist oppdatert: 11.04.20_

Kommentarer eller spørsmål? [Lag en issue på Github!](https://github.com/Sti2nd/sti2nd.github.io/issues)
