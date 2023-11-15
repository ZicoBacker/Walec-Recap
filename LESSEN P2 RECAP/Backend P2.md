# classes
De eerste les van P2 zijn we aan de slag gegaan met Classes in PHP. Ik begrijp er zelf ook maar half van dus dit is aids om uit te leggen maar ik zal me best doen.

We hebben geleerd om bijvoorbeeld namen zo te laten weergeven
```php
$voornaam = "arjan";

$tussenvoegsel = "de";

$achternaam = "Ruijter";

echo "Volle naam:" + $voornaam + $tussenvoegsel + $achternaam;
```

Met classes gaan we dit irritanter/makkelijker maken. Dat doen we zo:
```php
class Persoon

{

    public $voornaam = "Bert";

    public $achternaam = "Terlingen";
  
    public function __construct($voornaam, $achternaam)
    {
        $this->voornaam = $voornaam;
        $this->achternaam = $achternaam;
    }
}
```
zover ik snap lijkt dit een beetje op C#. Je maakt een `class [naam]` aan. Deze class kan je later terug roepen buiten de class.
- `public $voornaam` is een variable die buiten de class gebruikt kan worden. deze variable heeft de waarde `"Bert"`.
- `public $achternaam` werkt hetzelfde als hierboven.
- Ik heb dus geen idee wat `public function __construct($voornaam, $achternaam)` doet, maar het is belangrijk om het te laten werken?
-  in de brackets hebben we `$this->voornaam = $voornaam`. Hieruit begrijp ik dat `$this` is de class `Persoon`. dit betekend dus dat `$Persoon->voornaam = $voornaam`. dit is alleen zodat je de class kan gebruiken. 
- `$this->achternaam` werkt hetzelfde als hierboven.

Als dit goed gegaan is kan je nu met de class en variable naam, de waarde ophalen.
```php
$persoon1 = new Persoon('Danny', 'Verkerk');
echo $persoon1->voornaam . " " . $persoon1->achternaam .  "<br>";
```
je zegt hier het volgende:
- de variable `$persoon1` is een nieuwe class `Persoon` met de eerste twee waardes `('Danny', 'Verkerk'`);
- nu laten wij op de website `$persoon1->voonaam` zien, dit is `'Danny'`.

De rest is aids en snap ik ook niet.