# Les 3: Introductie FlexBox
FlexBox is een tamelijk nieuwe layout manier waarmee je in een (div) container elementen horizontaal of verticaal kunt verdelen.

Een voorbeeld:
```html
<div id="container">
  <div class="box">a</div>
  <div class="box">b</div>
  <div class="box">c</div>    
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

[](codepen://h-akkas/vpaRJQ?height=300&theme=0)
