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

### REMARQUE : L'indentaion est importante

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

    networks:
        dev:
    volumes:
        db-data:


 - `version:` = Indique la version de Docker Compose que nous utilisons, Docker fournira les fonctionnalités appropriées.

 - `services:` = Définit tous les différents containers que nous allons créer

 - `db:` = Le nom de notre service

 - `image:` = Si nous n'avons pas de Dockerfile et que nous voulons exécuter un service à l'aide d'une image déjà existant, on le met ici

 - `container_name:` = On donne un nom a notre container

 - `restart:` = On dit à notre service de toujours redémarré quoi qu'il arrive

 - `volumes:` = On lui spécifie un volume dans lequel il va devoir persister des données

 - `environment:` = configurer une ou des variables d'environnement dans le conteneur pour ce connecté au service

 - `networks:` = Ici, on indique le nom du réseau qu'il va devoir utiliser 


### Conteneur phpMyAdmin

    phpmyadmin:
            image: phpmyadmin
            container_name: wallky_phpmyadmin
            restart: always
            depends_on:
                - db
            ports:
                - 8080:80
            environment:
                PMA_HOST: db
            networks:
                - dev

 - `depends_on:` ça veut dire que le service `phpmyadmin` va attendre que le service `db` soit disponible avant de démarré, car il dépend de lui

 - `ports:` Le port sous lequel on veut affiché l'interface de notre service

 - `PMA_HOST:` On dit au service `phpmyadmin` que sa base de données sera `db:`


### Conteneur Apache et Php