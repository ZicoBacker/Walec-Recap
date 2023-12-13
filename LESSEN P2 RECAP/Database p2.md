## hoe gebruik ik where?
### start
```mysql
SELECT *
FROM tabel
```
Dit laat alles in de tabel zien. En we gebruiken `WHERE` om te zoeken op specifieke voorwaarden.
### Basic WHERE
```mysql
SELECT *
FROM tabel
WHERE naam = 'jan'
```
Dit laat alle rijen(records) zien waarbij de kolom `naam` = `jan`
### WHERE AND
```mysql
SELECT *
FROM TABEL
WHERE naam = 'jan' AND huisnummer < 10
```
Dit laat alle rijen(records) zien waarbij de kolom `naam` = `jan` EN waarbij de kolom `huisnummer` is kleiner dan 10. 
### WHERE OR
```mysql
SELECT *
FROM TABEL
WHERE naam = 'jan' OR naam = 'gerald'
```
Dit laat alle rijen zien waarbij de kolom `naam` de volgende namen heeft: `jan` OF `gerald`.
### WHERE IN
```mysql
SELECT *
FROM tabel
WHERE naam IN ('jan', 'piet', 'gerald')
```
we gebruiken WHERE IN voor het geval dat je meerdere waardes hebt die moeten verschijnen voor een kolom.
### WHERE NOT
```mysql
SELECT *
FROM tabel
WHERE NOT naam = 'jan'
```
Dit laat alle rijen zien waarbij de kolom `naam` niet `jan` is. een alternatief om te gebruiken is: 
`WHERE naam <> 'jan'`. Dit word alleen niet aangeraden. Bij **WHERE IN** moetje NOT gebruiken.
### Leeg veld
```mysql
SELECT *
FROM tabel
WHERE naam is NULL;
```
dit laat alleen de rijen zien waar de kolom `naam` leeg is. je kan niet `= NULL` gerbruiken. `NULL` betekend dat het veld leeg is.
### WHERE LIKE
```mysql
SELECT *
FROM tabel
WHERE NAAM LIKE 'J%'
```
Dit laat alle rijen zien waarbij de kolom `naam` begint met `j`. De `%` staat voor alles. bijvoordbeeld `j%` betekend dat na de `J` alles erachter mag komen. `%k` betekend er van alles mag staan zolang de `K` er op het eind staat. `_` doet hetzelfde als `%`, maar dan voor maar een letter/nummer/teken.
### WHERE BETWEEN
```mysql
SELECT *
FROM TABEL
WHERE huisnummer BETWEEN 10 AND 50
```
Dit laat alle rijen zien waarbij de kolom `huisnummer` een getal heeft tussen `10` en `50`.
## uitbreiden van kolommen
Je kan ook sommen maken met kolommen. Dit gaat als volgt:
```mysql
SELECT naam, 
huisnummer, 
huisnummer + 5
FROM tabel
```
dit zal de rijen `naam` `huisnummer` en `huinummer` maar het huisnummer heeft er plus 5 bij. De kolom heet dan ook wat je gedaan hebt: `huisnumer + 5`
### Rename kolom
```mysql
SELECT naam,
huisnummer,
huisnummer + 5 AS NieuwHuis
FROM tabel
```
Dit zal het volgende laten zien: `naam` `huisnummer` `NieuwHuis`. `NieuwHuis` zal de zelfde rij als `huisnummer` laten zien maar met +5 erbij. Je kan dus rekensommen maken met je tabellen.
### Afronden getallen
```mysql
SELECT NAAM,
SCHULD,
ROUND(SCHULD * 2.25,2) AS SCHULD_2024
FROM tabel
```
dit laat de rijen `naam` `schuld` en `schuld_2024` zien. we gebruiken `ROUND()` om de berekning `SCHULD * 2.25` af te ronden op `2` commagetallen. Als je de min in gaat rond je af op tien, honderd, duizentallen, ect.

### Afkappen getallen
Het verschil tussen afronden en afkappen is dat afkappen niet afrond. het veranderd de getallen gewoon naar 0. Dit is een voorbeeld:
```mysql
SELECT NAAM,
SCHULD,
TRUNCATE(SCHULD * 2.25,2) AS SCHULD_2024
FROM tabel
```
### Samenvoegen tekst
```mysql
SELECT CONCAT(naam, adres, postcode, plaat) AS gegevens
FROM tabel
```
Dit zal de kolommen `naam adres postcode plaat` als een kolom weergeven met de naam `gegevens`. De tekst zal dus ook direct aan elkaar geplakt worden. Om er spaties tussen te stoppen kan je  `CONCAT(naam, " , ", adres, " , ", postcode, " , ", plaats)` gebruiken. Dit zet er ook meteen comma's tussen.
### IF/IFNULL
Dit werkt redelijk hetzelfde als in elke andere programmeertaal. de syntax(hoe je het commando gebruikt) is:
`if(waarde1<>=! waarde2, if-true code, if-false code`
## Limit en Offset
```mysql
SELECT *
FROM tabel
LIMIT 15
```
Dit laat alleen de eerste 15 rijen zien in `tabel`.

