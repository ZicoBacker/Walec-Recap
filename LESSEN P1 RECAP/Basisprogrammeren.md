## 1. Leren programmeren
Het is ontzettend lastig voor veel mensen om te leren programmeren. Een computer leest alles heel letterlijk, hierdoor moet je op een andere manier leren denken om het goed te doen.

### Programmeer regels
De meeste regels/structuur van code is overal bijna hetzelfde, maar net een beetje anders.

### Order of execution
#CrashCourse
**De manier waarop code wordt gelezen is van boven naar beneden.** Hij doet eerst wat je zegt op regel 1, dan op regel 2 ect ect.. maar hierin hebben wij een paar belangrijke punten:
#### ; (semicolon of puntkomma)
deze gebruiken we om een taak te eindigen. bijvoorbeeld `console.log("hello world");` Als je dit niet doet kan je in sommige programmeer talen een error krijgen dus **maak hier een gewoonte van in javascript**

#### { } (curly brackets/ accolades)
Curly brackets gebruik je voor if/else statements of functies bijvoorbeeld. Het is belangrijk dat je ze sluit anders heb je gezeik met je code.
## 2. wat zijn variables
Variables is data dat kan variëren. bijvoorbeeld een doos waar je wat in kan stoppen.
je geeft aan wat voor soort doos het is( hout steen plastic karton) en geeft het een naam
```js
let Getal = 5
```
In dit voorbeeld zegt `let` wat voor soort doos het is, `Getal` is de naam van de doos en `5` is wat erin zit.

### Soort 'dozen'
er zijn 3 soorten 'dozen' in javascript: `let`, `var` en `const`. het verschil tussen `let`, `var` en `const` is dat `const` nooit aangepast kan worden nadat het aangemaakt wordt.

### Soort data dat in de dozen kan
De soorten data dat in de dozen kan is besproken in [[Fundamentals#Data types| Data types]].

Hier heb je twee voorbeelden van variables in JavaScript(JS) en CSharp(C#):
JavaScript
```js
let roundedNumber = 2;  
let decimalNumber = 3.14;  
let isFalse = false;  
let playerName = "Shane van der Woude";
```

C#
```c#
int roundedNumber = 2;  
float decimalNumber = 3.14f;  
bool isFalse = false;  
string playerName = "Shane van der Woude";
```