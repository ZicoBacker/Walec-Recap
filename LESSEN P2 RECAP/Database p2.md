# zoeken op meerdere voorwaarden
```mySQL
USE klanten;

SELECT naam, telefoonnr
FROM tblKlant
WHERE Plaats = 'Amsterdam'
AND kredietlimiet > 1000;
```
Het gaat om het gedeelte WHERE. Je kan hiermee gegevens laten zien als ze aan specifieke eisen voldoen. 
in dit geval van de code laat hij alleen de naam en telefoon zien van de tblKlant tabel bij wie de plaats  'Amsterdam' is en kredietlimiet > 1000 is.

## Je wil iets NIET zien
Zoals je kan gokken werkt dit bijna hetzelfde alleen moet je nu `NOT` gebruiken.
```mySQL
SELECT naam, telefoonnr
FROM tblKlant
WHERE NOT Plaats = 'Amsterdam';
```

# leeg veld
Als een veld in een database leeg blijft, zal dit zichtbaar zijn door de tekst **NULL**. Dit is hoe je ervoor zoekt:
```mySQL
SELECT *
FROM werknemer
WHERE voorvoegsel = NULL;
```
`NULL` in dit geval heeft geen haakjes nodig, Het is geen string waar we naar zoeken. `NULL` betekend dat het vakje leeg is.

# LIKE
Als je bijvoorbeeld alle klanten wilt zien waarvan de naam begint met de letter ‘F’, dan kun je het onderstaande statement gebruiken.
```mySQL
SELECT naam 
FROM tblKlant
WHERE naam LIKE 'F%';
```
het `%` teken in dit geval staat voor dat er van alles achter mag zolang het met een F begint.
je kan ook `_` gebruiken. dit is dan voor maar een teken.
# Between
**Voorbeeld:**
Als je wil weten welke klanten een kredietlimiet tussen de 5000 en 10000 euro hebben, kun je dat met de volgende query opvragen:
```mySQL
SELECT klantnr, kredietlimiet
FROM tblKlant
WHERE kredietlimiet BETWEEN 5000 AND 10000;
```
we zeggen hier dat `kredietlimiet` letterlijk tussen 5000 en 10000 moet zijn om hem te laten zien.

# Simpele kolombewerking
Tot nu toe hebben we steeds alleen de inhoud van kolommen getoond. Maar je kan ook bewerkingen uitvoeren op kolommen. Maar wat je dus ook kan doen is dit:
```mySQL
SELECT
    kredietlimiet, 
    rentepercentage, 
    kredietlimiet + 50
FROM tblKlant;
```
Dit is wat het dan laat zien:
![[Pasted image 20231116190831.png]]
Alles is met 50 omhoog gegaan.

Als je dan nog je kolom een andere naam wil geven kan dat ook:
```mySQL
SELECT
    kredietlimiet, 
    rentepercentage, 
    kredietlimiet + 50 AS nieuwe_kredietlimiet
FROM tblKlant;
```

# afronden
Om iets af te ronden in mySQL(database) gebruiken we ROUND, je doet dan:
```mySQL
ROUND(tabel,getallen achter comma) as kolomnaam;
```

## afkappen
je kan ook het comma getal gewoon afkappen( zonder af te ronden).
dan gebruiken we TRUNCATE, dat is op dezelfde manier als round:
```mysql
TRUNCATE(tabel,getallen achrer comma) as kolomnaam;
```

een goed voorbeeld:
```mysql
SELECT 
    kredietlimiet, 
    rentepercentage, 
    ROUND(kredietlimiet * rentepercentage/100, 2) AS rente
FROM tblKlant;
```
# Samenvoegen van tekst
om meerdere kolommen als een kolom te weergeven kunnen wij `CONCAT` gebruiken. Een voorbeeld
```MySQL
SELECT
    CONCAT(naam, adres, postcode, plaats) AS klant_gegevens
FROM tblKlant;
```

Je ziet dat alle kolommen aan elkaar geplakt zijn zonder spatie tussen bijvoorbeeld naam en adres. Dit los je op door een stukje tekst toe te voegen. In dit geval ", ", zodat de velden herkenbaar gescheiden zijn.
```MySQL
SELECT
    CONCAT(naam, ', ', adres, ', ', postcode, ' ', plaats) AS klant_gegevens
FROM tblKlant;
```
alles tussen de `''` zal als tekst weergeven worden. Je kan dus ook letters toevoegen.