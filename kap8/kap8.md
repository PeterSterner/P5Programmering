# 8. Objekter

Et vigtigt begreb i programmering og softwareudvikling i det hele taget er de såkaldte "objekter", som vi vil introducerer i nærværende afsnit. De spiller en central rolle i  objekt-orienteret programmering (forkortet OOP), som vel nok er den mest anvendte tilgang af professionelle programmører og softwareudviklere. 

Kort fortalt betragtes verdenen i OOP som opbygget af objekter. Objekter kan være alt muligt fra mennesker, dyr til ting osv. Grundlæggende gælder det for alle objekter, at de har to begreber knyttet til sig:
1. Attributter: Der beskriver objektets nuværende tilstand. 
2. Metoder: Dvs. en form for funktioner, der kan ændre på objektets nuværende tilstand. 
   
Objekter indkapsler med andre ord data og funktioner. Man kan tænke på dem som nogle containere, der ikke bare rummer statistiske værdier men også metoder til at ændre på disse værdier. Objekter kan have relationer til hinanden, de kan interagere med hinanden og ændre på hinandens tilstande. Herunder en figur der illustrerer det overordnede klassebegreb som en kapsel, der rummer metoder(eller adfærd) og variabler (eller data/attributter):
![En klasse som en kapsel ](../kap8/images/kapsel.png) 

En klasse kan også modelleres efter et såkaldt klassediagram, som er en nem måde at skabe et overblik over klassens funktionalitet:

![En klasse som en kapsel ](../kap8/images/class.png) 

Som vi skal se i senere kapitler kan man tilføje rigtig megen information omkring en klasses metoder og attributter. I det følgende vil diagrammet blive brugt til at give en mere visuel repræsentation af klassebegrebet, og i takt med at vi udvider vores forståelse tilføjer vi flere informationer.  

I praksis kan OOP bruges bl.a. til at sikre, at man bedre kan håndtere, overskue og implementere den enorme og stadigt voksende kompleksitet i programmer og systemer. Brugt rigtigt giver de ligesom funktioner pænere løsninger, der er nemmere at forstå, nemmere at udvide og modificere men også i højere grad at genbruge. 

Til at starte med har vi fokus på at få en fornemmelse for hvordan et objekt konstrueres og hvad de kan bruges til herunder hvorledes vi tilføjer data og metoder samt benytter dem i praksis. 

## Oprette en klasse som skabelon for et objekt 
I Javascript konstrueres et objekt vha af nøgleordet “class”. Vi vil tillade at bruge klasse i stedet for class, når vi omtaler dem. Når man opretter en klasse konstrueres en datastruktur, der rummer både data eller egenskaber om det objekt, som klassen er en skabelon for, men også metoder (eller funktioner), der ændrer på objektets tilstand. 

Vi konstruerer en klasse ved at skrive `class` efterfulgt af navnet på klassen. Navnet skal være i et ord. Herefter følger kroppen omkrænset af en start og slut krølparentes:
```javascript

class "KlasseNavn"
{


}
```
Klassen er vores skabelon, som kan bruges til at konstruere eller med et fint ord "instantiere" objekter af denne skabelon. Dvs. objekter er med andre ord konstrueret ud fra vores skabelon. 

## Klassens konstruktør initialiserer objektet
Når vi opretter et objekt dvs. en instans af klassen er vi typisk interesseret i at indlæse nogle grundlæggende egenskaber fra start af. Det gør vi ved brug af en såkaldt "konstruktør", som er en funktion eller metode, der har til formål at sætte nogle bestemte værdier på forhånd for den konkrete instans af klassen. I JS bruges nøgleordet `constructor` (eller konstruktør på dansk). Herunder et eksempel på en klasse som ingen argumenter tager og heller ingen værdier sætter i konstruktøren:  

```javascript
class "KlasseNavn"
{
  constructor()
  {

  }
}
```

## Multiple konstruktører og klassens attributter
Modsat mange andre sprog, så understøtter Javascript som udgangspunkt kun en konstruktør uden mulighed for at `overloade` denne. Med dette skal forstås, at I mange andre sprog kan man faktisk lave flere konstruktører og skelne mellem de enkelte ved at have forskellige antal argumenter til konstruktøren. Dette lader sig ikke umiddelbart gøre i Javascript, men man kan i stedet gøre brug af et mindre "hack", hvor man bruger standardværdier, og på den måde opnår nogenlunde samme funktionalitet i praksis.

Herunder et eksempel på ovenstående hvor vi har lavet en konstruktør, der har mulighed for at tage ingen eller op til n parametre med angivet ved p1,..,pn :

