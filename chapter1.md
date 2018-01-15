# Les 1: Het creëren van een layout met grid

Sinds het ontstaan van het web is het altijd al een uitdaging geweest om op een goede manier de layout voor een webpagina te definiëren. Terwijl hier in de jaren 90 frames en tabellen werden gebruikt is men met de komst van CSS overgegaan op div's en float's. Maar zowel frames als tabellen als floats zijn eigenlijk niet geschikt om layouts mee te maken. Ook jullie hebben geleerd om layouts te maken met floats, maar gelukkig zijn hier de afgelopen jaren betere methoden voor bedacht. Een van die methodes is grid! Daar gaat dit hoofdstuk over.

Hier nog even een voorbeeld van een layout met de ouderwetse HTML tabellen:
[](codepen://hakanakkas/aEGYLR?height=500&theme=0)

Zoals je in de code kunt zien is dit een en al spaghetti code. Websites die zo zijn ontworpen zijn ook niet responsive en dus smartphoneonvriendelijk. Je zult merken dat je met CSS grid vrij gemakkelijk je website responsive kunt maken!

## Wat is grid?
Grid lijkt aan de ene kant best op een HTML tabel. Het is namelijk een 2d-raster met kolommen en rijen. Terwijl je met HTML tabellen deze structuur in de HTML-code zet, doe je dat met grid in de CSS.

## Een layout met 3-kolommen
Laten we eerst beginnen met het creëren van een layout met drie kolommen. We maken een container `div` aan en daarbinnen drie div's die als kolommen gaan dienen.

``` html
<body>
  <div id="container">
    <div id="linkerkolom" class="box"></div>
    <div id="centrum" class="box"></div>    
    <div id="rechterkolom" class="box"></div>        
  </div>
</body>
```
Merk op dat we elke `div` in de container zowel een `id` als een `class` geven.

In de CSS kunnen we nu de container als `grid` instellen. Dat doen we door het attribuut `display` de waarde `grid` te geven. Ook moeten we met `grid-template-columns` aangeven hoe de verhouding van de kolommen moet zijn. Zie hieronder:

``` css
#container {
  display: grid;
  grid-template-columns: 1fr 6fr 1fr;
}
```
Bij `grid-template-columns` zie je iets met `fr`. Dit is een eenheid waarmee je een verhouding kan aangeven. 1 + 6 + 1 = 8. De eerste kolom heeft de waarde `1fr`. Dat betekent dat hij (in de breedte) 1/8 van de breedte in beslag neemt. De middelste kolom 6/8 en de derde kolom weer 1/8.

Vervolgens gaan we de div'jes in de container opmaken.

We geven de class `.box` een minimale hoogte van 700px, zodat we de kolommen ook mooi te zien krijgen zonder dat er veel tekst in zit. En vervolgens geven we elke div een andere kleur.

``` css
.box {
  min-height: 700px;
}

#linkerkolom {
  background-color: green;
}

#centrum {
  background-color: yellow;
}

#rechterkolom {
  background-color: blue;
}
```
Voor een demo van het bovenstaande, zie de uitwerking hieronder. Voel je vrij om er dingen aan te veranderen zodat je precies begrijpt hoe het in elkaar steekt.

[](codepen://h-akkas/qpKwzb?height=500&theme=0)

## Een layout met meerdere rijen
We gaan nu een stapje verder. Stel dat je de onderstaande layout zou willen maken:

[](https://docs.google.com/drawings/d/16WMBGT6tMgwsRhDCGE9J20cPwd0vReDXLkSHgtO82KM/edit?usp=sharing)

Dit is dus een layout met twee rijen. We passen de HTML aan:

``` html
<body>
  <div id="container">
    <div id="bovenbalk"></div>
    <div id="linkerkolom" class="box"></div>
    <div id="centrum" class="box"></div>    
    <div id="rechterkolom" class="box"></div>        
  </div>
</body>
```

Nu moeten we twee dingen doen:
* Eerst aangeven dat we twee rijen hebben in onze grid;
* En vervolgens instellen dat de `div` met `id` bovenbalk zo breed is als drie kolommen (met HTML tabellen heet dit `colspan`)

``` CSS
#container {
  display: grid;
  grid-template-columns: 1fr 6fr 1fr;
  grid-template-rows: 1fr 6fr;
}

#bovenbalk {
  grid-column-start: 1;
  grid-column-end: 4;
  background-color: pink;
}
```

Zoals je ziet hebben we in de container aangegeven dat we twee rijen willen. De verhoudingen zijn 1/7 voor de bovenste rij en 6/7 voor de tweede rij.

Vervolgens maken we de bovenbalk op:
Omdat we drie kolommen hebben, willen we aangeven dat deze balk drie kolommen in beslag moet nemen. Van kolom 1 _tot_ 4. Dat doen we met `grid-column-start` en `grid-column-end`.

Zie ook hieronder het uitgewerkte voorbeeld:
[](codepen://h-akkas/QaxRZe?height=500&theme=0)

## Geavanceerde layout met area's
Nu wil je als webdesigner uiteindelijk dit soort layouts maken:
[](https://docs.google.com/drawings/d/1-VTi4-hQc_w4njq-4oK20rsdAHmmmf6r98OdUxc8kas/edit?usp=sharing)

Deze zijn wat geavanceerder. Allereerst is het belangrijk om te weten dat je dit op verschillende manieren kunt doen. Een vrij eenvoudige en overzichtelijke manier om dit met CSS grid te doen is door gebruik te maken van de property `grid-template-areas`. Het werkt als volgt:

We gaan eerst de HTML aanpassen:
``` html
<body>
  <div id="container">
    <div id="bovenbalk"></div>
    <div id="linkerkolom">a</div>
    <div id="centrum1">b</div>  
    <div id="centrum2">b</div>  
    <div id="rechterkolom">c</div>        
    <div id="footer"></div>
  </div>
</body>
```
Zoals je ziet hebben we twee middenblokken: `centrum1` en `centrum2`. Ook hebben we een `footer` in het leven geroepen.

We gaan nu naar de CSS. Je stelt in de container alle gebieden van je layout in met de eigenschap `grid-templates-areas`:
``` css
#container {
  display: grid;
  grid-template-columns: 1fr 5fr 1fr;
  grid-template-rows: 1fr 3fr 3fr 1fr;
  grid-template-areas: "hoofd hoofd hoofd"
                       "menu midden1 fotos"
                       "menu midden2 fotos"
                       "voet voet voet";
}
```
We hebben vier rijen en drie kolommen. We hebben de verhoudingen ingesteld met `grid-template-columns` en `grid-template-rows`. En vervolgens delen we het raster in gebieden (areas). Elk gebied krijgt een eigen naam. Dus hoofd is een gebied dat in de breedte drie cellen in beslag neemt. Menu is een gebied dat in het verticale twee cellen in beslag neemt enz.

Het enige dat we nu nog hoeven te doen is dat we per div moeten aangeven voor welk gebied het is. Dat doen we met de property `grid-area`. Zie:

``` css
#bovenbalk {
  background-color: pink;
  grid-area: hoofd;
  height: 50px;
}

#linkerkolom {
  background-color: green;
  grid-area: menu;
}

#centrum1 {
  background-color: yellow;
  grid-area: midden1;
}

#centrum2 {
  background-color: lightgreen;
  grid-area: midden2;
}

#rechterkolom {
  background-color: blue;
  grid-area: fotos;
}

#footer {
  grid-area: voet;
  background-color: black;
}
```
Volgens mij spreekt het voor zich! Zie hieronder voor het gehele voorbeeld:

[](codepen://h-akkas/baKPNX?height=500&theme=0)


## Voor de rest
CSS grid is iets fantastisch, maar het is echt _veel meer_ dan de stof die in deze lesbrief is behandeld. We moedigen je daarom van harte aan om je te verdiepen in dit onderwerp. Dit kan allereerst door 25 hele leuke puzzeltjes op http://cssgridgarden.com/ te gaan doen. Voor de rest kun je eens kijken naar de volgende sites:
* https://www.youtube.com/watch?v=7kVeCqQCxlk
* https://css-tricks.com/snippets/css/complete-guide-grid/
* https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Grid_Layout
* https://www.w3schools.com/css/css_grid.asp
* https://people.igalia.com/svillar/slides/blinkon3.pdf
* https://bitsofco.de/css-grid-terminology/
