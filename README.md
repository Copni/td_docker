# TP1 : Docker
## Partie 1
### Question 1.1
Parce que le Dockerfile est versionné (visible par tous), donc les mots de passe y seraient exposés.
Avec -e, les variables sont définies au moment de l’exécution et ne restent pas stockées dans l’image.
### Question 1.2
Un conteneur Docker est éphémère. Sans volume, les données sont perdues à chaque destruction du conteneur.
Le volume /var/lib/postgresql/data permet de stocker durablement les fichiers de la base sur le disque de l’hôte.
### Question 1.3
| Étape           | Commande                                                                                                                                                                   |
| --------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Créer le réseau | `docker network create app-network`                                                                                                                                        |
| Build image DB  | `docker build -t my-postgres ./database`                                                                                                                                   |
| Run DB          | `docker run -d --name my-db --network app-network -e POSTGRES_DB=db -e POSTGRES_USER=usr -e POSTGRES_PASSWORD=pwd -v /my/own/datadir:/var/lib/postgresql/data my-postgres` |
| Run Adminer     | `docker run -d --name adminer --network app-network -p 8090:8080 adminer`                                                                                                  |
