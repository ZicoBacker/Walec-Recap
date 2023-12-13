# SASS
SASS is een compiler voor [[Frontend#CSS|CSS]]. In een SASS bestand kan je code kleiner opschrijven en [[Basisprogrammeren#2. wat zijn variables|variables]] maken en gebruiken. Hiermee maakt het het maken van een CSS bestand een stuk sneller en kleiner. 

## SASS setup 
Type het onderstaande commando in de terminal: 
`npm init`  
Dit commando zal een `package.json` bestand genereren.
in dit `.json` bestand moet je het volgende toevoegen bij scripts:
```json
"scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "sass": "sass -w scss:css"
    },
``` 
Dit zorgt ervoor dat je `Npm run sass` kan gebruiken. Hij maakt dan een nieuwe folder aan `css/` met daarin een `.css` bestand met je code van je `.scss`  bestand.

We installeren hiermee de _dependencies_. Door `npm install`/`npm i` wordt de node_modules en het bestand package-lock.json gegenereert.  
Door `--save-dev`/`-D` toe te voegen. Komen er ook regels bij in de package.json die de _dependencies_ van het project beschrijven.

je moet een van (of beide) deze scripts in je `package.json` toevoegen:
`npm run sass`
`npm run minify`
# position utility classes
## Utility classes
Moeilijke woorden voor een fantastisch concept. In veel websites moet je heel vaak dezelfde properties aanpassen voor veel verschillende elementen. Stel je eens voor dat je op een webpagina een stuk of 50 elementen hebt staan en bij de helft van de elementen moet je de property display veranderen naar flex. Dat zijn 25 regels aan styling.

Wat nou, als 1 class selector aan maakt ".flex" en daar de property display verandert naar flex. Dan moet je deze klasse wel toepassen op de HTML elementen, maar dit zorgt niet voor extra regels. In je CSS bestand heb je maar 3 regels nodig, in plaats van 25.

## Position property 
Ook ga je nu kennis maken met de property position. Deze property moet voorzichtig gebruikt worden! Het kan namelijk heel makkelijk je complete pagina ontwerp kapot maken. Daarom kan je de position property alleen in bepaalde gevallen echt goed gebruiken. En zal je voor de rest gebruik moeten maken van de flexbox methode die je in de vorige opdrachten hebt behandeld.

## syntax
```scss
&.fixed{
      position: fixed;
   }
   
   &.sticky{
      position: sticky;
   }
   
   &.absolute{
      position: absolute;
   }
```
# Banner styling
Banner element. 
Je vind ze tegenwoordig op bijna alle websites. Een grote afbeelding die vaak een groot deel van de pagina in beslag neemt. En vaak is er ook wat tekst in de banner te vinden. Bij een banner kunnen we goed gebruik maken van de position property om een IMG element te als achtergrond te gebruiken.

## Syntax
```scss
.banner {
  /*
   * @TODO: Add banner base styling.
   */
  display: flex;
  position: relative;
  width: 100%;
  height: 100vh; // zorgt ervoor dat hij       het schermbreedte in beslag neemt.
  /*
   * @TODO: Add banner img styling.
   */
  img {
    position: absolute;
    inset: 0;
    width: 100%;
    height: 100%;
    object-fit: cover;
    z-index: $background-level; // 1
  }
  /*
   * @TODO: Add banner div.content styling.
   */
  div.content{
    display: flex;
    flex-direction: column;
    padding: 1rem;
    z-index: $content-level; // 2
   }
  }
```
# Flex option utility classes
## Flex options. 
In deze opdracht en in de vorige opdrachten heb je al kennis gemaakt met flexbox en de properties justify-content en align-items. Deze twee properties kunnen goed ingezet worden om elementen te positioneren. Nu zijn er in deze opdracht al een aantal elementen die gebruik kunnen maken van deze twee properties. We kunnen het navigatie-menu aanpassen en de items anders positioneren. En we kunnen de tekst in de banner in verschillende hoeken plaatsen.

Daarom kan je nu dus ook flex-option-utility-classes gaan toevoegen. Hiermee kan je straks verschillende pagina's anders indelen door alleen wat andere classes toe te voegen aan elementen!

## info
Het nieuwe dat we hier leren is `!important`. dit zorgt ervoor dat dit altijd het element zal aanpassen, ook al heeft een andere selector normaal voorrang. dit doe je tussen de waarde en `;`.
## Syntax
```scss
.jc-center{
  justify-content: center;
}

.jc-space-between{
  justify-content: space-between !important;
}

.jc-flex-start{
  justify-content: flex-start !important;
}

.jc-flex-end{
  justify-content: flex-end !important;  
}

/*

 * @TODO: Add align-items utility classes.

 */
.ai-center{
  align-items: center !important;
}

.ai-flex-start{
  align-items: flex-start !important;
}

.ai-flex-end{
  align-items: flex-end !important;
}
```
# Responsive Grid
To have grids repsonsive, we need media queries and foreach loops. We used this in exercise two.
We have the following example:
```scss
@each $prefix, $size in conf.get("screensizes") {
 }
```
This will make the following screen sizes: S, M, L, XL and XXL.
```scss
@media screen and (min-width: $size) {
  }
```
 This piece of code will ask if the screen is bigger then the given value. It means all the styling will only work on screens that are smaller then X.
Then we added this:
```scss
@for $i from 1 through conf.get("columncount") {
    }
```

The final piece of code we add is the most important for everything to work:
```scss
.col-#{$prefix}-#{$i} {
        width: math.div(100%, math.div(conf.get("columncount"), $i));
      }
```
This code is difficult for me to explain but this code will give you grid styling for screen sizes and how much of that screen it will take up.