# 1. Unity installeren
Wij zijn de eerste les puur aan de slag gegaan met het installeren van [[Unity Hub]].
Daarnaast zijn we aan de slag gegaan met scripts toevoegen aan objecten. Dit doe je door een script rechts helemaal onder in te slepen.
![[Pasted image 20231115091431.png]]

## hoe maak iets
om een object te maken druk je op rechtermuisklik linksboven.
![[Pasted image 20231115091945.png]]
In basisprogrammeren voor games gaan we vooral aan de slag met 3D objects. dus meer zal je nog niet hoeven te weten.

**Om een script aan te maken** rechtermuisklik je in de balk midden onder:
![[Pasted image 20231115092257.png]]


## CSharp(C#)
In unity werken wij met CSharp(C#). dit werkt een beetje anders dan PHP of JavaScript.
Om een script te openen dubbelklik je erop, nadat ik je geholpen heb zal hij dit openen met visual studio community. Je zal ongeveer dit zien:
![[Pasted image 20231115093508.png]]

ik zal vanaf hier code zo laten zien:
```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Script1 : MonoBehaviour
{


    // Start is called before the first frame update
    void Start()
    {
        
    }

    // Update is called once per frame
    void Update()
    {
        
    }
}
```
Dit is de basis structuur van een C# script in Unity. Je hoeft niks aan te raken voor `public class Script1: MonoBehaviour {` we gaan tussen de brackets van de public class aan de slag.

Hier hebben we een voorbeeld van een script die we gebruikt hebben tijdens de les:
```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Moving : MonoBehaviour
{ 
    private float speed = 10;

    private float horizontal;
    private float vertical;
    private void Start()
    {

    }
    public void Update()
    {
        horizontal = Input.GetAxis("Horizontal");
        vertical = Input.GetAxis("Vertical");
        

        transform.Translate(new Vector3(horizontal, 0, vertical) * Time.deltaTime * speed );
    }


}
```
Dit ziet er allemaal enorm groot en uitgebreid uit, maar het wordt niet heel ingewikkeld. we beginnen bij het begin: 
- **`public class Moving: MonoBehaviour`** dit is de naam van het script en geeft aan dat het een script is.
- **`private float speed = 10;`** zoals eerder besproken, [[Basisprogrammeren#; (semicolon of puntkomma)|puntkomma's]] zijn heel belangrijk in C#. je gaat gezeik krijgen als je ze vergeet. 
	- `private` in dit geval heeft twee opties: `public` of `private`. als het `public` is betekend het dat andere scripts het getal kunnen gebruiken. wanneer het `private` is kan het alleen in het script waarin de variable staat gebruikt worden.
	- `float` is het [[Fundamentals#Data types|Data type]] voor de variable
	- `speed` is de naam van de variable
	- vervolgens zet je het data type soort erachter en klaar, je hebt een [[Basisprogrammeren#2. wat zijn variables|Variable]].
- **`private float horizontal;`** werkt ongeveer hetzelfde, alleen zeg je nog niet wat de waarde is van de variable.
- **`private float vertical;`** is hetzelfde
- Hierna beginnen we met `private void Start()` Dit is hoofdletter gevoelig. Dit draait elke keer wanneer het script start(wanneer je op play drukt). Alles erin wordt een keer uitgevoerd.
- In dit geval hebben wij er niks in staan. je kan je variables ook in je start zetten.
- **`public void Update()`** is ook hoofdletter gevoelig. Dit deel van het script wordt elke Frame gedaan. Hierin zien we het volgende
- **`horizontal = Input.GetAxis("Horizontal");`** is een klein beetje lastig. alles is hoofdletter gevoelig. Hierdoor is `horizontal` en `Horizontal` niet hetzelfde. er wordt hier gezegd dat de variable `horizontal` eigenlijk de input is van de knoppen om horizontaal te bewegen. `Input.GetAxis("Horizontal")` is namelijk al in unity. Dit zijn de A en D toetsen.
- **`vertical = Input.GetAxis("Vertical");`** heeft hetzelfde verhaal als hierboven.
- **`transform.Translate(new Vector3(horizontal, 0, vertical) * Time.deltaTime * speed );`** is het lastigste, dus we delen het op:
	- **`transform.Translate`** is hetzelfde als transform dat we gebruiken om een object zijn locatie of grootte aan te passen.
	- **`(new Vector3())`** heel simpel gezegd Vector3 is een soort mini array van 3 waardes.  zo zou je het je in kunnen beelden: <0, 0, 0>
	- **`(horizontal, 0 , vertical)`** de volgorde is hier XYZ. XYZ is ongeveer hetzelfde als in Minecraft. Het zijn de 3 dimensies. we zeggen hier dat X = `horizontal`, Y = 0 en Z = `vertical`
	- **`* Time.deltaTime`** zegt eigelijk "keer het aantal tijd tussen frames". Dit zorg ervoor dat je karakter niet tyfus snel door de wereld vliegt in dit geval.
	- **`* speed`** is in dit geval x10 zodat je niet tyfus langzaam beweegt.

Lange uitleg, maar als je dit ook maar een beetje snapt zal je redelijk ver komen voor BPVG.

# 2. 