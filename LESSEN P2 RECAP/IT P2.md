# Docker commands
## docker containers
`docker run`
Maak een container en voer deze uit op basis van een image.

Good docker run example:
`docker run --name naam -v volume --network netwerknaam -p port1:port2 -d image(httpd example)`

`docker start`
Start een gestopte container.

`docker stop`
Stop een draaiende container.

`docker restart`
Herstart een draaiende container.

`docker rm`
Verwijder een container.

`docker ps`
Toon informatie over draaiende containers.

`docker ps -a`
Toon informatie over alle containers (zowel draaiende als gestopte).

`docker logs`
Bekijk de loguitvoer van een container.

`docker exec -it`
Voer een opdracht uit binnen een draaiende container.

`docker inspect`
Toon gedetailleerde informatie over een container.
## Imagebeheer
`docker images`
Toon een lijst van beschikbare images.

`docker pull`
Haal een image van een Docker-registery.

`docker build -t`
Bouw een image op basis van een Dockerfile.

`docker push`
Upload een image naar een Docker-registery.

`docker rmi`
Verwijder een image.
## netwerkbeheer
Lijst van alle netwerken:
`docker network ls`

Inspecteer een netwerk:
`docker network inspect netwerknaam`

Maak een netwerk:
`docker network create <opties> <netwerknaam>`
Opties kunnen zijn `--driver` om het netwerktype te specificeren, en andere opties specifiek voor het netwerktype.

Verbind een container met een netwerk:
`docker network connect <netwerknaam> <containernaam>`

Verwijder een netwerk:
`docker network rm <netwerknaam>`

Koppel een container los van een netwerk:
`docker network disconnect <netwerknaam> <containernaam>`

Prune netwerken:
`docker network prune`
Dit commando verwijdert alle netwerken die niet in gebruik zijn.
## Volume beheer
Lijst alle volumes:
`docker volume ls`

Inspecteer een volume:
`docker volume inspect <volumenaam>`

Maak een volume:
`docker volume create <opties> <volumenaam>`
Opties kunnen zijn `--driver` om het volume type te specificeren, en andere opties specifiek voor het volume type.

Verwijder een volume:
`docker volume rm <volumenaam>`

Prune volumes:
`docker volume prune`
Dit commando verwijdert alle volumes die niet in gebruik zijn door een container.

Om een pad binnen een volume te verbinden aan een pad binnen de image doe jij bijvoorbeeld:
`-v /var/lib/docker/volumes/volumenaam:/usr/local/apache2/htdocs`
DIt zorgt ervoor dat de folder `htdocs` alles overneemt wat in `volumenaam` staat
