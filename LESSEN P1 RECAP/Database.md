# Het maken van een database en tabellen
Om ook maar iets te doen moet je een database hebben. Gelukkig kunnen wij die aanmaken. om dit te doen in [[Installeren#SQL Workbench|SQL Workbench]] moet je eerst [[Installeren#WAMP|WAMP]] aan hebben staan. dit is omdat de SQL Workbench een server nodig heeft om je databases te hosten. Dit zit in WAMP.
## database maken
Om een database te maken doe je door het volgende in een SQL script te zetten:
```mySQL
USE master;
create database database1;
```
je hebt nu een database gemaakt in mySQL Workbench. Alleen is de database nog leeg, er staat niks in. een structuur van een database ziet eruit als volgt:
**database**
	**TABEL1**
		Record1
		Record2
		Record3
	**TABEL2**
		Record1
		Record2
		Record3
	**TABEL3**
		Record1
		Record2
		Record3
## tabel maken
Dus nu moeten we een tabel maken in de database. Dit ziet er als volgt uit in een SQL script:
```mySQL
USE database1;
CREATE TABLE tabel1(
ID int,
naam varchar(32),
adres varchar(32),
Datum date,
isActive bool
);
```
- Om een tabel te maken gebruik je het commando `CREATE TABLE [tabelnaam]` en begin je met `(`
- Alles tussen `()` zal een kolom zijn in de tabel.
- om een kolom aan te maken doe je het volgende `[naam] [datatype]`. [[Fundamentals#Data types|data types]]
- wanneer je al je kolommen hebt sluit je af met `);`
## Tabellen wijzigen
soms wil je later een veld toevoegen in je tabel, of de soort waarde dat hij gebruikt aanpassen.
Ik laat je zien hoe:
```mysql
-- om een kolom in een tabel te verwijderen
ALTER TABLE tabel1
DROP COLUMN naam,
ADD COLUMN naam varchar(32),
RENAME COLUMN naam TO name,
MODIFY COLUMN naam varchar(5);
```
Je Begint altijd met `ALTER TABLE [tabelnaam]` als je een kolom wil aanpassen. Daarnaast heb je een paar dingen die je aan kan passen:
- `DROP COLUMN` verwijderd je een kolom.
- `ADD COLUMN [kolomnaam] [datatype(aantal tekens)]` dit maakt een nieuwe kolom aan.
- `RENAME COLUMN [kolomnaam] TO [kolomnaam]` veranderd de naam van je kolom.
- `MODIFY COLUMN [kolomnaam] [nieuw datatype(aantal tekens)]` laat je het datatype veranderen.
## Records toevoegen
Als het goed is heb je nu dan een tabel met een paar kolommen erin. Maar we hebben niks meer. we hebben nog geen data, nog geen records zoals dat heet in database. Om "records" toe te voegen gebruiken wij het volgende:
```mySQL
USE database1;
INSERT INTO tabel1 VALUES (1,"Zico", "boomstraat 45", 2020-1-1, True);
```
- `INSERT INTO tabel1` zeggen dat we een record willen toevoegen aan `tabel1`. 
- `VALUES` is voor de waarde op volgorde van de kolommen. in Dit geval is de volgorde: ID, naam, adres, Datum, IsActive.
- `()` hiertussen vul je je waardes in met een komma tussen elke waarde.
- sluit af met een `;`
# Database records opvragen
Een database gebruiken we om handig en snel informatie op te slaan. Maar hoe zien we nou alle informatie die we erin hebben staan? dit gaat als volgt
## SELECT
SELECT is een commando die je in elke opdracht gaat gebruiken die te maken heeft met records opvragen.
```MySQL
SELECT id, naam 
FROM tabel1
WHERE id = 1
ORDER BY datum ;
```
- `SELECT` Zegt welke hij terug gaat laten zien, in dit geval zal hij alle record van `id` en `naam` laten zien
- `FROM` is voor uit welke tabel, hier is dat `tabel1`
- `WHERE` is om te zorgen dat hij specifieker gaat zoeken. hij laat alleen de record zien van `id` en `naam` in dit geval waarbij het `id` van het record `1` is.
- `ORDER BY` geeft aan op welke volgorde hij als je data zet, ik heb hier gezegd op volgorde van `datum`.

Dit is voor deze periode het meest uitgebreid dat je `SELECT` kan worden.

## UPDATE en DELETE
we hebben geleerd [[Database#Tabellen wijzigen|hoe we tabellen wijzigen|]] en nu leren we hoe we records wijzigen. Dit is redelijk eenvoudig:

### Update
```mySQL
UPDATE tabel1
SET id = id + 1
WHERE naam = "johan";
```
Dit is een gemiddelde UPDATE query
- `UPDATE tabel1` vraagt uit welke tabel je gegevens wil aanpassen
- `SET id = id + 1` zegt dat hij het de kolom `id` eentje omhoog doet
- `WHERE naam = "johan";`  hij zegt hier dat hij alleen alles erboven doet waar de `naam` `johan` is.

### Delete
```mySQL
DELETE FROM tabel1
WHERE naam = "johan";
```
En dit is een gemiddelde DELETE query
`DELETE FROM tabel1` spreek voor zichzelf. Je gaat een record verwijderen uit `tabel1`.
`WHERE naam = "johan"` zegt dat hij alle records verwijderd waarbij de `naam` `johan` is.