```javascript
class "KlasseNavn"
{
  constructor(p1='',p2='',...,pn='')
  {
    this.p1 = p1
    this.p2 = p2
    ...
    this.pn = pn

  }
}
```
Ved at sætte p1,...,pn til en tom streng giver vi mulighed for at konstruktøren kan tage op til n-argumenter. De kan initialiseres eller undlades at initialiseres fuldstændig. Hvis vi initialiserer dem til andre værdier end de prædefineret, tildeles variablerne i kroppen af konstruktøren den/de ønskede værdi(er). Alternativt sætter Javascript blot disse attributter til den tomme streng. 

Variablerne i konstruktøren kaldes som tidligere nævnt også for `attributter`. Og som angivet ovenfor er det vigtigt at understrege, at selvom konstruktørens parametre har samme navne som attributterne, så er der tale om to forskellige ting.

Brugen af `this.p1 = p1`,..., `this.pn = pn` betyder, at vi knytter argumenterne givet i konstruktøren som attributter til det konkrete objekt, som klassen er en skabelon for.
`this` refererer altså til den konkrete instans af klassen eller objektet.


## Eksempel på en klasse: Cirkel
Lad os prøve at konkretisere ovenstående ved at lave en klasse for cirkler. Vi starter med at visualisere den i et klassediagram:
![En klasse for en cirkel](../kap8/images/classcircle.drawio.png) 

Til at starte med rummer klassen kun attributter, der skal beskrive cirklen. Vi skal senere udvide med metoder. 

En skabelon eller mere præcist en klasse for en cirkel kunne se således ud, men det er vigtigt at understrege, at den kunne se ud på mange forskellige måder: 	

```javascript
class Cirkel{
 constructor() {
   this.color = color(255);
   this.xpos = width/2; 
   this.ypos = height/2;
   this.radius = 1;
  }
}
```
Her angiver farve, position og radius nogle egenskaber ved en cirkel. De to variable `width`og `heigth` er prædefineret variable i P5. 

I det følgende har vi tilføjet konstruktøren, som vores første metode:

![En klasse for en cirkel med konstruktør](../kap8/images/classcircleconstructor.drawio.png) 

Konstruktøren kan betragtes som klassens første og meget vigtige metode, da den konstruerer klassen som objekt og initialiserer attributterne. Den første konstruktør tager ingen parametre, men i praksis vil det dog være rart selv at kunne bestemme værdierne, da de naturligvis varierer
fra cirkel til cirkel. I det følgende ændres koden, så værdierne gives med i konstruktøren:

```javascript
class Cirkel{
 constructor(colorcode=255,xpos = width/2,ypos = height/2,radius = 1 ) {
   this.color = color(colorcode);
   this.xpos = xpos; 
   this.ypos = ypos;
   this.radius = radius;
  }
}
```
Herunder et klassediagram der illustrer ovenstående: 
![En klasse for en cirkel med konstruktør](../kap8/images/classcircleconstructorparam.drawio.png) 

Hvis vi ikke angiver andet i konstruktøren, så vil de angivne variabler blive initialiseret med de samme værdier som i den foregående konstruktør. Meget vigtigt at gøre opmærksom på i denne sammenhæng er dog, at konstruktøren forventer at få argumenterne i den anviste rækkefølge, når vi opretter en konkret instans af klassen. Det vender vi tilbage til om lidt.

Hvert objekt er en cirkel, som skal kunne have forskellige egenskaber. Ved at bruge `this` får vi mulighed for at opbevare forskellige attributter hos de respektive cirkler. Igen er det en god ide at tænke på objekter som containere, der indeholder forskellige værdier.

## Oprette et objekt eller instans af klassen med nøgleordet `new`
Vi kan nu oprette objekter vha. af vores klasse. Det gør vi ved brug af nøgleordet `new`:
```javascript
let V = new K(A)
```
Variablenavnet er repræsenteret ved "V" og skal erstattes af et sigende navn/forkortelse for den klasse, som vi opretter en instans af. "K" repræsenterer klassens navn, og A betegner en eller flere attributter (adskilt af komma), som man kan give med til konstruktøren. 

Herunder et eksempel der forhåbentlig giver en bedre forståelse end den generelle definition:

```javascript
let c1;
let c2;
function setup() {
  createCanvas(400, 400);
  c1 = new Cirkel(); //vi opretter et nyt cirkel-objekt vha new (standard værdier for cirklen indlæses som attributter)
  c2 = new Cirkel(255,100,100,20); //vi opretter et nyt cirkel-objekt vha new (colorcode = 255, x = 100, y= 100, radius = 20) 
}
```
Vi har oprettet to forskellige cirkel-objekter med de to forskellige kald til den samme konstruktør her og gemt referencer til dem i de to variabler c1 og c2. Variablernes type er af typen "Cirkel". Vi har med andre ord konstrueret vores helt egen type. Vi bemærk i øvrigt, at variablerne i virkeligheden blot peger på en adresse til de to objekter. Det er netop det vi forsøger at indikere, når vi taler om "referencer". Herunder en illustration af ovenstående kode:

