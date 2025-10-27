# TP1 : Docker
## Partie 1
### Question 1.1
Comme le Dockerfile est sur Github, les mots de passe y seraient exposés. Il faut donc éviter ça avec -e. Avec -e, les variables sont définies au moment de l’exécution et ne restent pas stockées dans l’image.
### Question 1.2
Les conteneurs Docker sont éphémères. Ainsi, l'utilisation d'un volume permet de stocker les données et de les faire persister même si le conteneur est détruit.
### Question 1.3
| Étape           | Commande                                                                                                                                                                   |
| --------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Créer le réseau | `docker network create app-network`                                                                                                                                        |
| Build image DB  | `docker build -t my-postgres ./database`                                                                                                                                   |
| Run DB          | `docker run -d --name my-db --network app-network -e POSTGRES_DB=db -e POSTGRES_USER=usr -e POSTGRES_PASSWORD=pwd -v /my/own/datadir:/var/lib/postgresql/data my-postgres` |
| Run Adminer     | `docker run -d --name adminer --network app-network -p 8090:8080 adminer`                                                                                                  |
### Question 1.4
Un build multistage permet:
- de séparer la compilation et l’exécution.
- d'avoir une image finale plus légère (en gardant seulement le JRE et le .jar ).
- améliorer la sécurité (pas de Maven ni de code source en production).
### Question 1.5
Le reverse Proxi permet de rediriger les requêtes vers le backend et de gérer le load balancing.
### Question 1.6
Le docker-compose est important car il permet de faire fonctionner simplement plusieurs conteneurs ensemble en gérant les configuraiton, dépendances, volumes et réseaux.
### Question 1.7
Commandes principales :
'''bash
docker-compose build
docker-compose up -d
docker-compose down
docker-compose ps
docker-compose logs -f

'''
### Question 1.8
services → définit chaque conteneur (DB, backend, http).
depends_on → ordre de démarrage.
networks → communication interne.
volumes → persistance.
ports → publication externe (uniquement httpd).
### Question 1.9
'''bash
docker login
docker tag my-database copni/my-database:1.0
docker push copni/my-database:1.0
'''
### Question 1.1O
Publier petmet de partager les images entre les machines.


