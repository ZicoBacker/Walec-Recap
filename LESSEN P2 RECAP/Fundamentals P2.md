# 1. Git
## Nieuwe repository clonen:

`git clone [link]` -- hiermee haal je een kopie van wat je hebt op GitHub naar je pc. Dit kan je dan weer committen voor een nieuwe versie

## hoe zet ik een nieuwe versie op github:

`git add [filename]` --voegt een file toe die je wil uploaden naar je repository(GitHub) 
`git commit -m "[comment]"` --dit zet het klaar om op te sturen 
`git push` -- stuurt het op naar GitHub, het zal dus meteen zichtbaar zijn 

bedenk je het zo: 
`git add` zorgt ervoor dat je je bestand toevoegt aan een lijst (git commit). dit hoef je maar 1x te doen per bestand. 
`git commit -m "[comments]"` zet het lijstje op om op te sturen en geeft het een naam. (vaak een versie) 
`git push` zet hem op je GitHub.

## als je problemen hebt met iets in de richting van "unknown user/ no valid user" doe dan dit:

`git config --global user.email [GitHub email]` 
`git config --global user.name [GitHub name]

# 2. Git merging & revert
## Revert
om terug te gaan naar een oudere versie omdat je het verneukt hebt of iets doe je: `**git revert COMMIT CODE HIER**`

**waar vind ik mijn git commit code?**
Dit vind je in je GitHub Repository. als je dan rechtsboven gaat naar commits kan je dit zien:
![[Pasted image 20231115110834.png]]
het onderstreepte is je git commit code. Deze gebruik je om te reverten.
## Git merging
bij git heb je vaak problemen als jij en iemand anders hetzelfde aanpassen en dan beide willen pushen. dit los je op in je Visual Studio Code. VSC gaat je helpen in het oplossen van merging conflicts. Dit zal er zo uit zien.![[Pasted image 20231115111007.png]]

Deze stap is alleen voor het geval dat je in detail moet kijken wat je nou eigenlijk als resultaat krijgt.  
Druk op de "Resolve in Merge Editor" knop.  
Kies hier de veranderingen die je wilt en kijk in het onderste "Result" venster of het resultaat is wat je wilt. In dit venster mag je ook typen voor verdere aanpassingen.
![[Pasted image 20231115111140.png]]
# if/if-else statements
## if
If else statements zijn de basis van JavaScript. Hierbij doet hij alleen iets **ALS** de condities correct zijn. Een voorbeeld:
```js
let color = "red"
if (color === "red") {
	console.log("Sign is red")
	}
```
de `===` betekend dat het dezelfde waarde moet hebben en dezelfde soort variable(int, string, ect)
## Else
Als je alle andere opties ook iets wil laten doen, kan je else gebruiken.
```js
let color = "red"
if (color === "red") {
	console.log("Sign is red")
	}
else {
	console.log("Sign is not red")
}
```
## else if
Ook heb je nog `else if`. Dit gebruik je wanneer je een paar specifieke antwoorden iets anders wil laten doen, dit zal gebeuren voor de `else`:
```js
let color = "red"
if (color === "red") {
	console.log("Sign is red")
	}
else if (color === "green") {
	console.log("Sign is green")
}
else {
	console.log("Sign is not red")
}
```
# For loops
For loops draaien onder een specifieke conditie.
```js
for(let i = 0; i <5; i++) 
{
	console.log("test")
}
```
dit zal 4x `test` sturen. Het stuurt hem niet 5x omdat wanneer hij bij 5 is het **NIET ONDER** 5 is, en dat is de conditie voor de loop. Als jij hem 5x wil laten draaien verander jij hem naar
`let i=0; i != 5; i++;`. 
# How to make an associative array in javascript
To make arrays in javascript we use `let array = [30, 234, 34, 5, 65]`
To make an associative array we have to use `{}` instead. 
For example `let array = {"fries":20, "mom":10, "dad": 45}`. This is a associative array.
# Quick note how to use forEach in JS
To use `.foreach` you will first have to have an array. Otherwise this function can not be used. To me it kinda has a weird ass syntax but it is as follows:
```js
array.foreach((value, index) =>{
	script that does smth
});
```
 The value and index are switched around here to keep you on your feet.