![En cirkel og instanser af denne](../kap8/images/circleinstance.drawio.png) 

## Rækkefølgen af argumenter til konstruktøren
Endelig gør vi, som vi nævnte før, opmærksom på at ved at bruge standard værdier til at rumme forskellige antal argumenter til  konstruktørerne, er vi tvunget til at overholde rækkefølgen i argumenterne. Eksempelvis kunne man forestille sig følgende instantiering:
```javascript
c3 = new Cirkel(100,100,20)
```
 
Umiddelbart ville man tror det var en cirkel magen til referencen i `c2` men i praksis er det en cirkel med farvekoden `100` og centrum i `(x,y)=(100,20)` og radius `1`. Man skal med andre ord være opmærksom på rækkefølgen af ens argumenter/parametre i konstruktøren er overholdt ellers risikerer man at blande "æbler og bananer". 

I den forbindelse bør man derfor være meget bevidst om hvilke attributter, som man i en instantiering har brug for at indlæse versus hvilke som altid kan justeres undervejs. 
Tænkes eksempelvis på en cirkel kunne man spørge sig selv, hvad er det der gør en cirkel til en cirkel? Er det ikke i højere grad et punkt og en radius fremfor eksempelvis farvekoden? I praksis kunne man derfor overveje helt at undlade farvekoden som argument til konstruktøren. Den kan nemlig altid justeres. Herunder et eksempel på en ny klasse konstruktion:

```javascript
class Cirkel{
 constructor(x,y,r) {
   this.color = color(255); // bemærk vi har valgt at give den en prædefineret farvekode 
                            // og ikke som argument til konstruktøren 
   this.xpos = x;
   this.ypos = y;
   this.radius = r;
  }

```

## Ændre attributter efter konstruktøren er blevet kaldt
Vi kan som udgangspunkt ganske let ændre på attributternes værdier i et objekt, når vi først har instantieret det. Vi benytter følgende overordnede struktur:

```javascript
VariableObjekt.AttributNavn = NyVærdi
```

Herunder et eksempel der illustrerer hvorledes vi kan ændre en instans af cirklens attributter ovenfor:
```javascript
c = new Cirkel(100,100,20)
c.color = color(75) // ændre farvekoden for cirklen
c.xpos = 50 //ændre x-koordinatet til 50 i stedet for 100
```
I praksis anbefales derfor at justere på ikke essentielle attributter (såsom farvekoden ovenfor) på denne måde.

Vi gør desuden opmærksom på, at man også kan specificere at visse attributter er `private`. Dvs. de ikke bare lader sig ændre alle mulige steder i koder men at de skal ændres ved brug af bestemte metoder, så vi sikrer at de ændres korrekt. Det vender vi tilbage til i et senere kapitel.


## Objekters metoder
Som vi nævnte før, så rummer klasser også metoder, der kan ændre på objektets tilstand. Herunder har vi udvidet vores generelle klassedefinition med metoder. Vi skal tænke på metoder som funktioner. De kan tage et input og returnere et output. Dvs. reelt er der bare tale om funktioner, men de kaldes typisk for "metoder", når de flyttes ind i en klasse. 
Målet med metoder er typisk at ændre på et konkret objekts tilstand, som typisk er beskrevet ved dets attributter. Det kunne eksempelvis være at ændre på centrum for cirklen eller farvekoden. 

Herunder først en generisk formulering af metoder:

```javascript
class "KlasseNavn"
{
  // først konstruktøren ...
  constructor(p1='',p2='',...,pn='')
  {
    //...
  }
  // erstat selv "metode1" med et sigende navn
  // kan have ingen eller op til n parametre
  "metode1"(p11,....p1n)
  {

  }
  //...
  // erstat selv "metodeM" med et sigende navn
  // kan have ingen eller op til n parametre
  "metodeM"(pm1,....pmn)
  {

  }
}
```

I ovenstående har vi for overskuelighedens skyld givet metoderne navnene "metode1", ...,"metodeM", men i praksis bør man selvfølgelig give dem nogle sigende navne for den kontekst man arbejder med og være opmærksom på, at man navngiver metoderne på en ensartet måde. 

Vi kan have ligeså mange metoder vi ønsker, der tager lige så mange parametre som vi ønsker, og vi kan sågar have metoder ved samme navn, men i såfald vil den sidst defineret blive kaldt, hvorfor vi opfordre til at man undgår det eller løser det på samme måde som med konstruktøren, der har nogle standard værdier.  

