# Création du fichier docker-compose.yml

Exemple de création du fichier docker-compose.yml

1) Créer manuellement le du fichier docker-compose.yml à la racine de votre projet

2) Pour savoir dans quel format doit-on écrire le docker-compose.yml, vérifiez la version de Docker disponible sur votre poste.

    > docker -v

ou 

    > docker --version

Ce site montre les différente version : https://docs.docker.com/compose/compose-file/compose-file-v3/

Dans `docker-compose.yml`

    version: "3.8"
    services:

##  Spécifier nos services dans `docker-compose.yml`

### Conteneur MySQL

Dans `docker-compose.yml`

    version: "3.8"
    services:
        db:
            image: mysql
            container_name: wallky_mysql
            restart: always
            volumes:
                - db-data:/var/lib/mysql
            environment:
                MYSQL_ALLOW_EMPTY_PASSWORD: 'yes'
            networks:
                - dev

 - db: = 
 - image: =
 - container_name: =
 - restart: =  
 - volumes: = 
 - environment: = 
 - networks: = 