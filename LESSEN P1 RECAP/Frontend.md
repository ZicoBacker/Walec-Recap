# HTML
HTML staat voor HyperText Markup Language. HTML wordt gebruikt om een browser te vertellen wat er op de pagina komt te staan. eigenlijk is het geen programmeer taal maar een Markdown Language( opmaak taal.)
## elementen
In HTML werken wij met elementen. Elk element doet wat anders of ziet er anders uit. Meeste element tag start je met `<` en sluit je met `>`. een "closing tag" kan je herkennen aan `/`. je moet een starting en closing tag hebben voor de meeste elementen. Sommige elementen hebben geen closing tag nodig. 
## HTML attributes
Attributes is alles tussen de `< >` dat niet een element is. een voorbeeld:
`<a href="http://www.google.com/" target="_blank">` alles na de `a` in dit geval is een attribute.
## HTML basis pagina
```HTML
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
</head>
<body>

</body>
</html>
```
In het `head` element stop je alles wat je NIET gaat ziet op de html pagina. Denk aan `link` of `style`
In het `body` element stop je alles wat je WEL gaat zien op de html pagina. Denk aan `p` of `a`.
je kan `!` gebruiken om een basis HTML pagina op te zetten.
# CSS
CSS staat voor Cascading Style Sheets. Net als HTML is CSS eigenlijk geen programmeertaal. Dit is omdat het geen logica kan gebruiken. Ook is het geen markup language. Het is een stylesheet language. CSS is de enige stylesheet language die werkt met HTML.
## hoe gebruik ik CSS
### soorten CSS
Je hebt 3 manieren van CSS gebruiken:
- Inline
	Je schrijft het als [[Frontend#HTML attributes|attribuut]] in elk element.
- Internal
	je doet het in de head met de volgende element: `<style> </style>`.
- External
	Je verbind een los `.css` bestand aan de HTML pagina met `link:css`.
### Schrijven in CSS
om bijvoorbeeld een `p` element aan te passen via CSS moet je het volgende doen:
```CSS
p {
	 property: waarde; //syntax
	 font-size: 1rem; //voorbeeld
}
```

Als je bijvoorbeeld specifiek een class wil aanspreken in plaats van een element doe je:
```CSS
.text-big {
	font-size: 2rem;
}
```

Ook kan je ID's gebruiken:
```CSS
#banner {
	width: 100vw;
	height: 100vh;
}
```

# Tekst Elementen
## Wat zijn tekst elementen?
Ieder HTML element kan tekst bevatten en dit zal ook gewoon op de pagina komen te staan. Maar er zijn een aantal elementen die specifiek voor tekst zijn bedoelt en ook zo ingezet moeten worden. Door de juiste tekst elementen en structuur te gebruiken, kunnen met mensen met screenreaders de pagina ook gemakkelijk benaderen. 

En paar goede voorbeelden van tekst elementen: h1, p, span, strong en blockquote.

## Heading elementen
- heading elementen zijn `h1` to `h6`.
- Heading elementen zijn erg belangrijk voor screenreaders, omdat met de heading elementen structuur van de tekst aangegeven moet worden. 
- Een webpagina moet eigenlijk ook maar een `h1` hebben. Dat wordt soms gezien als de titel van de hoofdpagina. 
- `h2` tot `h6` worden gebruikt voor hoofdstukken.

## Paragraph elementen
- paragraph elementen zijn elementen voor stukken tekst. Denk aan:
	- p
	- strong
	- em
	- mark
	- small
	- del
	- ins
	- sub
	- sup

# Layout elementen
## Semantic Elements
"Semantic Elements" is eigenlijk gewoon een moeilijke term voor elementen die zeggen waarvoor ze gebruikt worden. Twee mooie voorbeelden hiervan zijn het nav element, wordt gebruikt voor website navigatie en het article element wordt gebruikt voor een artikel op een webpagina (of gewoon de tekst waar de pagina om gaat.)
Een paar voorbeelden van semantic elements en waarvoor je ze gebruikt:
- `<header>` komt altijd boven aan de pagina te staan.
- `<nav>` Wordt gebruikt voor pagina navigatie of submenu's.
- `<main>` is voor de algemene inhoud op de webpagina. Hier zal je er maar 1 van hebben.
- `<aside>` is om iets ernaast te zetten. Wordt vaak gebruikt voor navigeren in de pagina zelf.
- `<article>` voor bijvoorbeeld artikels. het wordt gebruikt om de inhoud te bundelen.
- `<section>` is om `<articles>` te verdelen. Dit wordt vaak aangeduid met een [[Frontend#Heading elementen|Heading element]].
- `<footer>` zal altijd onderaan de pagina staan, maar kan ook gebruikt worden onder aan een `article`. 

### Moet je Semantic Elements gebruiken?
>Nee, je kan nog steeds een mooie HTML pagina in elkaar zetten met standaard elementen zoals "div". Dit zorgt er alleen voor dat je code een stuk minder overzichtelijk wordt.

Is wat er canvas staat maar Jesse wil **HEEL HEEL HEEL** erg graag dat je het wel doet. Semantic elementen worden dus puur en alleen ingezet om de code overzichtelijk te houden.

## Lijsten en menu's
een voorbeeld van een lijst/ menu structuur:
```html
<ol>
      <li>
        Dit is het eerste item.
        <ul>
          <li>Subitem 1</li>
          <li>Subitem 2</li>
          <li>Subitem 3</li>
        </ul>
      </li>
      <li>
        Dit is het tweede item.
        <ul>
          <li>Subitem 1</li>
          <li>Subitem 2</li>
          <li>Subitem 3</li>
        </ul>
      </li>
    </ol>
```
`OL` staat voor "ordered lists"
`UL` staat voor "unordered lists"
`LI` staat voor "List item"

# Boxmodel
Het is de basis van alle HTML elementen. Alle HTML elementen kan je zien als "doos" (box) of gewoon als vierkant. Het boxmodel bestaat uit 4 onderdelen (van buiten naar binnen): **margin**, **border**, **padding** en **content**. 
- Margin: ruimte om het element heen. Deze ruimte is transparant. 
- Border: de rand van het element. 
- Padding: ruimte vanaf de rand (border) tot de content.
- Content: de inhoud van het element. Bijvoorbeeld text of afbeeldingen
- ![[Pasted image 20231116183212.png]]

## Verschil tussen content-box en border-box
Je kan met CSS aangeven dat een element zich moet "gedragen" als content-box of als border-box. Het verschil zit hem in de breedte van het element, als deze gedefinieerd wordt! Als een content-box een width krijgt van 500px, dan is het content-gedeelte van het boxmodel 500px breed.   
Als een border-box een width krijgt van 500px, dan is de border+padding+content 500px breed.\

### Welke moet ik  gebruiken
Het handigste is om alle elementen een **box-sizing: border-box** te geven. Het vervelende is dat de browsers standaard de box-sizing op "content-box" hebben staan.

# Eenheden
Je hebt ze ondertussen al een paar keer ingezet! De eenheden waarmee je bijvoorbeeld de grootte van elementen of tekst aan geeft.
## Soorten Eenheden
- `px` is pixels
- `%` is het aantal % van de grootte van waar het in staat.
- `em` is op schaal van de grootte van het element waar het in staat?
- `rem` ,RootEM, werkt hetzelfde, alleen op basis van de HTML Element.
- `VH` is view height. 1vh staat dus gelijk aan 1% dan van hoogte van je scherm.
- `VW` is view width, hetzelfde als `VH` maar dan voor de breedte.