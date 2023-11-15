# 1. Git
## Nieuwe repository clonen:

`git clone [link]` -- hiermee haal je een kopie van wat je hebt op GitHub naar je pc. Dit kan je dan weer committen voor een nieuwe versie

## hoe zet ik een nieuwe versie op github:

`git add [filename]` --voegt een file toe die je wil uploaden naar je repository(GitHub) 
`git commit -m "[comment]"` --dit zet het klaar om op te sturen 
`git push` -- stuurt het op naar GitHub, het zal dus meteen zichtbaar zijn 

bedenk je het zo: 
`git add` zorgt ervoor dat je je bestand toevoegt aan een lijst (git commit). dit hoef je maar 1x te doen per bestand. 
`git commit -m "[comments]"` zet het lijstje op om op te sturen en geeft het een naam. (vaak een versie) 
`git push` zet hem op je GitHub.

## als je problemen hebt met iets in de richting van "unknown user/ no valid user" doe dan dit:

`git config --global user.email [GitHub email]` 
`git config --global user.name [GitHub name]

# 2. Git merging & revert
## Revert
om terug te gaan naar een oudere versie omdat je het verneukt hebt of iets doe je: `**git revert COMMIT CODE HIER**`

**waar vind ik mijn git commit code?**
Dit vind je in je GitHub Repository. als je dan rechtsboven gaat naar commits kan je dit zien:
![[Pasted image 20231115110834.png]]
het onderstreepte is je git commit code. Deze gebruik je om te reverten.
## Git merging
bij git heb je vaak problemen als jij en iemand anders hetzelfde aanpassen en dan beide willen pushen. dit los je op in je Visual Studio Code. VSC gaat je helpen in het oplossen van merging conflicts. Dit zal er zo uit zien.![[Pasted image 20231115111007.png]]

Deze stap is alleen voor het geval dat je in detail moet kijken wat je nou eigenlijk als resultaat krijgt.  
Druk op de "Resolve in Merge Editor" knop.  
Kies hier de veranderingen die je wilt en kijk in het onderste "Result" venster of het resultaat is wat je wilt. In dit venster mag je ook typen voor verdere aanpassingen.
![[Pasted image 20231115111140.png]]
