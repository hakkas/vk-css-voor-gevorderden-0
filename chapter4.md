# Les 4: Selectors en Combinators

Tot nu toe heb je geleerd hoe je eenvoudige selectors kunt gebruiken voor de opmaak van je elementen. Je hebt leren werken met classes, id's etc. Ook heb je pseudo classes zoals :link, :hover gebruikt. Maar dit waren slechts de basics van de mogelijkheden die je hebt met selectors. In deze lesbrief gaan we in op meer dan 20 verschillende selectors die je tegenwoordig kan gebruiken in CSS3.

### Het sterretje als selector: *

```css
* {
 margin: 0;
 padding: 0;
}
```

Laten we eerst de basis selectors behandelen, zodat we later over kunnen stappen naar de wat geavanceerdere.

Het sterretje selecteert _alle_ elementen in je document. Veel ontwikkelaars gebruiken deze truuc om alle margin's en padding's voor elk element te resetten naar 0px;

Maak de * selector kan ook worden gebruikt voor alle (child) elementen van element:

```css
#container * {
 border: 1px solid black;
}
```

Deze code geeft ieder element _in_ de #container een zwart randje.

### Een id als selector: #X
```css
#container {
   width: 960px;
   margin: auto;
}
```
Door een hashtag te gebruiken voor een selector kun je elementen met een specifieke id selecteren. Dit wordt vaak gebruikt omdat het lekker simpel is om een bepaald element te selecteren.

## Een class als selector: .X
```css
.error {
  color: red;
}
```
Met een . kunnen we elementen met een bepaalde class selecteren. Het verschil tussen een id en een class is waarschijnlijk bekend: Er kunnen meerdere elementen in een HTML-document met dezelfde class voorkomen, terwijl er maar 1 element mag zijn die dezelfde id mag hebben.

## X Y
```css
li a {
  text-decoration: none;
}
```
Stel dat je niet alle linkjes (a) wilt selecteren, maar alleen de linkjes (a) die in een li zitten? Dat kan met een zogenaamde _descendant selector_. Als je ```li a``` als selector aangeeft, dan worden alle linkjes die in een li-element zitten geselecteerd.

Je kunt ook ```ol li a``` als selector opgeven. In dit geval worden alle elementen geselecteerd waarbij de ```a``` in een ```li``` zit en die ```li``` moet dan in een ```ol``` zitten.

## X
```css
a { color: red; }
ul { margin-left: 0; }
```
De meest eenvoudige selector is de _type selector_. Als je bijvoorbeeld alle ul's in het document wilt selecteren, dan gebruik je als selector gewoon ```ul```.

## X:visited en X:link
```css
a:link { color: red; }
a:visted { color: purple; }
```
We use the :link pseudo-class to target all anchors tags which have yet to be clicked on.

Alternatively, we also have the :visited pseudo class, which, as you'd expected, allows us to apply specific styling to only the anchor tags on the page which have been clicked on, or visited.

## X + Y
```css
ul + p {
   color: red;
}
```
Dit is een voorbeeld van een _adjacent selector_. Adjacent betekent aangrenzend of naburig. In het voorbeeld ```ul + p``` worden dus alle p's geselecteerd die _direct_ _na_ een ul komen.

