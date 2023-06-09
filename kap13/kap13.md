# 13. Softwarearkitektur
Systemer har det med tiden at udvikle sig i omfang og kompleksitet. Tag eksempelvis fysikmotoren, Unreal Engine, der vurderes at fylde et par millioner linjers kode, eller styresystemet, Android, som i dag vurderes at være oppe på 13-15 millioner linjers kode. Begge systemer har hundreder eller tusinder af udviklere bag. For at skabe struktur og systematik samt et fællessprog til at beskrive systemet overordnede rammer, er der brug for at inddrage softwarearkitektur. 

Softwarearkitektur definerer en grundlæggende organisering af et system og dets opførsel herunder hvordan de enkelte komponenter i systemet er samlet samt deres forhold til hinanden og kommunikationen mellem dem.

Softwarearkitektur er et slags "blueprint" for hvorledes systemet er opbygget. 
Den danner derudover udviklingsgrundlaget for programmørerne, testerne, designerne osv, så de ved hvad der skal laves hvornår og i overordnet termer hvordan.  
Samtidig inddrager og afbalancerer den projektets forskellige aktørers behov og ønsker samt hvorledes holdet bag udviklingen organiseres.

Det er med andre ord en ekstremt vigtig del i udviklingen af større og mere komplekse systemer. 

I det følgende gennemgår vi en række forskellige modeller til at konceptualisere og visualisere systemarkitektur. Det giver et bedre grundlag til at forstå hvorledes et system bør opbygges og belyser noget af den tavse viden og kompleksitet, som ligger gemt i systemer af en vis størrelse.

## Master-slave eller klient-server arkitektur - n-tier model

## Tre-lags-arkitektur
Tre-lags-arkitektur er en ret simpel struktur, der inddeler et system i tre lag: 
- Et præsentationslag hvis primære opgave at give brugeren af programmet en forståelig og tilgængelig grænseflade, som programmet er opbygget af.
- Et applikationslag, der står for at koordinere og håndtere brugerens interaktion i præsentationslaget med det underliggende datalag. 
- Et datalag hvor data knyttet til systemet er gemt og dets opgave er at bistå applikationslaget i at sende relevante data og information. 

Præsentationslaget kommunikerer med datalaget igennem applikationslaget og aldrig direkte. Herved separeres programlogik fra data og brugergrænseflade. Skal der ændres i nogle af lagene kan det i højere grad gøres uafhængig af de andre lag.
Tre-lags-arkitektur kan bruges med stort set alle tænkelige systemer, som en grundlæggende arkitektur. Eksempelvis et website, hvor man klikker på en knap, der så kalder noget kode i applikationslaget, som henter nogle data frem, der så sendes tilbage til brugergrænsefladen og vises på sitet.

## UML-diagrammer
UML står for Unified Modelling Language og er et diagramsprog til modellering af ens systemer. 
Det giver en fælles forståelsesramme og sprog til at kommunikere funktionalitet og arkitektur ud på tværs af teknologi og sprog. 

UML omfatter mange forskellige diagramtyper og man kunne skrive lange bøger om UMLs forskellige strukturer. I det følgende vil vi introducere nogle klassediagrammer, som er centrale i forhold til at visualisere og illustrere objektorienteret arkitekturer. Det skal understreges, at UML er ekstremt omfattende og man kunne fylde flere bøger alene om UML, men her berøres kun hvad der er essentielt i forhold modellering af klasser og deres overordnede relationer til hinanden.

### Klassediagrammer
Et klassediagram kan betragtes som en visuel repræsentant for et objekt. Man tegner et rektangel med 3 under-inddelinger bestående af:
-Navn: Klassenavnet
-Attributter: De feltvariable som er knyttet til klassen. 
-Metoder: De operationer/funktioner som er implementeret i klassen. Typisk opererere de på attributterne. 
Herunder et eksempel på et generisk klassediagram:
![Klassediagram](../kap13/images/klassediagram.png)

Modifikatorer som prefix for attributter og operationer indikerer synligheden af disse. F.eks. betegner et "+", at metoderne eller attributterne er offentlige. Dvs. tilgængelig for andre klasser og "-" betegner at klassen er privat. Man kan også indikerer med en hashtag, at attributten er beskyttet/protected. Dvs. kun tilgængelig for  børn af den definerende klasse.

Herunder et eksempel på et klassediagram hvor det er illustreret hvordan man signalere synligheden af attributter og metoder:

![Udvidet klassediagram](../kap13/images/udvidetklassediagram.png)

Generelt kan det variere hvor mange detaljer man ønsker at give sine klassediagrammer. Man kan typisk skelne mellem tre niveauer:

- Konceptuelt niveau hvor kun navnet på klassen angives
- Specifikationsniveau hvor klassens navn, metoder og attributter samt deres tilgængelige er inkluderet
- Implementeringsniveau hvor man også angiver typerne på attributterne og typer til parametre for de angivne metoder/operationer. Man sætter et ":" hvor typen indikeres. 
  
Det afhænger bl.a. af målgruppen hvilket niveau af detaljeringsgrad man vælger, men også hvor omfangsrigt projektet er. 

Klassediagrammer kan sammensættes og man kan med forskellige relationer illustrere hvorledes de er forbundet. 
Herunder et eksempel:

![Klassediagrammer](../kap13/images/udvidetklassediagram.png)

Som det bemærkes kan et klasser have forskellige relationer til hinanden. 

Herunder en oversigt over nogle af vigtigste mulige relationer man kan sætte mellem klasser. Vi vælger at bruge de engelske betegnelser, så det er nemmere at slå op. For en fuldstændig oversigt bedes man konfererere med referencemanualen til UML.

![Relationer mellem klassediagrammer](../kap13/images/relationerdiagrammer.png)

### Tilstandsdiagrammer
Tilstandsdiagrammer beskriver forskellige tilstande, som programmet kan være i og hvordan man bevæger sig fra en tilstand til en anden.
De kan bruges til at modellere et system eller en klasses adfærd. 

Der findes forskellige variationer over tilstandsdiagrammer og hvordan de tegnes, men i praksis skelner vi overordnet mellem to slags tilstandsdiagrammer:

1. Adfærds-tilstandsdiagram: Som beskriver adfærden  af et element i systemet. Det kan i princippet også være hele systemet. Det bruges til at repræsentere en konkret implementation af et system. 
2. Protokol-tilstandsdiagram: Beskriver adfærden af en protokol, som betegner et sæt af regler, der beskriver systemets adfærd. De repræsenterer en specifik implementation af et element i systemet. 
   
Herunder to eksempler tilstandsdigrammer. Først et meget simpel et der beskriver tilstandene for en dør, som kan være åben eller lukket samt pile, der illustrerer en transition:
![Tilstandsdiagram for en dør](../kap13/images/statediagram0.png)

I objekt-orienteret forstand kan man tænke på tilstande, som nogle af de data, der er knyttet til objekt, mens objekets metoder er transitionerne, der ændre på de mulige tilstande. 

Herunder et mere komplekst eksempel på et tilstandsdiagram: 
![Tilstandsdiagram for en opvarmningsproces](../kap13/images/statediagram1.png)
Diagrammet illustrerer, at en tilstand kan have forgrenet tilstande. Her handler det om at når man vil varme noget op i en ovn eller lignende, så vil man muligvis først skulle aktivere ovnen for derefter at kategorisere den som aktiv. 


### Use-case-diagrammer
Et use case-diagram illustrerer på et overordnet niveau forholdet mellem forskellige brugsscenarier, aktører/ og systemer. De fortæller ikke noget om rækkefølgen som funktioner/sekvenser udføres i.
Use-case-diagram kan illustrere hvorledes bruger og system interagerer med hinanden, definere og organisere funktionelle krav i systemet samt angive konteksten og kravene til systemet

Use cases er repræsenteret med en mærket oval form. Pindefigurer repræsenterer aktører i processen, og aktørens deltagelse i systemet modelleres med en linje mellem aktør og use case. For at skildre systemgrænsen skal du tegne en boks rundt om selve use casen. Herunder er de enkelte komponenter i et use-case-diagram illustreret
Herunder et eksempel på et use-case-diagram:
![Elementer i et use-case-diagram](../kap13/images/usecasesymbols.png)

Herefter et eksempel på et use-case-diagram, hvor vi benytter figurerne til at lave et simpelt use-case-diagram:
![Et eksempel på et use-case-diagram](../kap13/images/usecasediagramexample.png)

