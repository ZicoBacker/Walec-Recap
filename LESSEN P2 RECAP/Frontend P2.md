# SASS
SASS is een compiler voor [[Frontend#CSS|CSS]]. In een SASS bestand kan je code kleiner opschrijven en [[Basisprogrammeren#2. wat zijn variables|variables]] maken en gebruiken. Hiermee maakt het het maken van een CSS bestand een stuk sneller en kleiner. 
## Hoe gebruik ik SASS?
- om SASS te gebruiken moet jij je terminal gebruiken. In je terminal wil je naar de folder gaan waar je `.SCSS` bestand in staat, anders werkt het volgende niet. 
- Om naar een folder te gaan in je terminal doe je `cd [foldernaam]` of `cd ../` om terug te gaan.
- In je terminal doe je `npm run sass`. als jij een `package.json` al hebt zal dit werken. 
- Als jij nog geen `package.json` hebt dan kan je `npm i sass` doen in de folder waar je met SASS aan de slag wil. 
- Als je SASS aan staat en je wil dat hij stop, ga je in je terminal en druk je `CONTROL + C`.
# Nested selectors
In SASS kan je gebruik maken van nested selectors. Dit betekend eigenlijk gewoon een selector in een selector. Dat ziet er zo uit:
```SCSS
ol{
	background-color: red;
	li {
	font-size: 12px;
	}
}
```

## variables
ook kan je in sass [[Basisprogrammeren#2. wat zijn variables|variables]] gebruiken. dat ziet er zo uit:
```SCSS
$teal: #04bf9d;
p{
	color: $teal;
}
```
hij zal hier dus de hex code `#04bf9d` gebruiken voor `color`.