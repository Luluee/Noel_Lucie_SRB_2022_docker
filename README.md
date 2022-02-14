# Noel_Lucie_SRB_2022_docker
Projet Docker
# Prérequis
* Installer Docker sur votre ordinateur, pour cela aller sur [Docker](https://hub.docker.com)
* Un invite de commande, pour commencer le projet
* Un éditeur de texte

# Commandes
* docker-compose build : permet de construire mes services.
* docker-compose up : permet de lancer mes services.
* Pour accéder à l'application finale, ouvrir un navigateur web et taper : localhost:3000 
Il est possible de tester seuleument les dockerfile en utilisant les commandes suivantes :
* docker build -f Dockerfile -t frontend(ou backend)
* docker run -it frontend(ou backend)

# Docker-compose
## Premier block du docker-compose :
Docker-compose permet d'ajouter les services qui nous seront utile.
```yaml
services:
  backend:
    build:
      context: ./
      dockerfile: ./backend/Dockerfile
    ports:
      - 8080:8080
    container_name: backend
    depends_on:
      - mongo
```
* Le premier block je l'ai nommé backend qui correspond au service NodeJs.
* Puis j'ai ajouté la ligne build, pour qu'au lancement mon dockerfile soit construit.
* La ligne Dockerfile indique où aller chercher le Dockerfile.
* Ensuite la ligne ports me permet de changer le port par défaut si besoin, ci-dessus j'ai gardé le port par défaut.
* J'ai nommé mon container backend.
* Et enfin j'ai utilisé la dernière ligne pour que mon backend soit relié à ma base de données mongodb.

## Deuxième block du docker-compose :
```yaml
mongo:
    image: mongo
    expose:
      - 27017
    ports:
      - 27017:27017
    container_name: mongo
```
* Le deuxième block je l'ai nommé mongo qui correspond à la base de données mongodb.
* Puis j'ai ajouté la ligne image, pour indiquer l'image souhaité, là j'ai choisi mongodb.
* La ligne expose permet d'exposer le port que je choisis.
* Ensuite la ligne ports me permet de changer le port par défaut si besoin, ci-dessus j'ai gardé le port par défaut.
* J'ai nommé mon container mongo.

## Troisième block du docker-compose :
```yaml
frontend:
    build:
      context: ./
      dockerfile: ./frontend/Dockerfile
    ports:
      - 3000:3000
    container_name: frontend
```
* Le troisième block je l'ai nommé frontend qui correspond au service ReactJs.
* Puis j'ai ajouté la ligne build, pour qu'au lancement mon dockerfile soit construit.
* La ligne Dockerfile indique où aller chercher le Dockerfile.
* Ensuite la ligne ports me permet de changer le port par défaut si besoin, ci-dessus j'ai gardé le port par défaut.
* J'ai nommé mon container frontend.

# Dockerfile
Les Dockerfiles sont des fichiers qui permettent de construire une image Docker adaptée à nos besoin.
## Dockerfile backend
```
FROM node:12.18.3

RUN mkdir -p /usr/src/app

WORKDIR /usr/src/app

COPY ./backend/package.json ./
COPY ./backend/ .

RUN npm install
EXPOSE 8080
CMD [ "npm", "start"]
```
* La commande FROM nous permet de récupérer une image.
* La commande RUN mkdir -p va créer le dossier app dans le dossier /usr/src.
* La commande WORKDIR nous permet de nous placer sur le répertoire demandé.
* La commande COPY permet de copier les fichiers dans le répertoire où on c'est placé juste avant.
* La commande RUN npm install permet d'installer toutes les dépendances de paquets Json.
* La commande EXPOSE 8080 permet de préciser le port par défaut.
* Et la dernière commande permet de lancer l'application uniquement lorqu'on le lancera depuis docker.

Le Dockerfile frontend utilise les mêmes commandes que le Dockerfile backend. Il y a tout de même certaines particularités comme par exemple le port ou les dossiers.
