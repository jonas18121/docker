
## Supprimer un container/image/service

### Supprimer un service

    > docker-compose rm <nom_du_service_dans_docker-compose.yml>








## Voir la liste des container/images/service

### Voir tous les images 

    > docker-compose images








## Faire tourner ou stoper docker/docker-compose

### Faire tourner docker-compose

    > docker-compose up

### Faire tourner docker-compose en arrière plan

    > docker-compose up -d

### Arrêter les conteneurs et supprimer les conteneurs, les réseaux, les volumes et les images créés par up.

    > docker-compose down

### Arrêter l'exécution des conteneurs sans les supprimer. Ils peuvent être redémarrés avec docker-compose start.

    > docker-compose stop

### Démarrer les conteneurs

    > docker-compose start








## Ligne de commande git bash

### Entrer dans la cli de git bash du projet

    > docker exec -it <nom_du_container_du_projet> bash

