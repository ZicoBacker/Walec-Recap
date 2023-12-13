# Shane headstart uitleg (***IS NOG NIET NODIG OM TE WETEN***) :

## Variable and component access

### components aanroepen
blabla.cs
```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class blabla : MonoBehaviour
{
    private BoxCollider boxCol;
    public float myFloat;

    // Start is called before the first frame update
    void Start()
    {
        boxCol = GetComponent<BoxCollider>();
        boxCol.isTrigger = false;
    }

    // Update is called once per frame
    void Update()
    {
        
    }
}
```
buiten de basic layout gebeurt Hier het volgende:
**`private BoxCollider boxCol;`** Wat we hier doen is een variable aanmaken. De soort variable is `BoxCollider`. Simpel gezegd dit betekend dat deze variable een instelling van het component(shit rechts in je unity scherm) kan aanpassen.

**`public float myFloat;`** Is een float variable die "myFloat heet". Dit kan een comma getal bevatten.

**`boxCol = GetComponent<BoxCollider>();`** Hier zeggen we dat `boxCol` een component(nogmaals die shit rechts in unity) haalt. alles tussen de `<>` is alle instellingen die de variable bevat. in dit geval is het de boxcollider.

`boxCol.isTrigger = false;` hier roepen wij de variable `boxCol` op. De `.isTrigger` is de instelling "isTrigger" in de Box Collider rechts in unity(Wow whatttt!?). die zetten wij op `false`. That's it
### public var to other script
boolo.cs
```c#
public class NewBehaviourScript : MonoBehaviour
{
    private blabla lmfaoHi;

    // Start is called before the first frame update
    void Start()
    {
        lmfaoHi = GameObject.Find("Cube").GetComponent<blabla>();
        lmfaoHi.myFloat = 2.5f;
    }

    // Update is called once per frame
    void Update()
    {
        
    }
}
```
**De spicy shit:**
Wat we hier doen is een variable van een ander script oproepen. We beginnen redelijk simpel:
**`private blabla lmfaoHi;`** we maken een Variable aan. Deze variable kan public variable nemen van uit het C# script `blala`. De naam daarvan zal `lmfaoHi` worden in dit script.

**`blaBla = GameObject.Find("Cube").GetComponent<blabla>();`** is een enorm stuk, dus ik deel het op in twee delen:

het eerste deel:
**`lmfaoHi = GameObject.Find("Cube")`** jij zegt hier dat de variable `lmfaoHi` het `GameObject` met de naam `"Cube"` vind.

Het tweede deel:
**`.GetComponent<blabla>();`** zorgt er vervolgens voor dat uit `"Cube"` die je in heet eerste deel gevonden hebt, de component(script in dit geval) Met de naam `blabla` haalt.

**`lmfaoHi.myFloat = 2.5f;`** is heel simpel. aangezien we kunnen zeggen dat `lmfaoHi` gelijk staat aan alle public variables in het component `bla bla`. 

`.myfloat` zegt specifiek tegen welke variable we praten. 
`2.5f;` de `f` staat gewoon voor float. dit moet je doen bij alle float waardes.
## Day night cycle
```c#
public class DayNightSwitch : MonoBehaviour
{
    public float speed;
    public Vector3 baseRotationDirection = new Vector3(4, 30, 17).normalized;
    
    //Start is called before the first frame update
    void Start()
    {
        baseRotationDirection = baseRotationDirection.normalized;
    }
    
    //Update is called once per frame
    void Update()
    {
        transform.Rotate(baseRotationDirection * Time.deltaTime * speed);
    }
}
```
Vergeleken met vorige delen is dit redelijk vanzelfsprekend:
**`public float speed;`** maakt een publieke `float` variable aan met de naam `speed`

**`public Vector3 baseRaotationDirection = new Vector3(4, 30, 17).normalized;`**
Dit is weer een groot stuk tekst dat niet heel veel zegt, maar toch zeggen we het in twee delen:

#vector3
**`public Vector3 baseRotationDirection`**
nieuwe publieke variable die wat nieuws heeft: `Vector3`. Dit is heel simpel gezegd een array van 3 waardes voor een positie. Deze heeft de naam `baseRotationDirection`. een `Vector3` is een [[Fundamentals#Data types|Data type]] specifiek in C#/Unity.

**`new Vector3(4, 30, 17).normalized;`** dit betekend dat je `baseRotationDirection` een `Vector3` meegeeft met de waardes `(4, 30, 17)`. `.normalized;` zorgt ervoor dat je nummers omlaag schaalt en dus tussen 1 en 0 blijven. hij maakt ze dus een comma getal.

dan hebben we:
`baseRotationDirection = baseRotationDirection.normalized;`
Dit is een dubbel check zodat de getallen 100% `.normalized` zijn.

**`transform.Rotate(baseRotationDirection * Time.deltaTime * speed);`**
zoals we in de les geleerd hebben zorgt `transform` ervoor dat wij het component transform in gaan. 
`.rotate` zorgt ervoor dat we kijken naar de XYZ rotate getallen.
zoals eerder besproken `baseRotationDirection` heeft 3 waardes. alle 3 deze waardes gaan `* Time.deltaTime * speed;`
## Other
### how fps works
1 = 1000ms
60fps = 16,6...7ms per frame/input lag. dit is je deltaTime
als je taak langer duurt dan je ms die je hebt = frame drop

### What is .normalized
.normalized = number scaling tussen 1 en 0


### Void Start and void Awake
#voidAwake
void start is het eerste wat runt in je C# script.
void Awake Daarentegen begint voor elke void start in elk script dat je maakt.

void start runt na void awake. Awake unstoppable