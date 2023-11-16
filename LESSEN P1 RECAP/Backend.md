# PHP
## hoe gebruik ik PHP? 
om PHP te gebruiken moeten we eerst [[Installeren#WAMP|WAMP]] geïnstalleerd hebben. Zodra je WAMP geïnstalleerd hebben maak je een `index.php`. In de `index.php` begin je met een basis HTML pagina en moet je `<?php` doen  om te beginnen met PHP scripts. Dit ziet er zo uit.
```PHP
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PHPBasics</title>
</head>
<body>
    <?php

     ?>
</body>
</html>
```
Alles tussen `<?php` en `?>` moet PHP script zijn.
## Basic's
### Variables
in PHP werkt [[Basisprogrammeren#2. wat zijn variables|variables]] maken een beetje anders. Om een variable te maken doe je 
```PHP
$voornaam = "johan";
```
om een variable aan te maken moet je `$` gebruiken, anders werkt hij niet. De rest is hetzelfde.

### Echo
PHP gebruikt `echo` om text op de pagina te weergeven binnen `<?php ?>`.  voorbeeld:
```php
<?php
$voornaam = "johan";
echo "hallo mijn naam is " . $voornaam;
```
Dit zal dus het volgende weergeven: `hallo mijn naam is johan`. Om een variable toe te voegen na een string gebruik je `.` 
### Sommen
in PHP kan je in de `echo` sommen maken.
```php
<?php
$getal1 = 15;
$getal2 = 10;
echo "het getal van de rekensom is" . $getal1 + getal2;
?>
```
### If/Else
Dit is hoe je If/Else statements maakt in PHP
```php
<?php
$isActive = true;
if ($isActive = true) {
echo 'active';
}
else {
echo 'false';
}
?>
```

### Arrays
In PHP heb je arrays, zie dit voor je als een variable met een meerdere waarde op een rij
```php
<?php
$snacks = array("Mars", "Twix", "Snickers");
?>
```
om in PHP een array te maken moet je dit aangeven. dit doe je door `= array();` te gebruiken. Het ziet er ongeveer zo uit voor de computer
```
$snacks = array(
getal 0 => Mars
getal 1 => Twix
getal 2 => snickers
)
```

Als je iets in een array aan wil roepen:
```php
<?php
$snacks = array("Mars", "Twix", "Snickers");
echo $snacks[0];
?>
```
`echo $snacks[0];` zegt eigenlijk dat hij de waarde uit de array `$snacks` pakt op plek 0, dat is `Mars`.
## Verdiept (moet je wel weten)
### Foreach Arrays
Je kan de foreach loop gebruiken om alles uit een array te typen.
```php
<?php
$snacks = array("Mars", "Twix", "Snickers");
foreach ($snacks as $index => $value) {
	echo "op nummer " . $index . " staat " . $value; 
}
?>
```
foreach zegt hier dat in de array `snacks` de getallen nu `$index` heten en de waardes `$value` heten. Vervolgens doe hij alles tussen `{}` keer het aantal waardes dat de array `snacks` heeft.

### Arrays Expanded
zoals je weet hebben arrays een `getal => waarde`. Je kan dit ook aanpassen.
```php
<?php
$naw = array(
	"firstname" => "Zico",
	"achternaam" => "Backer",
	"zipcode" => "2345AB"
)
?>
```
de computer ziet de array ook op deze manier. Nu heb je dus geen getallen meer ervoor, dat is vervangen door `"firstname"` ect.

### Nested arrays
Nested arrays betekend eigenlijk niks anders dan een array in een array. Hier heb je Arejens voorbeeld:
```php
<?php
$personen = array(array("firstname" => "Arjan",
                        "infix" => "de",
                        "lastname" => "Ruijter",
                        "address" => "Prins Hendrikstraat",
                        "addressnumber" => 17,
                        "zipcode" => "1901CB"),
                                    
                  array("firstname" => "Bert",
                        "infix" => "van der",
                        "lastname" => "Steeg",
                        "address" => "Willem de Zwijgerlaan",
                        "addressnumber" => 253,
                        "zipcode" => "1051XM"),
                                    
                  array("firstname" => "Mohammed",
                        "infix" => "El",
                        "lastname" => "Yassidi",
                        "address" => "Admiraal de Ruijterweg",
                        "addressnumber" => 68,
                        "zipcode" => "1067RC"));
?>
```
in deze Nested array maken wij ook gebruik van wat we geleerd hebben in [[Backend#Arrays Expanded(|arrays Expanded]]. Het ziet er ongeveer zo uit voor de computer:
```php
<?php
$personen = array(
		  getal1=>array("firstname" => "Arjan",
                        "infix" => "de",
                        "lastname" => "Ruijter",
                        "address" => "Prins Hendrikstraat",
                        "addressnumber" => 17,
                        "zipcode" => "1901CB"),
                                    
          getal2=>array("firstname" => "Bert",
                        "infix" => "van der",
                        "lastname" => "Steeg",
                        "address" => "Willem de Zwijgerlaan",
                        "addressnumber" => 253,
                        "zipcode" => "1051XM"),
                                    
          getal3=>array("firstname" => "Mohammed",
                        "infix" => "El",
                        "lastname" => "Yassidi",
                        "address" => "Admiraal de Ruijterweg",
                        "addressnumber" => 68,
                        "zipcode" => "1067RC"));
?>
```

Als je dit zou willen gebruiken in een foreach loop ziet dat er zo uit:
```php
foreach ($personen as $name => $value) {
	echo "------------------------------------<br>"
	.$value['firstname'] . " " . $value['infix'] . " " . $value['lastname'] . "<br>"
	. $value['address'] . " " . $value['addressnumber'] . "<br>"
	. $value['zipcode']
	. "<br>";
 }
```

### Functies
Om een andere PHP pagina zonder html indeling te linken.  kan je dit bovenaan je PHP pagina stoppen(buiten de HTML)
```php
<?php include('../functions/functions.php'); ?>
```

[[Basispogrammeren P2#functies maken|Functies]] in PHP werken redelijk hetzelfde als functies in andere programmeertalen.
een voorbeeld van een simpele plus som functie:
```php
<?php
function som($getal1, $getal2) {
	$som = $getal1 + $getal2;
	return "De som van $getal1 + $getal2 = " . $som . "<br>";
 }
?>
```

### ElseIf
ElseIf is een verdieping op [[Backend#If/Else|If Else]] van een stukje terug. Het geeft je meer mogelijkheden voor een variable. Hier is weer een voorbeeld van arejen:
```php
<?php
$userrole = 'moderator';
    if ($userrole == 'administrator') {
        echo "Welkom terug administrator<br>";
        
    } elseif ($userrole == 'customer') {
        echo "Welkom terug customer<br>";
    
    } elseif ($userrole == 'moderator') {
        echo "Welkom terug moderator<br>";
    
    } else {
        echo "Welkom terug<br>";
    }
?>
```
Wat hier gebeurt is redelijk simpel
- `$userrole = 'moderator'` spreekt voor zichzelf.
- `if ($userrole == 'administrator') {}` dan doet hij alles tussen `{}`
- `elseif ($userrole == 'customer') {}` je gebruikt `elseif` als je meer dan twee opties wil hebben.
- `else {}` moet altijd als laatst. 