Herunder har vi modelleret denne generelle klasse ovenfor i et generisk klassediagram:
![Et generelt klassediagram](../kap8/images/genereltklassediagram.drawio.png) 
Vi bemærker, at diagrammet er udvidet med en indikation af hvilken type attributterne har og hvilken type metoderne returnerer. Der er med andre ord mulighed for at eksplicitere. Det er ikke nødvendigvis et krav og afhænger i høj grad af hvem man kommunikerer til. Handler det om at give et overblik så kan det undlades og omvendt, hvis det er til en programmør. Vi vender tilbage til klassediagrammer i detaljer i kapitel 13. 

Lad os konkretisere brugen af metoder i vores eksempel fra før med cirklen. 
Der kan eksempelvis blive behov for at ændre på cirklens tilstand såsom at bevæge cirklen et andet sted end på skærmen samt at tegne cirklen:

```javascript
class Cirkel{
 constructor(x,y,r) {
   this.color = color(255); // bemærk vi har valgt at give den en prædefineret farvekode 
                            // og ikke som argument til konstruktøren 
   this.xpos = x;
   this.ypos = y;
   this.radius = r;
  }
  move(x,y){  //start på metoden move
    this.xpos = x;
    this.ypos = y;
  }
  draw() //start på metoden draw
  {
    ellipse(this.xpos,this.ypos,this.radius);
  }
}
```


Bemærk flere vigtige ting her: 1) Selvom metoder reelt bare er funktioner, så skriver vi ikke længere function foran, når vi implementere en metode til en klasse. 2) Metode move tager to parametre mens draw ikke tager nogle. I metoden move bliver x og y brugt til at sætte centrums koordinaterne for x og y, der betegnes med xpos og ypos. 3) I metoden draw udnytter vi, at klassen har indlejret en række egenskaber, såsom centrum for cirklen, der betegnes med xpos og ypos.

Herunder viser vi nu hvordan man kan bruge klassen til at oprette og bevæge en cirkel rundt på skærmen. Dvs. vi antager at koden ovenfor er tilføjet over funktionen setup:

```javascript
let c;
function setup() {
  createCanvas(400, 400);
  c = new Cirkel(200,200,50); //vi opretter et nyt cirkel-objekt vha new
  c.draw();
  c.move(300,300);
  c.draw();
}
```

Bemærk her særligt konstruktionen af et nyt cirkelobjekt. Vi bruger nøgleordet `new`. Vi giver den argumenterne 200, 200 og 50, som xpos, ypos og radius bliver sat til jf. klasse-definitionen.

Vi tegner herefter cirklen og flytter den til position (300,300). Afslutningsvis tegner vi den igen.

Vi kunne let konstruere lige så mange cirkler som vi nu havde lyst til og vi skal i næste afsnit se hvordan vi kan opbevare mange af de samme objekter uden at skulle konstruere tilsvarende ligeså mange variabler. Men herunder følger et eksempel hvor vi har konstrueret to cirkler og kalder deres respektive metoder:

```javascript
let c1;
let c2;
function setup() {
  createCanvas(400, 400);
  c1 = new Cirkel(200,200,50);
  c1.draw();
  c1.move(300,300);
  c1.draw();
  c2 = new Cirkel(100,100,20);
  c2.draw();
}
```
## Navngivning af klasser, metoder og attributter
For at øge læsbarheden på tværs af programmer og programmører, så anbefales det kraftigt, at man er konsekvent i sin navngivning af klasser, metoder og variable.
I JavaScript ligesom alle mulige andre sprog, er der en række konventioner, som man forslås at følge.

Når man navngiver en klasse skrives første bogstav med stort. Hvis klassens navn består af flere ord benyttes `PascalCase`. Dvs. hvert nyt ord skal starte med stort. Herunder nogle tænkte eksempler på klassenavne der illustrer ideen:

```javascript
hund = new Hund()
hundEjer = new HundEjer(hund)
p1 = new Punkt()
p2 = new Punkt()
ls = new LinjeSegment(p1,p2)
```

For navngivningen af metoder gælder, at man opfordres til at bruge at `CamelCase`, der modsat `PascalCase` tillader at det første bogstav i det første ord starter med småt. Ydermere anbefales det, at det første ord er et verbum som indikerer en handling (eller en ændring af objektets tilstand). Herunder nogle tænkte eksempler fra de ovenfor instantieret klasser:

```javascript
hundeNavn.sætNavn("Terry") //sætter hundens navn
console.log(hundEjer.hentNavn()) // printer "Tintin" ;-)
p1.sætKoordinater(2,3) //sætter koordinater for punkter
p2.sætKoordinater(7,4)
ls = new LinjeSegment(p1,p2) //konstruerer et linjesegment udfra punkterne
```

Attributter og variablenavne kan også erklæres med `CamelCase` som eksemplerne ovenfor. Man bør i øvrigt være opmærksom på at for både klasser, metoder og attributter, så gælder der, at de er "case sensitive", hvilket betyder, at Javascript skelner mellem navne/ord, hvor den eneste forskel er om et eller flere af bogstaverne er skrevet med små eller store bogstaver. 