### Sekvensdiagrammer
Ulemperne ved use-case-diagrammer er, at de ikke er specielt detaljeret i fht at modellere logikken i en mere sofistikeret procedure eller funktion, og de giver heller ikke noget billede af hvilken rækkefølge objekter interagerer med hinanden. 
Sekvensdiagrammer har tilformål at komme disse mangler til livs. 
De beskriver rækkefølgen og mere detaljeret hvorledes objekter og komponenter i et sytem  interagerer med hinanden i fht at afslutte en proces. På den måde giver de et mere detaljeret billede af hvorledes systemet implementeres eller hvorledes fremtidig funktionalitet bør konstrueres.  
Herunder ses et generisk eksempel på et sekvensdiagram til at beskrive en generisk interaktion mellem først to efter følgende tre objekter
![Et generisk eksempel på et sekvensdiagram mellem to objekter](../kap13/images/sequencediagram0.png)
Objekterne er identificeret ved kassogrammerne for oven. 
De lodrette søjler markerer er såkaldte aktiveringsfelter, som indikerer at både "Message Caller" og "Message Receiver" er aktive. 
Beskeden, der bliver sendt mellem de to objekter, er markeret med pilen og en tekst, som beskriver beskedens indhold. Beskeder kan gå i vilkårlige retninger
Man behøver ikke skrive andet end titlen på beskeden men den samlede signatur er givet ved: 
<center>attribute = message_name (arguments): return_type</center>  

Et objekt kan sende en returbesked, der signalerer, at modtageren er færdig med at processere beskeden:

![Asynkron returbesked](../kap13/images/sequencediagram2.png)

Man skelner mellem to typer beskeder. Synkrone (hele pile) og asynkrone (stiplede pile). Sidstnævnte betyder, at afsenderen ikke venter på, at høre fra modtageren men at afsenderen godt kan finde på at sende beskeder til andre objekter. 
Ved synkrone beskeder ventes på at modtageren sender signal om at beskeden er modtaget inden processen fortsættes.  

Herunder ses tre objekter, der interagerer med hinanden: 

![Et generisk eksempel på et sekvensdiagram mellem tre objekter](../kap13/images/sequencediagram.jpg)

Herunder eksempler på hvorledes sekvensdiagrammer kan bruges i praksis:

![Et eksempel på anvendelse af sekvensdiagrammer](../kap13/images/sequencediagramapplied0.jpg)

Bemærk at eksemplet illustrer, at man kan vælge at tegne en tændstikfigur for en aktør. Det indikerer, at der er knyttet en særlig use-case til sekvensdiagrammet. 

![Endnu et eksempel på anvendelse af sekvensdiagrammer](../kap13/images/sequencediagramapplied1.jpg)

## C4-model
En mere moderne og forenklet tilgang til  beskrivelse og visualisering af en  softwarearkitektur på er ved brug af den såkaldte C4-model, som har fokus på abstraktioner først. Man kan tænke på C4 lidt som at læse et kort over et landskab. Man forestiller sig mao at vores system som et kort over en række delkomponenter som på den eller anden måde interagerer eller relaterer sig til hinanden. 

Ofte når vi navigerer et  ukendt sted, så navigerer vi ved at orientere os ud fra bestemte steder og lidt på samme måde fungerer det når vi skal forholde os til komplekse softwaresystemer. Vi starter med at forstå en del og ligesom ringe i vandet udvider vi vores forståelse og horisont.  

I C4-modellen starter vi med at placere systemet på et slags verdenskort, hvor vi kan se hvorledes vores land er placeret i forhold til andre lande. Tænker vi på landet som vores it-system, så handler det om at orientere sig mod hvordan  det interagerer og relaterer sig til omkringliggende systemer. Er vi eksempelvis ved at lave et it-system til skoler, så vil det system typisk interagere med andre offentlige systemer.   

Dernæst zoomer vi ind på landet og kigger på de enkelte regioner og byer. Vi kan zoome mere og mere ind til vi kommer til det område, som vi befinder os i. 

Herefter kan vi vælge at zoome endnu mere ind og se hvordan de enkelte byer eller komponenter er konstrueret. 

C4-modellen består, som navnet antyder, af fire lag, der alle er navngivet med `C` som første bogstav. Vi tillader os dog at nævne de danske oversættelser i parenteser: Context (kontekst), Container (container), Component (komponent) og Code (kode).

### C4 eksemplificeret
Herunder eksemplificeres C4-modellen fire niveau ved at præsentere et internet bank-system. 
Det er vigtigt at understrege, at der findes ikke en entydig optimal løsning. Forskellige personer vil designe systemet vidt forskelligt. Men ideen med C4 handler i lige så høj grad om at give et fælles (visuelt) sprog mellem softwarearkitekter, programmører og testere m.fl. til at forstå hvorledes systemet grundlæggende er opbygget.  

