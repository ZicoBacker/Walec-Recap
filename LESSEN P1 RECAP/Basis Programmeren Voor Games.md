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
## voorbeeld
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

# 2. Opdrachten
## 1.1
- download het pakket met de unity bestanden en zet `scenes>prototype1` op. maak dan een vehicle aan op position `0, 0, 0`
- plaats een obstacle op position `0, 0, 25`
- sleep een camera en voeg hem toe aan je vehicle
## 1.2
- maak een script door een folder aan te maken en die `scripts` te noemen. Daarin maak je een script genaamd `PlayerController`.
- Open het script en in het `Update` gedeelte van het script stop je het volgende: `transform.Translate(Vector3.forward * Time.deltaTime * 20);`.
- voeg een rigid body toe aan je objecten (`vehicle` en `obstacle`) door op add components te drukkken.![[Pasted image 20231117143808.png]]
- Hierna voeg je het script `PlayerController` toe.
- geef de `rigidBody mass` een waarde in kgs.
- copy paste de obstacles een paar keer met CTRL + D
## 1.3
### Follow player camera
- je maakt een nieuw script aan met de naam `FollowPlayer`
- deze voeg je toe aan je camera.
- vervolgens hernoem jij je camera naar `player`
- je moet het onderstaande in je script hebben: #vector3 
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class FOL : MonoBehaviour
{
    public GameObject player;
    private Vector3 offset = new Vector3(0, 5, -7);
    // Start is called before the first frame update
    void Start()
    {
        
    }

    // Update is called once per frame
    void Update()
    {
        transform.position = player.transform.position + offset;
    }
}
```
Het enige dat we echt toegevoegd hebben is `transform.position = player.transform.position + offset;` we zeggen hier. dat de positie van de camera gelijk staat aan de variable `player` plus de `offset`.
- Sleep vervolgens. je vehicle in je public variable in unity![[Pasted image 20231117150509.png]]
- je kan je unity een kleurtje geven als je je game runt. Dit doe je in `edit>preferences`
## 1.4
Antwoord:
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class GaBewegen : MonoBehaviour
{
    public float speed = 10f;
    public float turnSpeed = 10f;
    public float horizontalInput;
    public float forwardInput;
    // Start is called before the first frame update
    void Start()
    {

    }

    // Update is called once per frame
    void Update()
    {
        horizontalInput = Input.GetAxis("Horizontal");
        forwardInput = Input.GetAxis("Vertical");

        transform.Translate(Vector3.forward * Time.deltaTime * speed * forwardInput);
        transform.Translate(Vector3.right * Time.deltaTime * turnSpeed * horizontalInput);
        transform.Rotate(Vector3.up, turnSpeed * horizontalInput * Time.deltaTime);
        
    }
}
```
wat we hier hebben gedaan is onze inputs toegevoegd. 
- bijna alles is al uitgelegd in [[Basis Programmeren Voor Games#voorbeeld|Het vorige hoofdstuk]]
-  de `transform.Rotate` draait het model.
- `Time.deltaTime`is uitgelegd in [[BPRG verdieping#how fps works|Deltatime]]

# BPRG Thema 2
In thema twee zijn wij aan de slag gegaan met de volgende dingen:
## player position limiting
```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class PlayerController : MonoBehaviour
{
    public float horizontalInput;
    public float speed = 10.0f;
    private float xRange = 10;
    public GameObject projectilePrefab;
    // Start is called before the first frame update
    void Start()
    {
        
    }

    // Update is called once per frame
    void Update()
    {
        horizontalInput = Input.GetAxis("Horizontal");
        transform.Translate(Vector3.right * horizontalInput * Time.deltaTime * speed);

        if (transform.position.x < -xRange) {
            transform.position = new Vector3(-xRange, transform.position.y, transform.position.z);
        }
        if (transform.position.x > xRange)
        {
            transform.position = new Vector3(xRange, transform.position.y, transform.position.z);
        }
```
Dit is een verdieping op de vorige opdrachten. Hierin hebben wij gezegd dat de player niet buiten een specifiek X as mag komen. Hiervoor hebben wij `transform.position = new Vector3(xRange, transform.position.y, transform.position.z);` gebruikt. De variable `xRange` is de waarde waar hij niet buiten mag komen. 

## projectiles
```c#
public float speed = 40;
void Update() {
transform.Translate(Vector3.forward * Time.deltaTime * speed);
} 
```
Wij hebben projectiles aangemaakt, Het script hierboven zorgt ervoor dat het vooruit beweegt. Verderest hebben wij het object toegvoegd aan "prefabs".

## Spawn en Delete objects

```c#
if (Input.GetKeyDown(KeyCode.Space))
{
// Launch a projectile from the player
Instantiate(projectilePrefab, transform.position, projectilePrefab.transform.rotation);
} 
```
Dit is de code in het playerscript die ervoor zorgt dat wij deze pojectielen kunnen in "spawnen". Hiervoor gebuiken we `Instantiate`. de syntax is `Instantiate(object,position, rotation)`.

```c#
private float topBound = 30;
private float lowerBound = -10;
void Update() {
if (transform.position.z > topBound)
{
Destroy(gameObject);
} else if (transform.position.z < lowerBound) {
Destroy(gameObject);
}
} 
```
dit is een nieuw script die ervoor zorgt dat als het object te ver naar boven gaat dat hij "despawned". Dit is belangrijk omdat je anders enorme lag kan veroorzaken. Ook doen we dit voor de onderkant(`topBound` en `lowerBound` respectievelijk.)

## Spawnmanager
een spawnmanager is een object zonder fysieke vorm in unity. Hierin kan je alle scripts toevoegen die gedraaid moeten worden.
```c#
private float spawnRangeX = 20;
private float spawnPosZ = 20;

void Update() {

if (Input.GetKeyDown(KeyCode.S)) {
// Randomly generate animal index and spawn position
Vector3 spawnPos = new Vector3(Random.Range(-spawnRangeX, spawnRangeX), 0, spawnPosZ);

int animalIndex = Random.Range(0, animalPrefabs.Length);

Instantiate(animalPrefabs[animalIndex], spawnPos,
animalPrefabs[animalIndex].transform.rotation); }} 
```
Dit is kneiter volle code maar doet niet veel speciaals. Het zegt dat als jij `S` ingedrukt houd dat hij een van de animal prefabs gaat inspawnen op een locatie tussen `spawnRangeX` en `spawnPosZ`.
Dit object heeft dezelfde rotation als de prefab..

### Randomize Spawns
als je de spawns op random intervals wil hebben kan je dit stukje script gebruiken:
```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class SpawnManager : MonoBehaviour
{
    public GameObject[] animalPrefabs;

    //spawn position parameters
    private float spawnRangeX = 10;
    private float spawnPosZ = 20;

    //spawnintervals for animals
    private float startDelay = 2;
    private float spawnInterval = 1.5f;

    // Start is called before the first frame update
    void Start()
    {
        InvokeRepeating("SpawnRandomAnimal", startDelay, spawnInterval);
    }

    // Update is called once per frame
    void Update()
    {
        if (Input.GetKeyDown(KeyCode.S))
        {
            SpawnRandomAnimal();
        }
    }
    void SpawnRandomAnimal()
    {
        Debug.Log("functie uitgevoerd");

        //Random animal
        int animalIndex = Random.Range(0, animalPrefabs.Length);

        //random spawn position variable
        Vector3 spawnPos = new Vector3(Random.Range(-spawnRangeX, spawnRangeX), 0, spawnPosZ);

        //Spawn object
        Instantiate(animalPrefabs[animalIndex],
            spawnPos,
            animalPrefabs[animalIndex].transform.rotation);
    }
```
nogmaals dit is weer kneiter groot stuk code, maar de helft heb ik al uitgelegd. We hebben van het inspawnen van de prefab een functie gemaakt. Nu zeggen we in de `void Start` dat we de prefabs spawnen op basis van een interval. Deze interval is op basis van dit stuk code: `int animalIndex = Random.Range(0,animalPrefabs.Length);

## Colliders
Dit was hel, je voegd een collider toe aan het object en dan dubbelklikken op de prefab. In de prefab doe jij je collider. dit doe je voor alle prefab( projectile en animals). wij hebben een nieuw script aangemaakt die dan je objecten kapot maakt zodra zij colliden:
```C#
void OnTriggerEnter(Collider other) {
Destroy(gameObject);
Destroy(other.gameObject); } 
```

