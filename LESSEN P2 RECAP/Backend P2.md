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
In backend zijn we aan de slag gegaan met het gebruiken van een database in PHP. Wij maken een database aan via phpmyadmin of mysql, wat wij gebruiken bij database. Ik ga hier de uitleg geven voor hoe je het doet met mySQL maar het werkt bijna hetzelfde met phpmyadmin. We maken een connectie tussen een database en de php website.

### Maken van de database
Wij hebben bij database geleerd hoe wij een database maken. Dit ging als volgt:
``` MySQL
-- maken van de database en die gebruiken:
CREATE DATABASE Opdracht_database;
USE Opdracht_database;

-- maak een tabel aan in de database die wij later kunnen vullen
CREATE TABLE Cars (
    id int(10) NOT NULL AUTO_INCREMENT,
    Merk varchar(200) NOT NULL,
    Model varchar(200) NOT NULL,
    Topsnelheid smallint(5) UNSIGNED NOT NULL,
    Prijs int(11) NOT NULL,
    PRIMARY KEY (`id`) -- Dit betekend dat id uniek moet zijn en dat het een "connectiepunt" is.
) ENGINE=INNODB CHARSET=latin1; -- geen Idee wat het doet maar het laat het werken.
```
Dit script voer je dan uit in je MySQL workbench (je moet WAMP aan hebben staan om dat te doen).

Alleen nu is de database nog leeg, we gaan hem vullen. Dit doe je als volgt:
```MySQL
INSERT INTO Cars(Merk, Model,Topsnelheid,Prijs) VALUES ("Bugatti", "La vioture noire", "420", "16500000");

INSERT INTO Cars(Merk, Model,Topsnelheid,Prijs) VALUES ("Rolls-Royce", "Swaptail", "250", "10960000");

INSERT INTO Cars(Merk, Model,Topsnelheid,Prijs) VALUES ("Bugatti", "EB110", "390", "7500000");

INSERT INTO Cars(Merk, Model,Topsnelheid,Prijs) VALUES ("Mercedes-Benz", "Maybach Exelero", "350", "6700000");

INSERT INTO Cars(Merk, Model,Topsnelheid,Prijs) VALUES ("koenigsegg", "CCXR Trevita", "401", "4000000");
```
je ziet hier na cars: 
(Merk, Model,Topsnelheid,Prijs). 
Dit betekend dat je alleen die velden invult. `Id` geeft zichzelf al een waarde die automatisch met 1 omhoog gaat via `AUTO_INCREMENT`.

