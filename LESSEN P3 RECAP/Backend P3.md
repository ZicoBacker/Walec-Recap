# MVC framework
## Rewrite module moet werken
gooi ff double check of rewrite_module aan staat. Dit vind je in apache > apache modules >
## .htaccess configs
Voeg de `apache conf` extension toe voor code highlight.
Om index.php aan te spreken meteen wanneer hij in een andere folder staat moeten wij de volgende .htaccess toevoegen zodat het weer werkt.

.htaccess config in root:
```.htaccess
<IfModule mod_rewrite.c>
    RewriteEngine On
    RewriteRule ^$ public/ [L]
    RewriteRule (.*) public/$1 [L]
</IfModule>
```

.htaccess in the public folder:
```.htaccess
<IfModule mod_rewrite.c>
    Options -Multiviews
    RewriteEngine On
    RewriteBase /public
    RewriteCond %{REQUEST_FILENAME} !-d
    RewriteCond %{REQUEST_FILENAME} !-f
    RewriteRule ^(.+)$ index.php?url=$1 [QSA,L]
</IfModule>
```
## Framework structure
Wij zullen de index.php leeg laten, en alles in de app folder stoppen. Alles wat je in je index.php hebt staan is `require_once '../app/require.php';`. 
In de `require.php` gaan wij exact hetzelfde doen: 
```php
require_once 'libraries/Core.php';
require_once 'libraries/BaseController.php';
require_once 'libraries/Database.php';
require_once 'helpers/functions.php';
require_once 'config/config.php';
```
Voor duidelijkheid: het verschil tussen `require` en `require_once` is dat `require_once` checkt of het bestand al is opgehaald, en het niet nog is doet als dat het geval is.
**In mvc gebruiken de zelfde curly bracket conventie die wij gebruiken in c#.**
## Constructor
Bij het maken van een core moet er altijd een constructor aangeroepen worden.
Dat doe je via `public function __construct(){}`.
## getURL
Om de url te krijgen van moet je dit aanroepen als function. 
Wij gebruiken `$url = $this-> getURL();`. dit roept de function `getURL();` aan. `$This` werkt alleen binnen de klasse `Core`. 
