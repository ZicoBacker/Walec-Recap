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