Nu heb je een volledig werkende database met waardes erin. Het hele script ziet er zo uit:
```MySQL
CREATE DATABASE crud_php_pdo_opdracht;
USE crud_php_pdo_opdracht;

CREATE TABLE Cars (
    id int(10) NOT NULL AUTO_INCREMENT,
    Merk varchar(200) NOT NULL,
    Model varchar(200) NOT NULL,
    Topsnelheid smallint(5) UNSIGNED NOT NULL,
    Prijs int(11) NOT NULL,
    PRIMARY KEY (`id`)
) ENGINE=InnoDB CHARSET=latin1;

INSERT INTO Cars(Merk, Model,Topsnelheid,Prijs) VALUES ("Bugatti", "La vioture noire", "420", "16500000");
INSERT INTO Cars(Merk, Model,Topsnelheid,Prijs) VALUES ("Rolls-Royce", "Swaptail", "250", "10960000");
INSERT INTO Cars(Merk, Model,Topsnelheid,Prijs) VALUES ("Bugatti", "EB110", "390", "7500000");
INSERT INTO Cars(Merk, Model,Topsnelheid,Prijs) VALUES ("Mercedes-Benz", "Maybach Exelero", "350", "6700000");
INSERT INTO Cars(Merk, Model,Topsnelheid,Prijs) VALUES ("koenigsegg", "CCXR Trevita", "401", "4000000");
```
### Config.php
Je config.php is eigenlijk niks meer dan een plek waar je je inlog gegevens van je database in stopt. Dit zet je apart omdat je het vaker nodig hebt en het is makkelijk als je alles op een plek heb staan zodat het makkelijk aan te passen is. Een simpele manier ervan ziet er zo uit:
```php
<?php
$dbHost = 'localhost'; //kan je ook gewoon laten
$dbName = 'DataBase Name'; //verander dit naar je database naam.
$dbUser = 'root'; //Kan ook je gewoon laten
$dbPass = ''; //kan je ook gewoon laten
?>
```
Ja, dat is alles wat je er in hoef te stoppen.  Dit gaan wij terug roepen in de [[Groeps recap P2#Index.php|index]] En [[Groeps recap P2#NewRecord.php|NewRecord script]].
### Index.php
De index in php werkt bijna hetzelfde als de index in html. je begint met een standaard pagina.
```php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Crud-php-pdo-opdracht</title>
</head>
<body>
    <h1>De fijv duurste auto`s ter wereld</h1>
</body>
</html>
```

Nu gaan wij dus data op moeten halen vanuit de database. 
Wij openen een php script tag boven het hele HTML gedeelte en include de config:
``` php
//!!!!!!!
<?php
include('config/config.php');
?>
//!!!!!!!

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Crud-php-pdo-opdracht</title>
</head>
<body>
    <h1>De fijv duurste auto`s ter wereld</h1>
</body>
</html>
```
Nu kunnen wij dus de variabelen die wij gemaakt hebben in `config.php` gebruiken.

Nu maken wij een variable aan `$dsn`. Dit staat voor [Data Source Name](https://www.php.net/manual/en/pdo.construct.php#:~:text=Parameters%20¶-,dsn,PDO%20driver-specific%20connection%20syntax.) (hoef je niet te weten). Hierin stoppen wij alle informatie over de database:
```php
<?php
	include('config/config.php');
	 $dsn = 'mysql:host=$dbHost;
			 dbname=$dbName;
			 charset=UTF8;';
?>
```

Dan maken wij een nieuwe `PDO` variable. dit staat voor [PHP Data Object](https://www.allphptricks.com/php-crud-pdo-prepared-statements/#:~:text=CRUD%20stands%20for%20Create%2C%20Read,for%20accessing%20databases%20in%20PHP.). Hierin stoppen wij DSN en je login en wachtwoord variable:
```php
 include('config/config.php');

 $dsn = "mysql:host=$dbHost;
         dbname=$dbName;
         charset=UTF8;";

 $pdo = new PDO($dsn,$dbUser,$dbPass);
```

je hebt nu een soort connectie gelegd tussen jou database en de PHP webite. Maar je roept nog niks op. Om wat op te roepen gebruiken wij SQL 'Queries' die wij geleerd hebben bij database. Om bijvoorbeeld een tabel te laten zien moeten wij een sql query maken die alle data selecteerd. Wees hier specifiek in wanneer je aan de slag gaat op een website. We beginnen met het maken van een `$SQL` variable met onze query:
```php
$sql = "SELECT id,
         Merk,
         Model,
         Topsnelheid,
         Prijs
         FROM Cars
         ORDER BY Prijs DESC";
```
Dit selecteerd dus eigenlijk alles uit de tabel en zet op rij van prijs hoog naar laag.

Nu wij de query hebben gaan we deze voorbereiden om naar de database te sturen en informatie terug te krijgen. Dat gaat als volgt:
```php
$statement = $pdo->prepare($sql);
```

En dan voeren wij de query uit:
```php
$statement->execute();
```

Nu hebben wij de statement uitgevoerd en zal de database informatie opsturen. Wij moeten deze informatie als het ware een soort van opvangen. dit doe je door een `$result` variabele aan te maken:
```php
$result = $statement->fetchAll(PDO::FETCH_OBJ);
```

Oke we hebben nu dus de informatie in `$result` alleen staat dit erin als een object(`OBJ`). Dit moeten wij nu uit gaan werken als een tabel. Dit is wat je nu zou moeten hebben in je `<?php ?>`:
```php
<?php
 include('config/config.php');

 $dsn = "mysql:host=$dbHost;
         dbname=$dbName;
         charset=UTF8;";

 $pdo = new PDO($dsn,$dbUser,$dbPass);

 $sql = "SELECT id,
         Merk,
         Model,
         Topsnelheid,
         Prijs
         FROM Cars
         ORDER BY Prijs DESC";

 $statement = $pdo->prepare($sql);

 $statement->execute();

 $result = $statement->fetchAll(PDO::FETCH_OBJ);
 ?>
```

Om het uit te werken gaan we een nieuwe variabele maken genaamd `$TableRows` met niks erin:
```PHP
$TableRows = "";
```

Nu stoppen wij `$result` in een foreach loop en zorgen wij dat het voor elke rij zijn Id, merk, model, ect verwerkt:
```PHP
foreach ( $result as $car) {
    $TableRows .= "<tr>
                        <td>$car->id</td>
                        <td>$car->Merk</td>
                        <td>$car->Model</td>
                        <td>$car->Topsnelheid</td>
                        <td>$car->Prijs</td>
                    </tr>";
 }
```
Lastig uit te leggen maar met `($result as $car)` zeggen wij dat in deze foreach loop `$result` `$car` is. zoals eerder besproken is `$car` een object. Om informatie uit een object te halen doe je ->. In dit geval is `.=` erbij toevoegen. Dus wij voegen een nieuwe tabelrij `<tr>` met daarin de `$car->id`, `$car->Merk`, ect.

Vervolgens gaan wij terug naar het HTML deel en maken wij een tabel met daarin deze informatie. Dat gaat zo:
```php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Crud-php-pdo-opdracht</title>
</head>
<body>
    <h1>De fijv duurste auto`s ter wereld</h1>
    <a href="../Create.php">Nieuw Record</a>
    <table>
        <thead>
            <th>Merk</th>
            <th>Model</th>
            <th>Topsnelheid</th>
            <th>Prijs</th>
        </thead>
        <tbody>
            <?php echo $TableRows; ?>
        </tbody>
    </table>

</body>
</html>
```

uiteindelijk zal heel je code er zo uit zien:
```php
<?php
 include('config/config.php');

 $dsn = "mysql:host=$dbHost;
         dbname=$dbName;
         charset=UTF8;";

 $pdo = new PDO($dsn,$dbUser,$dbPass);

 $sql = "SELECT id,
         Merk,
         Model,
         Topsnelheid,
         Prijs
         FROM Cars
         ORDER BY Prijs DESC";

 $statement = $pdo->prepare($sql);

 $statement->execute();

 $result = $statement->fetchAll(PDO::FETCH_OBJ);

 $TableRows = "";
 foreach ( $result as $car) {
    $TableRows .= "<tr>
                        <td>$car->id</td>
                        <td>$car->Merk</td>
                        <td>$car->Model</td>
                        <td>$car->Topsnelheid</td>
                        <td>$car->Prijs</td>
                    </tr>";
 }

?>

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Crud-php-pdo-opdracht</title>
</head>
<body>
    <h1>De fijv duurste auto`s ter wereld</h1>
    <a href="../Create.php">Nieuw Record</a>
    <table>
        <thead>
            <th>Merk</th>
            <th>Model</th>
            <th>Topsnelheid</th>
            <th>Prijs</th>
        </thead>
        <tbody>
            <?php echo $TableRows; ?>
        </tbody>
    </table>

</body>
</html>
```

### Create.php
Wij hebben nu data laten zien uit een database, maar we moeten ook nog data toevoegen. Om data toe te voegen gaan wij een apart webpagina maken.
We maken een hyperlink naar de webpagina:
```php
<h1>De fijv duurste auto`s ter wereld</h1>
    <a href="../Create.php">Nieuw Record</a>
    <table>
```

Op deze webpagina maken wij een forumlier. Wij kunnen de data in de formuliervelden gebruiken:
```php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Add a new record!</title>
</head>
<body>
<form method="post" action="NewRecord.php">
        <label for="Merk">Merk: </label>
        <input type="text" name="Merk" id="Merk"><br><br>

        <label for="Model">Model: </label>
        <input type="text" name="Model" id="Model"><br><br>

        <label for="Topsnelheid">Topsnelheid: </label>
        <input type="text" name="Topsnelheid" id="Topsnelheid"><br><br>

        <label for="Prijs">Price: </label>
        <input type="Text" name="Prijs" id="Prijs"><br><br>

        <input type="submit" value="Verzend" name="submit">
    </form>
</body>
</html>
```
Let op, `<form method="post" action="NewRecord.php">` is van belang. De action geeft aan naar welke website we gaan en post is de methode. **method MOET post zijn** en action is je volgende pagina waar wij aan de slag gaan met de nieuwe data. **De benaming van je inputs komen later terug**.
### NewRecord.php
In NewRecord gaan wij geen webpagina maken, we gaan alleen een script gooien die alle informatie verwerkt in de database. Een groot deel van dit is hetzelfde als `index.php` dus ik ga snel over het eerste deel heen. 
We beginnen met de `<?php ?>` basis opzetten:
```php
<?php
include('config/config.php');

$dsn = "mysql:host=$dbHost;
         dbname=$dbName;
         charset=UTF8;";

 $pdo = new PDO($dsn, $dbUser, $dbPass);
 ?>
```

Nu doen we wat nieuws, wij spreken namelijk direct tegen de `METHOD="POST"` die alle ingevulde velden bijhoud en gooien een filter overheen:
```php
$_POST = filter_input_array(INPUT_POST, FILTER_SANITIZE_FULL_SPECIAL_CHARS);
```
Zoals het zegt haat het rare tekens eruit.

Nu maken wij onze query. Dit werkt een beetje anders en we gebruiken ':placeholders'. Dit zijn benamingen die we later een waarde geven:
```php
 $sql = "INSERT INTO Cars(Merk,
                          Model,
                          Topsnelheid,
                          Prijs)
         VALUES          (:Merk,
                          :Model,
                          :Topsnelheid,
                          :Prijs)";
```
Dit is een simpele insert into.

Nu gaan wij de query voorbereiden zoals gewoonlijk:
```php
$statement = $pdo->prepare($sql);
```

Alleen we hebben de placeholders nog staan, Die moeten eruit met de waarde van het formulier. Dit gaat als volgt:
```php
$statement = $pdo->prepare($sql);
 $statement->bindValue(':Merk', $_POST['Merk'], PDO::PARAM_STR);
 $statement->bindValue(':Model', $_POST['Model'], PDO::PARAM_STR);
 $statement->bindValue(':Topsnelheid', $_POST['Topsnelheid'], PDO::PARAM_INT);
 $statement->bindValue(':Prijs', $_POST['Prijs'], PDO::PARAM_INT);
```
we zeggen heel simpel uitgelegd dat `':prijs'` hetzelfde is als `$_POST['prijs']` (**de benaming van eerder**) en dat de variable een `PDO::PARARM_INT` Interger(getal) moet zijn. Hiermeer veranderen wij dus de placeholder naar een daadwerkelijke waarde.

Nadat je dit voor elk vlak heb gedaan is het tijd om de `$statement` uit te voeren. We stoppen nog wat ext op de pagina en een redirect terug naar index.php:
```php
$statement->execute();
echo "Form saved, you will redirected!";
header('Refresh:2.5; url=index.php');
?>
```

en dat is het. Je code ziet er dan zo uit:
```php
<?php
include('config/config.php');

$dsn = "mysql:host=$dbHost;
         dbname=$dbName;
         charset=UTF8;";

 $pdo = new PDO($dsn, $dbUser, $dbPass);

 $_POST = filter_input_array(INPUT_POST, FILTER_SANITIZE_FULL_SPECIAL_CHARS);

 $sql = "INSERT INTO Cars(Merk,
                          Model,
                          Topsnelheid,
                          Prijs)
         VALUES          (:Merk,
                          :Model,
                          :Topsnelheid,
                          :Prijs)";

 $statement = $pdo->prepare($sql);
 $statement->bindValue(':Merk', $_POST['Merk'], PDO::PARAM_STR);
 $statement->bindValue(':Model', $_POST['Model'], PDO::PARAM_STR);
 $statement->bindValue(':Topsnelheid', $_POST['Topsnelheid'], PDO::PARAM_INT);
 $statement->bindValue(':Prijs', $_POST['Prijs'], PDO::PARAM_INT);

 $statement->execute();

 echo "Form saved, you will redirected!";
 header('Refresh:2.5; url=index.php');
?>
```


---
# References

#### What is DSN?
https://www.php.net/manual/en/pdo.construct.php#:~:text=Parameters%20¶-,dsn,PDO%20driver-specific%20connection%20syntax
#### What is PDO?
https://www.allphptricks.com/php-crud-pdo-prepared-statements/#:~:text=CRUD%20stands%20for%20Create%2C%20Read,for%20accessing%20databases%20in%20PHP