Endelig bør man også være bevidst om, at man skriver på engelsk eller dansk. Generelt vil vi opfordre læseren til at overveje hvem målgruppen er og så i øvrigt være konsekvent og konsistent i sine valg. 

## Øvelser
Herunder følger en række øvelser. Lav som minimum øvelserne 1. til 7 samt et af projekterne.

1. Hvilke egenskaber og metoder kunne være relevante for en bil, et dyr og et selvvalgt objekt som den tredje. Giv mindst 3 metoder og 3 egenskaber for hver af de tre objekter. Overvej egenskabernes datatyper og hvordan metoderne bør kodes. Metoderne må ikke være draw.
2. Navngiv metoderne hhv. klasserne ud fra reglerne om `CamelCase` hhv. `PascalCase`.
3. Implementer en konstruktør med egenskaber og metoder for hver af de nævnte i 1.
4. Implementer en draw metode, der kan tegne de tre objekter. Metoden skal gerne inddrage nogle af de 3 egenskaber for hver af de 3 objekter. Dvs. udfaldet af draw skal gerne påvirkes af ændringer i egenskaberne. Eksempelvis kan højden på en bil ændre tegningen af bilen.
5. Vi laver i det følgende et simpelt spil kaldet “Afraid of raindrops”, hvor man i bunden har en vandret linje, som ens helt kan bevæge sig til venstre og højre på. Fra oven regner det med forskellige cirkler, der oprettes i toppen af skærmen og bevæger sig lodret ned. Cirklerne har forskellige størrelser og bevæger sig i forskellige hastigheder. Hvis ens cirkel kolliderer med ens helt, så er det gameover. Implementer en klasse for en cirkel, der håndterer forskellige størrelser, placeringer, hastigheder og kollision med ens helt. Implementer desuden, at man kan starte forfra og hold styr på antallet af cirkler, som man undgår. 
6. Forklar hvad følgende kode gør vha. kommentarer:

```javascript
let b; 

function setup() {
  createCanvas(640, 360);
  b = new Ball(); 
}

function draw() {
  background(255);
  b.update(); 
  b.display();
}
class Ball {
  constructor() {
    // vi opretter to vektorer
    this.position = new createVector(random(100), random(100));
    this.velocity = new createVector(random(1,4), random(1,5));
  }
  
  update() {
    this.position.add(this.velocity);
    
    if ((this.position.x > width) || (this.position.x < 0)) {
      this.velocity.x = this.velocity.x * -1;
    }
    if ((this.position.y > height) || (this.position.y < 0)) {
      this.velocity.y = this.velocity.y * -1;
    }
  }
  display() {
    stroke(0);
    fill(175);
    ellipse(this.position.x, this.position.y, 48, 48);
  }
}
```

6. Udvid koden i 5 med en metode, der tager en anden bold og returnerer hvorvidt de overlapper/kolliderer.
7. Udvid koden i 5. så der er fem forskellige cirkler med forskellige radier der bevæger sig rundt med forskellige hastigheder. Implementer en metode der giver point hvis der bliver trykket på cirklerne. De små og hurtigt bevægende cirkler skal give flere point.
8. Konstruer en klasse der repræsenterer en cirkel. Dvs. med attributter til at beskrive radius og placering samt metoder til at tegne og farvelægge cirklen. Udvid nu cirklen så den har en ekstra attribut, der beskriver farven af cirklen. Cirklen kan antage fem forskellige farver. Udvid draw, så den farvelægger cirklen efter den foreskrevne attribut.
9. Konstruer en løkke, der genererer 100 af de nævnte cirkler fra forrige opgave med fire tilfældige farver. Skriv nu en funktion, der tager tre parametre (se nedenfor). De fire parametre består af listen af cirkler, koordinater. Funktionen har til opgave at finde farven for den nye cirkel ved at farvelæg den med den samme farve, som den cirkel der ligger nærmest den nye cirkel.
```javascript
function knn(cirkler, x, y, r)
{

}
```
10. Udvid koden i foregående opgave, så tager en ekstra parameter kaldet K, hvor K er et naturligt tal større end 1. Farvelæg nu cirklen efter den mest forekommende farve blandt de K nærmeste naboer til cirklen. Denne algoritme kaldes KNN (K-Nærmeste-Naboer) og er en basal, men vigtig algoritme indenfor maskinelæring og kunstig intelligens.
11. Konstruer en klasse der repræsenterer en fugl og lav metoder til at animere at den flyver og den bevæger sig vandret over skærmen. Det må gerne være en meget simpel fugl.
12. Udvid med en simpel rektangulær riffel i bunden af skærmen, der skyder ellipseformede kugler af sted i den retning, der klikkes med musen.
13. Konstruer en animation vha klasser, der visualiserer en række dominobrikker der vælter fra siden. Brug simple rektangler.
14. Konstruer en klasse for en person. Klassen skal kunne tegne personen (bare en tændstiksmand). Lav metoder der kan bevæge arme og ben i stop motion stil ved at trykke på bestemte taster.
15. Udvid 7)  så man kan gå fra venstre mod højre på skærmen. Lav flere personer der går efter hinanden.
16. Lav en tændstiksmand, der kan danse nogle meget simple bevægelser vha selvvalgte taster. Brug klasser i implementeringen.
17. Lav et simpelt Pong-spil ved hjælp af klasser. En klasse til at repræsentere de to padler, som placeres i hver sin side. Bolden bevæger sig frem og tilbage, når den kolliderer med padlerne. Udvid Pong, så man kan have flere bolde i gang samtidig. Der er point til modstanderen hvis man ikke når at ramme bolden. I et af projekterne skal vi lave en kunstig intelligent modstander, så der har du også mulighed for at se hvorledes Pong kan laves. Men det er en god øvelse at lave det selv først.

