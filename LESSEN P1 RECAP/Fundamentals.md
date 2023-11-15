## 1. Data types
### wat is data?
 **Data is niks ander dan informatie die je computer heeft. voor een computer bestaat alles uit 1 en 0.** Slimme mensen hebben toen programmeer talen bedacht. Hierdoor kunnen wij praten tegen de computer met code. Er zijn verschillende vormen van data, Dit noemen wij data types.
### Data types
#CrashCourse 
Voor alle data types geld het volgende: Als een data type meer kan, kost het je computer ook meer kracht.

- **Integers(INT):** zijn getallen. Het maximale getal dat een INT kan hebben is: 2,147,483,647
	`1` is een voorbeeld van een INT
- **Strings(STR):** zijn stukken tekst die alles mogen bevatten. bijvoorbeeld: `"hallo"`
- **Booleans(BOOL):** deze data types kunnen twee waarden hebben: `true`(binair 1) of `false`(binair 0)
- **Double:** zijn voor enorm grote comma getallen. Het grootste getal is: 1.79769313486231570e+308d.
- **Float:** gebruik je voor comma getalen( die niet heel groot zijn). 
- **EXTRA: numbers:** zijn basically doubles, maar alleen javascript gebruikt het voor alle getallen.

 [[Basisprogrammeren#Leren programmeren|Volgende deel voor de absolute basis]]


## 2. Naming conventions
### Wat is een naming convention
#CrashCourse 
**naming conventions zijn door de industrie aangemaakt als een standaard van hoe je alles een naam moet geven.** Het is bedoeld zodat je meteen snapt waar je naar kijkt als je het tegen komt. Elke taal heeft zijn eigen naming convention en soms kunnen bedrijven ook nog zelf een eigen naming convention hebben. Het is belangrijk dat je de naming conventions van je omgeving gebruikt.

**JavaScript gebruikt camelCasing.**

Dit zijn de drie meest gebruikte naming conventions:
- **camelCasing**
	Elk woord aan elkaar behalve de eerste krijgt een hooftletter
	voorbeeld: `superCar`

- **PascalCasing**
	Elk woord aan elkaar krijgt een hoofdletter
	voorbeeld: `SuperCar`

- **isX**
	Voor booleans, alle variables na `is` krijgen een hoofdletter.
	voorbeeld: `isActive` `isAlive` 

## 3. Comments
In programmeren maken we comments om te zorgen dat onze code makkelijker te begrijpen is. 

### **"comments zijn dus documentatie?"**
dat dan weer niet helemaal waar. Laten we zeggen comments zijn een snelle uitleg wat het doet. terwijl documentatie dat in meer detail doet.

### hoe schrijf ik comments?
er zijn veel verschillende manieren, de twee meest gebruikte zijn:
- **//** dit wordt gebruikt om een specifieke regel te gebruiken voor een comment
- `/* */` alles tussen de `*` is een comment. deze kunnen meerdere regels lang zijn.

## 4. Error
Spreekt redelijk vanzelf, het is het rode dat je krijgt wanneer een fout hebt gemaakt in je code. Vaak staat er in je Error wat en waar het fout is gegaan.

### Try catch
Een try catch statement is een soort if else statement maar dan is het voor slechts 1 ding bedoeld.  
Error handling. ***Je gebruikt een try catch statement wanneer je wilt checken of een stuk code zou kunnen draaien voordat je de data van deze code direct verwerkt.*** Dit is voornamelijk relevant als je data door wilt sturen naar bijvoorbeeld een database en elk klein detail wel moet kloppen.

## 5. Switch cases
(Waarom is dit hier en niet bij basisprogrammeren)
**Een Switch case is een soort van If, else if, else statement.** je kan Switch case of if else gebruiken. het is wat jij wil. om het simpel uit te leggen geef ik een stukje code
```JavaScript
let i = 10;

switch (i)
{
	case 5:
		console.log("1e case");
		break;
	case 10:
	case 20:
		console.log("2/3r case");
	break;
	default:
		console.log("default case");
		break;
}
```
om een Switch case te starten begin je met `switch (variable)`.  deze [[Basisprogrammeren#2. wat zijn variables|variable]] wordt gebruikt om te checken voor de cases.  je opent met een `{`.
het eerste wat je zien tussen de curly brackets is `case 5: ` dit is dus hetzelfde als `if (i= 5) {` alleen dan makkelijker. Hierna zien we een `console.log("1e case");` en `break;`. 
Wat `break;` hier doet is het stoppen van de switch case. hierna zal de code verder gaan met de rest. buiten de `{}`.
vervolgens zien we wat interessants:
```javascript
case 10:
case 20:
```
Dit zegt `if (i = 10 OR i = 20) {`. Hij zal dus het volgende commando na case uitvoeren bij beide.


