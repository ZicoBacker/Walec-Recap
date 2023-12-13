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


