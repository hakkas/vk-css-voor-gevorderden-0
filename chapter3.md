# Les 3: Introductie Flexbox
Flexbox is een tamelijk nieuwe layout manier waarmee je in een (div) container elementen horizontaal of verticaal kunt verdelen. Samen met grid kun je hiermee de meest ingewikkelde layouts maken. Laten we meteen beginnen met een voorbeeld:

Stel dat je de volgende galerij wilt maken:
![](./images/galerij.png)

Je wilt dus wat foto's naast elkaar hebben en de afstand tussen de foto's moeten gelijk zijn.

Eerst de HTML:
```html
<div id="container">
  <div class="box">
    <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/c/cb/Spider_icon_%28Noun_Project%29.svg/100px-Spider_icon_%28Noun_Project%29.svg.png">
  </div>
  <div class="box">
      <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/d/dd/Fish_icon_%28The_Noun_Project_27052%29.svg/100px-Fish_icon_%28The_Noun_Project_27052%29.svg.png">
  </div>
  <div class="box">
    <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/b/b3/Mixed_forest_silhouette_scaled-to-hight%2C_quadratic.svg/100px-Mixed_forest_silhouette_scaled-to-hight%2C_quadratic.svg.png">
  </div>    
</div>
```

En de bijbehorende CSS:
```css
#container {
  background-color: yellow;
  display: flex;
  justify-content: space-evenly;
}

.box {
  background-color: green;
  width: 100px;
  height: 100px;
}
```

En het resultaat is:
[](codepen://h-akkas/Mrqwpx?height=150&theme=0)

Merk op dat het `display` eigenschap op het container element is ingesteld op `flex`. En met `justify-content` kunnen we instellen hoe de _flex-items_ horizontaal(!) in de container worden uitgelijnd. `space-evenly` betekent dat de ruimte tussen de flex-items precies eerlijk verdeeld wordt. Naast `space-evenly` heb je ook nog de volgende mogelijkheden:


| justify-content        | Betekenis           |
| ------------- |:-------------:|
| `justify-content: center;` | ![](./images/center.png) |
| `justify-content: flex-start;` | ![](./images/flex-start.png) |
| `justify-content: flex-end;` | ![](./images/flex-end.png) |
| `justify-content: space-around;` | ![](./images/space-around.png) |
| `justify-content: space-between;` | ![](./images/space-between.png) |

Je kunt middels het onderstaande even kijken naar het effect van de verschillende opties:

[](codepen://h-akkas/JMaYmL?height=200&theme=0)


Stel dat je hier nou een foto bij zet, dan gaat is dat geen probleem. De plaatjes krijgen een nieuwe plek zodat de ruimte tussen de elementen gelijk blijft. Zie maar:
[](codepen://h-akkas/godavE?height=150&theme=0)

## Flex-direction
Met flex-direction kun je de richting van de flex-items bepalen. Standaard staan de items naast elkaar, van links naar rechts. Maar dat kun je aanpassen. Je kunt bijvoorbeeld zeggen:

```css
#container {
  background-color: yellow;
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  width: 100px;
  height: 500px;
}
```
(De opmaak van `.box` is niet veranderd). Je ziet de property `flex-direction` ingesteld op column. Dat betekent dus dat de flex-items op elkaar worden gestapeld. Hieronder de uitwerking:

[](codepen://h-akkas/mpGevg?height=500&theme=0)

Naast de waarde `column` kun je ook de volgende waarden meegeven:


| flex-direction        | Betekenis           |
| ------------- |:-------------:|
| `flex-direction: column;` | De flex-items worden onder elkaar weergegeven |
| `flex-direction: column-reverse;` | De flex-items worden in omgekeerde volgorde onder elkaar weergegeven |
| `flex-direction: row;` | De flex-items worden naast elkaar weergegeven |
| `flex-direction: row-reverse;` | De flex-items worden in omgekeerde volgorde naast elkaar weergegeven |

## Verticaal uitlijnen met `align-items`
Met `justify-items` heb je geleerd hoe je elementen _horizontaal_ kunt uitlijnen. Met flexbox kun je (gelukkig) ook op een vrij eenvoudige manier elementen _verticaal_ uitlijnen. Hieronder een voorbeeld waarbij we de elementen verticaal hebben gecentreerd.

[](codepen://h-akkas/VQLwGP?height=400&theme=0)

Zoals je kunt zien hebben we een attribuut toegevoegd aan de container: `align-items: center`. Naast center kun je ook de volgende opties meegeven aan `align-items`:

![](./images/align-items.svg)

## Voor de rest
FlexBox is een fantastische techniek om elementen in een 1-dimensionale container te positioneren. Samen met Gridlayout kun je de meest geavanceerde layouts maken. Wat je hierboven hebt geleerd is slechts de basis. Je kunt nu de leuke en leerzame Flexxy Froggy opgaven maken door <a href="http://flexboxfroggy.com/#nl">hier</a> te klikken. Ook kun je de volgende pagina's raadplegen voor meer documentatie:
* https://css-tricks.com/snippets/css/a-guide-to-flexbox/
* https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flexible_Box_Layout/Basic_Concepts_of_Flexbox