#### Niveau 1: Kontekst/context
Niveau 1 giver det overordnede overblik. Menneskefiguren symboliserer brugeren. De grå felter er nogle af de centrale systemer, som systemet interagerer. Pilene beskriver flowet i data og hvorledes de enkelte dele (også kaldet "container" her) interagerer. Hver del kan beskrives med nogle få linjers tekst. 
![C4-model Kontekst-niveau (1): ](../kap13/images/c41.png)

#### Niveau 2: Container
Efterfølgende kan vi zoome ind på de enkelte dele. Til at starte med zoomer vi ind på en `container`. En container repræsenterer et system/program eller en database. Den skal køre for at det samlede system kører. Bemærk de stiplede linjer, som markerer bank-systemet fra forrige niveau.  
![C4-model container-niveau (2): ](../kap13/images/c42.png)

#### Niveau 3: Komponent/Component
Herefter kan vi zooome ind på de enkelte container. Nedenfor er zoomet ind på containeren ved navn `API Application`. Vi skal tænke på et komponent som en samling af beslægtet og veldefineret funktionalitet, der typisk kan kaldes igennem en veldefineret grænseflade. 
![C4-model Komponent-niveau (3): ](../kap13/images/c43.png)

#### Niveau 4: Kode/code
Endelig kan vi zoome yderligere ind på de enkelte komponenter og få visualiseret komponentet ved brug af et klassediagram, use-case-diagrammer eller noget helt tredje:
![C4-model Klassediagram-niveau (4): ](../kap13/images/c44.png)


Det bemærkes, at I takt med at vi kommer længere og længere ned C4-modellen, så kommer vi stadig tættere på koden og relationerne bliver beskrevet mere kodenært. 

#### Symboler og figurer brugt i C4
Herunder forslag til hvilke figurer man kan overveje at bruge til at visualisere og repræsentere de enkelte dele i C4. Det er ikke nødvendigvis afgørende, at man præcis bruger disse figurer, men vigtigere at man i teamet bliver enige om hvilke figurer, der repræsenterer hvilke niveauer og komponenter. 

![C4-model Figurer: ](../kap13/images/c45.png)

En af de helt klare styrker ved modellen er, at den giver mulighed for at fortælle forskellige historier afhængig af målgruppen og deres tekniske indsigt. 
Samtidig er den visuelt orienteret og det giver for mange ofte et bedre og mere tilgængeligt overblik over systemets enkelte del samt hvorledes de er forbundet. 

## Øvelser

1. Konstruer en trelagsmodel for et brætspil. Beskriv i overordnede termer hvad de tre lag dækker over. 
2. Konstruer en trelagsmodel for en app, der skal kunne tage billeder og gemme det i skyen.
3. Lav et klassediagram for et DyrePatient til at håndtere dyr i et dyrehospital. Identificer mindst 3 attributter og 3 metoder, som kunne være relevante at inddrage i en sådan klasse. 
4. Konstruer nu børneklasser som udvider den oprindelig klasse, der repræsenterer fordi dyrearter. Det kan eksempelvis være konkrete dyr men også dyr eller arter eller hvorvidt de kan flyve, svømme eller være på land. Kategoriseringen er op til dig. Identificer mindst 3 attributter og 3 metoder, som kunne være relevante at inddrage i disse klasser, som adskiller sig for de andre. 
5. I det følgende ønske et design for en online bogbutik. Overvej relevante klasser herunder metoder og attributter samt deres relationer til hinanden. Visualiser disse ved brug af klassediagrammer. 
6. Lav klassediagramer over et system, som skal håndtere elever, klasser, lærere, administration/IT og klasselokaler. Systemet skal håndtere karakterer, skema, timer m.m.
7. Lav klassediagrammer over et computerspil (eksisterende eller fiktivt)
8. Konstruer de tre øverste lag i C4-modellen over en online pizzabutik kaldet MustEat, der skal understøtte muligheden for at kunder kan bestille pizzaer fra en menu over nettet.
9. Konstruer de tre øverste lag i C4-modellen for NetFix, som skal være en streamingkanal. 
10. Konstruer alle fire lag i en C4-model herunder relevante klassediagrammer i kodelaget til en app, der skal facilitere, at man kan sende penge til hinanden og betale regninger
11. Konstruer alle fire lag i en C4-model herunder relevante klassediagrammer i kodelaget til et nyt social medie.