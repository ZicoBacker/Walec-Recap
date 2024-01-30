# functies maken
om een functies zijn stukken tekst die je terug kan roepen met de naam van de functie.
een voorbeeld:
```JavaScript
function naam(getal1, getal2) { //de variables getal1 en getal2 bestaan.
return console.log("hello World" + getal1 + getal2);
} //de variables getal1 en getal 2 bestaan niet meer.

naam(1,5);
```
Wat hier uit zal komen is `hello World15`. Ik leg uit waarom
`function naam(getal1, getal2) {` we zeggen hier dat we een functie aanmaken met daarin 2 variables die alleen bestaan tussen de `{}`. De naam van de functie in dit geval is `naam`. 

Tussen de haakjes staat het volgende: `console.log("hello World" + getal1 + getal2);` 
dit hebben we eerder gehad, dit zegt in de console `Hello World` met de twee waardes van getal 1 en 2, maar die hebben we nog niet. Die geef je mee met wanneer je de functie aanroept.

`naam(1,5);` we roepen de functie op, hij zal dus doen wat tussen de `{}` staat. we geven de functie twee getallen mee: `(1, 5);` deze twee getallen staan gelijk aan getal1 en getal2.

`return` is een commando dat het script stopt en de functie geeft terug wat je returned. Dit kan je in veel verschillende wegen gebruiken maar daar komen we nog op.

Dit is zo uitgebreid simpel dat functies bestaan.

# For each javascript
The **`forEach()`** method of [`Array`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) instances executes a provided function once for each array element.
```js
const array1 = ['a', 'b', 'c'];
array1.forEach((element) => console.log(element));
```

```js
// Add to the start of an array
Array.unshift(element);

// Add to the end of an array
Array.push(element);

// Add to a specified location
Array.splice(start_position, 0, new_element...);

// Add with concat method without mutating original array
let newArray = [].concat(Array, element);

```




# Javascript in HTML
## Elementen aanpassen
Met javascript kan je elementen en tekst in HTML aanpassen. Dit kan je doen door gebruik te maken van `document.getElementById()`. Hiermee kan je een variabele koppelen aan het element in de HTML. Voorbeeld:
```js
let Text1 = document.getElementById("text1") 
```
Dit zegt dus dat de variabel `Text1` in javascript hetzelfde is als het element met het id `text1` is in HTML.

Nu kunnen wij het element aanpassen via de javascript. Om dit te doen als voorbeeld kan je het aanspreken als een [[Backend P2#classes|Object]]. Voor tekst doen wij dat via `Text1.InnerHTML("Hello World")`. Dit stukje text zegt dat de `InnerHTML` van `Text1` : `"Hello World"` moet zijn.

Je kan ook de CSS aanpassen via JavaScript. We doen dit hier door `Text1.style.<style>` te doen. wij kunnen alles eraan toevoegen, Maar dit wordt wel inline en niet external. Een voorbeeld is
```js
Text1.style.color = "green"
```
## Events
Een event is eigenlijk wanneer er wat gebeurd in de html. Denk dan aan `onclick`, `onmouseover`,`onmouseout`, ect. Hieraan kan je een functie hangen die uitgevoerd wordt wanneer een Event gebeurd. Wij kunnen dit op twee manieren doen:
`<button onlick="Myfunction()">Hello!</button>`. Wij doen dit in de HTML en `Myfunction()` is een referentie naar de de `Myfunction()` in JavaScript.

De tweede manier is om het in de JavaScript te doen. Een voorbeeld is:
```js
button = document.GetElementById("button1");
button.addEventListener("click", myFunction);
```
Dit stukje wacht totdat de knop geklikt wordt en zal daarna `myFunction` uitvoeren.