Voorbeeld:
[](codepen://h-akkas/mxRZNb?height=300&theme=0)


## X > Y

```css
div#container > ul {
  border: 1px solid black;
}
```
Als je een &gt; gebruikt tussen twee elementen, dan worden alleen de directe kinderen geselecteerd. Dus als de ul direct in de div zit, dan krijgt hij een randje. Maar als de ul ook nog eens in een andere div zit (dus als het een van de kleinkinderen is), dan wordt hij niet geselecteerd.

Zie hier een voorbeeld:
[](codepen://h-akkas/jzygbw?height=300&theme=0)

## X ~ Y

```css
ul ~ p {
   color: red;
}
```
Deze zogenaamde _sibling combinator_ lijkt veel op de + van X + Y, behalve dan dat hij minder strict is. Een sibling betekent een broertje of zusje. In de context van HTML bedoel je daarmee de elementen die op gelijke niveau zijn. In het volgende voorbeeld zijn de p en de ul _siblings_ van elkaar:

```html
<body>
  <ul>
    <li></li>
    <li></li>
  </ul>
  <p>
  </p>
</body>
```

Terwijl de _adjacent selector_ (ul + p) alleen de eerste sibling van het type p selecteert, is de ~ minder strict. Bij ul ~ p hoeft de p niet meteen na de ul te komen. Als hij maar na de ul komt en een sibling is.

In het onderstaande voorbeeld zie je dat de alinea met tekst groen is, terwijl de p niet direct na de ul komt:
[](codepen://h-akkas/xWgvLe?height=300&theme=0)

## X[title]
```css
a[title] {
   color: green;
}
```
Hier selecteren we alle elementen die een attribuut genaamd title hebben. Je kunt natuurlijk ook andere attributen tussen de blokhaken zetten.

##  X[href="foo"]
```css
a[href="https://www.coderclass.nl"] {
  color: #1f6053; /* green */
}
```
In het bovenstaande voorbeeld worden alle linkjes die verwijzen naar https://www.coderclass.nl geselecteerd.

Denk erom dat je de link tussen aanhalingstekens moet zetten.

Dit is best handig, maar stel dat je alle linkjes die verwijzen naar een bepaald domein wilt selecteren? Dus https://www.coderclass.nl/onsteam/, maar ook https://www.coderclass.nl/badges/ etc. Dan kunnen we gebruik maken van het sterretje. Zie hieronder:

##  X[href*="coderclass"]
```css
a[href*="coderclass"] {
  color: #1f6053; /* green */
}
```

*= betekent dat het woordje coderclass ergens in de url moet voorkomen.

##  X[href^="http"]
```css
a[href^="http"] {
   background-color: url(path/to/external/icon.png) no-repeat;
   padding-left: 10px;
}
```

<div class="alert alert-success">
  <i class="fa fa fa-info-circle"></i>
  <p>
    <strong>Opdracht</strong> Maak nu opdracht 7 in repl.it
  </p>
</div>

Met het dakje ^ kun je aangeven dat de inhoud van href moet beginnen met http. Dit kun je gebruiken om de externe links op je pagina anders op te maken dan de interne links.

En stel je voor dat we alle links die naar een foto verwijzen willen selecteren. Dan moeten we naar het einde van de string zoeken. Kijk maar:

##  X[href$=".jpg"]
```css
a[href$=".jpg"] {
   color: red;
}
```
Hiermee selecteren we alle elementen waarvan de href eindigt op een jpg. Een plaatje dus. Het dollar tekentje ($) geeft het einde van de string aan.

##  ```X[data-*="foo"]```

```css
a[data-filetype="image"] {
   color: red;
}
```

Stel dat we niet alleen de jpg bestanden, maar ook gif's, png bestanden, bmp bestanden etc. zouden willen selecteren. Dan kan dat natuurlijk op deze manier:

```css
a[href$=".jpg"],
a[href$=".jpeg"],
a[href$=".png"],
a[href$=".gif"] {
   color: red;
}
```

Maar dit is lelijk en inefficient. Een andere oplossing zou zijn om met _custom attributen_ te werken. We kunnen namelijk onze eigen attributen bedenken en toevoegen aan een element. We bedenken er even een: ```data-filetype```. En de data-filetype van alle links die naar plaatjes verwijzen stellen we in op ```'image'```. Dat ziet er zo uit:

```html
<a href="path/to/image.jpg" data-filetype="image"> Image Link </a>
```

Nu we dat gedaan hebben hoeven we in de selector alleen aan te geven dat we alle links willen waarvan de data-filetype gelijk is aan image. Lekker handig toch?

```css
a[data-filetype="image"] {
   color: red;
}
```

##  X:checked

```css
input[type=radio]:checked {
   border: 1px solid black;
}
```
Met deze zogenaamde psuedoclass zullen alleen de radiobuttons/checkboxen geselecteerd worden die aangevinkt zijn.

##  X:after
The before and after pseudo classes kick butt. Every day, it seems, people are finding new and creative ways to use them effectively. They simply generate content around the selected element.

Many were first introduced to these classes when they encountered the clear-fix hack.

```css
.clearfix:after {
    content: "";
    display: block;
    clear: both;
    visibility: hidden;
    font-size: 0;
    height: 0;
    }

.clearfix {
   *display: inline-block;
   _height: 1%;
}
```

This hack uses the :after pseudo class to append a space after the element, and then clear it. It's an excellent trick to have in your tool bag, particularly in the cases when the overflow: hidden; method isn't possible.

For another creative use of this, refer to my quick tip on creating shadows.

According to the CSS3 Selectors specification, you should technically use the pseudo element syntax of two colons ::. However, to remain compatible, the user-agent will accept a single colon usage as well. In fact, at this point, it's smarter to use the single-colon version in your projects.

##  X:hover
```css
div:hover {
  background: #e3e3e3;
}
```

Oh come on. You know this one. The official term for this is user action pseudo class. It sounds confusing, but it really isn't. Want to apply specific styling when a user hovers over an element? This will get the job done!

Keep in mind that older version of Internet Explorer don't respond when the :hover pseudo class is applied to anything other than an anchor tag.

You'll most often use this selector when applying, for example, a border-bottom to anchor tags, when hovered over.

```css
a:hover {
 border-bottom: 1px solid black;
}
```
Pro-tip - border-bottom: 1px solid black; looks better than text-decoration: underline;.

##  X:not(selector)
```css
div:not(#container) {
   color: blue;
}
```
The negation pseudo class is particularly helpful. Let's say I want to select all divs, except for the one which has an id of container. The snippet above will handle that task perfectly.

Or, if I wanted to select every single element (not advised) except for paragraph tags, we could do:

```css
*:not(p) {
  color: green;
}
```

##  X::pseudoElement
```css
p::first-line {
   font-weight: bold;
   font-size: 1.2em;
}
```

We can use pseudo elements (designated by ::) to style fragments of an element, such as the first line, or the first letter. Keep in mind that these must be applied to block level elements in order to take effect.

A pseudo-element is composed of two colons: ::

```css
p::first-letter {
   float: left;
   font-size: 2em;
   font-weight: bold;
   font-family: cursive;
   padding-right: 2px;
}
```

This snippet is an abstraction that will find all paragraphs on the page, and then sub-target only the first letter of that element.

This is most often used to create newspaper-like styling for the first-letter of an article.

Target the First Line of a Paragraph
```css
p::first-line {
   font-weight: bold;
   font-size: 1.2em;
}
```
Similarly, the ::first-line pseudo element will, as expected, style the first line of the element only.

"For compatibility with existing style sheets, user agents must also accept the previous one-colon notation for pseudo-elements introduced in CSS levels 1 and 2 (namely, :first-line, :first-letter, :before and :after). This compatibility is not allowed for the new pseudo-elements introduced in this specification." - Source

##  X:nth-child(n)
```css
li:nth-child(3) {
   color: red;
}
```
Remember the days when we had no way to target specific elements in a stack? The nth-child pseudo class solves that!

Please note that nth-child accepts an integer as a parameter, however, this is not zero-based. If you wish to target the second list item, use li:nth-child(2).

We can even use this to select a variable set of children. For example, we could do li:nth-child(4n) to select every fourth list item.


##  X:nth-last-child(n)

```css
li:nth-last-child(2) {
   color: red;
}
```

What if you had a huge list of items in a ul, and only needed to access, say, the third to the last item? Rather than doing li:nth-child(397), you could instead use the nth-last-child pseudo class.

This technique works almost identically from number sixteen above, however, the difference is that it begins at the end of the collection, and works its way back.


##  X:nth-of-type(n)

```css
ul:nth-of-type(3) {
   border: 1px solid black;
}
```

There will be times when, rather than selecting a child, you instead need to select according to the type of element.

Imagine mark-up that contains five unordered lists. If you wanted to style only the third ul, and didn't have a unique id to hook into, you could use the nth-of-type(n) pseudo class. In the snippet above, only the third ul will have a border around it.


##  X:nth-last-of-type(n)
```css
ul:nth-last-of-type(3) {
   border: 1px solid black;
}
```
And yes, to remain consistent, we can also use nth-last-of-type to begin at the end of the selectors list, and work our way back to target the desired element.

##  X:first-child

```css
ul li:first-child {
   border-top: none;
}
```
This structural pseudo class allows us to target only the first child of the element's parent. You'll often use this to remove borders from the first and last list items.

For example, let's say you have a list of rows, and each one has a border-top and a border-bottom. Well, with that arrangement, the first and last item in that set will look a bit odd.

Many designers apply classes of first and last to compensate for this. Instead, you can use these pseudo classes.

##  X:last-child

ul > li:last-child {
   color: green;
}
The opposite of first-child, last-child will target the last item of the element's parent.

Example
Let's build a simple example to demonstrate one possible use of these classes. We'll create a styled list item.

Markup
```html
<ul>
   <li> List Item </li>
   <li> List Item </li>
   <li> List Item </li>
</ul>
```
Nothing special here; just a simple list.

```css
ul {
 width: 200px;
 background: #292929;
 color: white;
 list-style: none;
 padding-left: 0;
}

li {
 padding: 10px;
 border-bottom: 1px solid black;
 border-top: 1px solid #3c3c3c;
}
```
This styling will set a background, remove the browser-default padding on the ul, and apply borders to each li to provide a bit of depth.

Styled List
To add depth to your lists, apply a border-bottom to each li that is a shade or two darker than the li's background color. Next, apply a border-top which is a couple shades lighter.

The only problem, as shown in the image above, is that a border will be applied to the very top and bottom of the unordered list - which looks odd. Let's use the :first-child and :last-child pseudo classes to fix this.

```css
li:first-child {
    border-top: none;
}

li:last-child {
   border-bottom: none;
}
```
Fixed
There we go; that fixes it!

##  X:only-child

```css
div p:only-child {
   color: red;
}
```
Truthfully, you probably won't find yourself using the only-child pseudo class too often. Nonetheless, it's available, should you need it.

It allows you to target elements which are the only child of its parent. For example, referencing the snippet above, only the paragraph that is the only child of the div will be colored, red.

Let's assume the following markup.

```html
<div><p> My paragraph here. </p></div>

<div>
   <p> Two paragraphs total. </p>
   <p> Two paragraphs total. </p>
</div>
```
In this case, the second div's paragraphs will not be targeted; only the first div. As soon as you apply more than one child to an element, the only-child pseudo class ceases to take effect.

##  X:only-of-type
```css
li:only-of-type {
   font-weight: bold;
}
```
This structural pseudo class can be used in some clever ways. It will target elements that do not have any siblings within its parent container. As an example, let's target all uls, which have only a single list item.

First, ask yourself how you would accomplish this task? You could do ul li, but, this would target all list items. The only solution is to use only-of-type.

```css
ul > li:only-of-type {
   font-weight: bold;
}
```