## Projekt: Epidemi-simulation
Konstruér et lærred med maksimal størrelse vha. de globale variabler windowWidth og windowHeight.

Lav to globale variabler x og y. Sæt x=windowWidth/2 og y=windowHeight/2.

Lav en global variabel r og sæt den til et lille tal. F.eks. 10.

Tegn en cirkel i (x,y) med radius r. En cirkel repræsenterer et menneske i vores simulation.

Vi skal nu have mennesket til at bevæge sig:

   - Opret to globale variabler r1 og r2 og sæt dem til tal i ]0;1[.

   - I funktionen draw opdateres cirklens centrum til x=x+r1 og y=y+r2.

Kør programmet. Mennesket bevæger sig nu (desværre ud af lærred).

For at få mennesket til at bevæge sig tilbage, skal vi først tjekke om personen er på vej uden for. I draw-funktion skal du implementere følgende:

   - Hvis x-r&lt;0 er personen på vej ud til venstre for lærred. Sæt r1=- r1.

   - Hvis x+r>maxWidth er personen på vej ud til højre for lærred. Sæt r1=-r1.

   - Hvis y&lt;0 er personen  på vej ud over lærred. Sæt r2=-r2.

   - Hvis y>maxHeight er personen på vej ud under lærred. Sæt r2=-r2.

   

Nu bevæger personen sig rundt på lærred så længe, at programmet kører. Svar på følgende spørgsmål:



1. Hvorfor indgår radius r i beregningerne ovenfor?
2. Hvad sker der, hvis vi eksempelvis sætter r1 eller r2 til et større tal?
3. Hvorfor ændrer vi fortegn på retningsvektorens ene koordinat ved kollision med lærreds vægge? Vink: Forstå refleksionsloven: https://www.mathsisfun.com/physics/reflection.html

For at få flere mennesker til at bevæge sig rundt, er det en god idé at benytte datatypen “array” samt lidt objekt-orienteret programmering (OOP). Da OOP er B-niveau er det helt i orden at kopiere koden nedenfor ind øverst i script.js.


```javascript
class Menneske {
    constructor(x, y, radius, retning_x, retning_y) {
   	 this.x = x;
   	 this.y = y;
   	 this.radius = radius;
   	 this.retning_x = retning_x;
   	 this.retning_y = retning_y;
    }

    draw() {
   	 circle(this.x, this.y, this.radius*2);
    }

    collision(windowWidth, windowHeight) {
   	 if (this.x + this.radius > windowWidth) {
   		 this.retning_x = -this.retning_x;

   	 }
   	 if (this.x - this.radius <= 0) {
   		 this.retning_x = -this.retning_x;

   	 }
   	 if (this.y + this.radius > windowHeight) {
   		 this.retning_y = -this.retning_y;
   	 }
   	 if (this.y - this.radius <= 0) {
   		 this.retning_y = -this.retning_y;
   	 }
   	 this.x = this.x + this.retning_x;
   	 this.y = this.y + this.retning_y;
    }

}
```

Lav nu et globalt array, der er tomt. Kald det “mennesker”.

```javascript
let mennesker = [];
```

Opret en global variabel n og sæt den til f.eks. 500. Denne variabel betegner hvor mange mennesker, der indgår i vores simulation.

I setup-funktionen tilføjer du en for-løkke. I for-løkken skal nye menneske-objekter oprettes og tilføjes til dit array. Det gøres med new-operatoren:


```javascript
mennesker.push(new Menneske(random(0, windowWidth), random(0, windowHeight), radius, random(-5, 5), random(-5, 5)));
```

Bemærk: push-funktionen er en metode på array-objektet, der tilføjer nye elementer til arrayet. 

Random-funktionen sikrer bare, at menneskene indsættes forskellige steder på lærred og bevæger sig med forskellige hastigheder.

Tilbage er bare at konstruere en for-løkke i din draw-funktion, der tegner alle menneskene i dit array.

``` javascript
for (let i = 0; i < n; i++) {
   mennesker[i].draw();
   mennesker[i].collision(windowWidth, windowHeight);
}
```

Nu bevæger n mennesker sig rundt på lærred. Du kan nu implementere følgende funktionalitet selv:

1. Lad hvert menneske have sin egen farve ved at tilføje en farve-attribut til din constructor i Menneske-klassen og initialisere den til en bestemt farve, når du opretter et menneske.
2. Skrive kode i draw-funktionen, der afgør om et menneske kolliderer med et andet menneske. Vink: Benyt en ny for-løkke.
3. Skriv kode, der inddeler mennesker i 3 kategorier: Smittet, usmittet og raske.


## Projekt: Ping-Pong AI
I nærværende skal vi lave en kunstig intelligent modstander til Pong. Man kan vælge mange strategier. Herunder er bare nævnt nogle få stykker:
* "Løberen": Bevæger sig efter bolden.
* "Midteren": Bevæger sig ind til midten, når man har slået og bevæger sig først igen når modstanderen har slået.
* "Beregneren": Forsøger at beregne banekurven for bolden og placere sig derefter. 

Projektet er rigtig sjovt, hvis man er flere om at udvikle hver sin AI, så  man kan lade dem konkurrece mod hinanden.

Start med at danne dig et overblik over koden og forstå hvad der sker. 
Projektet er øvelse i at bruge klasser samt deres metoder og attributter. Men ydermere vil det også øve dig i at læse større mængder af eksisterende kode. Det er vigtig kompetence som programmør, da man jo sjældent starter med at udvikle noget fra bunden men i stedet ofte tager udgangspunkt i en eksisterende kodebase. 
Selve spillet og koden er vedlagt men kan også tilgås online på https://editor.p5js.org/henrik.sterner/sketches/0cVpDHzZU​

Herunder er koden for pong-spillet fordelt på flere filer. Husk at inkludere filerne i din index.html (se et eksempel til sidst):

```javascript
//ball.js: Håndtere bolden og dens fysik
class Ball
{
  constructor()
  {
    this.START_SPEED = 4;
    this.x = 200;
    this.y = 100;
    this.w = 20;
    let a = random(-PI/4,PI/4)+random([0,PI]);
    this.vx = cos(a)*this.START_SPEED;
    this.vy = sin(a)*this.START_SPEED;
    this.history=[]//contains the 25 points from the last 25 frames
  }
  
  move()
  {
    this.y +=this.vy;
    this.x +=this.vx;
  } 
  
  update()
  {
    if(this.y>=height || this.y<=0)
    {
      this.vy *= -1;
    }
    let v = createVector(this.x, this.y)
    
    if(this.history.length>25)
    {
      this.history=this.history.slice((1, 26))
    }
    this.history.push(v)

  }
  reset()
  {
    this.history = [];
    this.x = 200;
    this.y = 100;
    let a = random(-PI/4,PI/4)+random([0,PI]);
    this.vx = cos(a)*this.START_SPEED;
    this.vy = sin(a)*this.START_SPEED;
  }
  show()
  {
    fill(255);
    noStroke();
    ellipse(this.x,this.y,this.w);
  }
}
```
Herefter følger koden for den menneske paddle:

```javascript
//peddle.js håndtere at man kan bevæge paddlen med tastaturet
class Peddle
{
  constructor(side,name)
  {
    this.name = name
    this.x = this.selectPosition(side);
    this.w = 20;
    this.h = 100;
    this.y = 200//height;
    this.vy = 2;     
  }

  selectPosition(side)
  {
    if(side==="Left") return 10
    if(side==="Right") return 390
  }

  update()
  {
    if(this.y>=height-50 || this.y<=50)
    {
      this.vy *=-1;
    }
  }
  change_dir(y)
  {
    this.vy = y;
  }
  // ballx, bally er boldens nuværende postition
  // ballxspeed, ballyspeed boldens velocity 
  // history er en liste af vektorer der pejer på de sidste 25 pkt bolden har været
  // Paddlex og Paddley er positionen af den anden paddle
 
  move(ballx,bally,ballxspeed, ballyspeed, history,Paddlex,Paddley)
  {
    //The runner
    this.y +=this.vy; 
  }
  show()
  {
    rect(this.x,this.y,this.w,this.h);
  }
  
}
```
Endelige følger en skabelon for AI-modstanderen. 

```javascript
  //peddleAI.js
  // Det er her i peddleAI.js=> move at I skal skrive noget kode der får jeres AI til at rykke sig
  // ballx, bally er boldens nuværende postition
  // ballxspeed, ballyspeed boldens velocity 
  // history er en liste af vektorer der pejer på de sidste 25 pkt bolden har været
  // Paddlex og Paddley er positionen af den anden paddle
class PeddleAI
{
  constructor(side, name)
  {
    this.name = name
    this.x = this.selectPosition(side);
    this.w = 20;
    this.h = 100;
    this.y = 200//height;
    this.vy = random([-2,2]);  
  }

  selectPosition(side)
  {
    if(side==="Left") return 10
    if(side==="Right") return 390
  }

  update()
  {
    if(this.y>=height-50 || this.y<=50)
    {
      this.vy *=-1;
    }
  }
  change_dir(y)
  {
    this.vy = y;
  }

  
  move(ballx,bally,ballxspeed, ballyspeed, history,Paddlex,Paddley) 
  {
    //The chaser
     
    if(bally>this.y){
      this.vy = 2
      this.y = this.y+this.vy
    }
    else if(bally<this.y){
      this.vy = -2
      this.y = this.y + this.vy
    }
    
    //this.y +=this.vy; bare køre op og ned 
  }



  show()
  {
    rect(this.x,this.y,this.w,this.h);
  }
  
}
```

Efterfølgende er her sketch.js som samler de andre klasser:

```javascript

let r_p;  // right paddle
let l_p;  // left paddle
let ball;
let prev_x = 0;

let score1 = 0;
let score2 = 0;
const SPEED_UP = 1.02;

function setup() {
  createCanvas(400, 400);
  rectMode(CENTER);
  l_p= new Peddle("Left","The Runner");
  r_p = new PeddleAI("Right","The Chaser");
  ball = new Ball();
}

function moveHuman() //left side can be moved manually using arrows
{
    l_p.vy = 0
    if(keyIsDown(UP_ARROW))
    {
      if(l_p.y<=50)
      {
        l_p.vy *=-1;
      }
      else {
        l_p.y-=2
      }
      
    }      
    if(keyIsDown(DOWN_ARROW))
    {
      if(l_p.y>=height-50)
      {
        l_p.vy *=-1;
      }
      else {
        l_p.y+=2
      }
    }
    
}
function draw() {
  background(0);
  textSize(20);
  text(l_p.name,30,50)
  text(score1,45,25);
  
  text(r_p.name,290,50)
  text(score2,340,25);

  //moveHuman()   //uncomment to move left side manually
  
  l_p.move(ball.x,ball.y, ball.vx, ball.vy, ball.history,r_p.x,r_p.y);   //changes the y value using velocity
  r_p.move(ball.x,ball.y, ball.vx, ball.vy, ball.history,l_p.x,l_p.y); //AI movement
  r_p.update(); //checks if paddle is outside border
  l_p.update(); //checks if paddle is outside border
  l_p.show();  //show the paddle
  r_p.show();   //show the paddle
  
  ball.move();
  ball.show(); 
  ball.update();
  
  //if ball goes outside
  if (ball.x>=width)
  {
    score1++
    ball.reset();
  }
  if (ball.x<=0)
  {
    score2++;
    ball.reset();
    
  }

  //detect collision
  /*
  if(ball.x>=380 && ball.y<=(r_p.y+50) && ball.y>=(r_p.y-50))
  {
    ball.vx *=-1;
    ball.vx *= SPEED_UP;
    ball.vy *= SPEED_UP;
  }
  
  if(ball.x>=20 && ball.y<=(l_p.y+50) && ball.y>=(l_p.y-50))
  {
    ball.vx *=-1;
    ball.vx *= SPEED_UP;
    ball.vy *= SPEED_UP;
  }
  */
  let dy = 50;
  
  //detect collision
  if(ball.x >= 380 && prev_x < 380 && ball.y<=(r_p.y+dy) && ball.y>=(r_p.y-dy)) {
    ball.vx *=-1;
    ball.vx *= SPEED_UP;
    ball.vy *= SPEED_UP;
  }
  
  if(ball.x <= 20 && prev_x > 20 && ball.y<=(l_p.y+dy) && ball.y>=(l_p.y-dy)) {
    ball.vx *=-1;
    ball.vx *= SPEED_UP;
    ball.vy *= SPEED_UP;
  }
  prev_x = ball.x
  
}
```
Til sidst et udsnit af html-filen. Forudsætter javascript filerne ligger samme sted som index.html:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/1.4.0/p5.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/1.4.0/addons/p5.sound.min.js"></script>
    <script src="peddle.js"></script>
    <script src="peddleAI.js"></script>
    <script src="ball.js"></script>
  
    <link rel="stylesheet" type="text/css" href="style.css">
    <meta charset="utf-8" />

  </head>
  <body>
    <script src="sketch.js"></script>
  </body>
</html>
```