Zonder `limit` kan je geen `offset` gebruiken. Je moet dus ook eerst een `limit` hebben. dit kan je op twee manier doen:
```mysql
-- manier 1 (de standaard)
SELECT *
FROM tabel
LIMIT 15 OFFSET 30

-- manier 2
SELECT *
FROM tabel
LIMIT 15, 30
```


## kkr grote sheet:
```mysql
-- basic where
SELECT *
FROM tabel
WHERE naam = 'jan';

-- WHERE AND
SELECT *
FROM TABEL
WHERE naam = 'jan' AND huisnummer < 10;

-- WHERE OR
SELECT *
FROM TABEL
WHERE naam = 'jan' OR naam = 'gerald';

-- WHERE IN
SELECT *
FROM tabel
WHERE naam IN ('jan', 'piet', 'gerald');

-- WHERE NOT
SELECT *
FROM tabel
WHERE NOT naam = 'jan';

-- WHERE NULL
SELECT *
FROM tabel
WHERE naam is NULL;

-- WHERE LIKE
SELECT *
FROM tabel
WHERE NAAM LIKE 'J%';

-- WHERE BETWEEN
SELECT *
FROM TABEL
WHERE huisnummer BETWEEN 10 AND 50;

-- SOMMEN IN TABEL
SELECT naam, 
huisnummer, 
huisnummer + 5
FROM tabel;

-- RENAME KOLOM
SELECT naam,
huisnummer,
huisnummer + 5 AS NieuwHuis
FROM tabel;

-- ROUND
SELECT NAAM,
SCHULD,
ROUND(SCHULD * 2.25,2) AS SCHULD_2024
FROM tabel;

-- AFKAPPEN (TRUNCATE)
SELECT NAAM,
SCHULD,
TRUNCATE(SCHULD * 2.25,2) AS SCHULD_2024
FROM tabel;

-- Het verschil tussen truncate en round is dat truncate niet afrond en gewoon afkapt.
-- Combine columns
SELECT CONCAT(naam, adres, postcode, plaat) AS gegevens
FROM tabel;

-- IF
if(waarde1 <>=! waarde2, if-true code, if-false code);

-- LIMIT
SELECT *
FROM tabel
LIMIT 15;

-- LIMIT AND OFFSET
-- manier 1 (de standaard)
SELECT *
FROM tabel
LIMIT 15 OFFSET 30

-- manier 2
SELECT *
FROM tabel
LIMIT 15, 30

-- om offset te gebruken **MOET** je een limit hebben!!!!!
```
# Using group by with aggregate
we can use `avg() count() max() min() sum()` to do math for us in Database. To have these things show up for each specific field we can use `GROUP BY` for example
```mysql
SELECT plaats, SUM(sal)
FROM werknemer
GROUP BY plaats
```
This would show every `sum` of `sal` for each `plaats` instead of just showing one `plaats` and `sal`.
# GROUP by with HAVING MYSQL
`HAVING` is heel simpel gezegt een `WHERE` voordat je gegevens gaat groeperen. 

**b.v.** als je wil weten in welke gemeenten he gemiddelde inkomen van medewerkers minder is dan € 3500,-. Hiervoor moet eerst het gemiddelde inkomen berekend worden. Het is dus niet mogelijk om al op voorhand een `SELECT` te maken, want zowel het totaal van de salarissen als het aantal rijen dat per gemeente aanwezig is, zijn pas bekend als alle rijen verwerkt en `GROUP BY` zijn.
De oplossing hiervoor is `HAVING`. Deze werkt op dezelfde manier als `WHERE`, maar dan met de resultaten van de groepering.

## Syntax
```MYSQL
SELECT
    soh.customerid,
    YEAR(soh.orderdate) AS orderyear,
    ROUND(SUM(sod.linetotal), 2) AS yearlyrevenue
FROM salesorderheader soh
LEFT JOIN salesorderdetail sod
    ON sod.salesorderid = soh.salesorderid
WHERE YEAR(orderdate) IN (2001, 2003)               -- Alleen 2001 en 2003 selecteren
GROUP BY soh.customerid, YEAR(soh.orderdate)
HAVING yearlyrevenue > 50000                        -- jaarlijkse omzet > € 50.000.-
ORDER BY soh.customerid, YEAR(soh.orderdate)
LIMIT 25;
```
 we zeggen hier dat we van de database `salesorderheader soh` willen zien en van de sod database een left join willen van `salesorderdetail sod`. Hierin willen wij de volgende kolommen zien: `soh.customerid`,  `soh.orderdate` met de naam `orderyear`, `sod.linetotal` met de naam `yearlyrevenue`.  de `sod/soh.[tabelnaam]` is omdat we twee databases gebruiken en we dus duidelijk aan moeten geven welke database wij gebruiken. We willen alleen de informatie tussen `2001` en `2003` zien dus daarom gebruiken we `WHERE orderdate IN ()`. Dit kan omdat het een `date` variable is. Daarna groeperen wij eerst op `soh.customerid` en daarna op `soh.orderdate`. Hij laat ze alleen zien als de `yearlyrevenue` groter is dan 50.000. 

**Tip** je kan zien dat `HAVING` pas uitgevoerd word na de verwerking omdat het `yearlyrevenue` gebruikt. Dit kan alleen nadat hij verwerkt is.