# react-docker

Pour utiliser docker avec un projet react copier les fichiers de ce repository à la ractine de votre projet react


## Image docker local
Le fichier `/dev/DockerFile` est utilisé pour générer l'image Docker en local.
Cette image contient NodeJS et le dossier node_modules

## Docker-compose local
Le fichier `docker-compose.yml` utilise l'image docker local et l'expose sur le port 3000.

Un volume est utilisé pour monter l'application react.

Le fichier `.env` permet d'activer le rechargement automatique du navigateur lors de la modification du code.

**Pour demarer le projet en local :**
```
docker-compose up
```
L'application est initialisée sur le port 3000 <http://localhost:3000>.

## Lancer des commandes dans le container

Lancer une console interactive sur le container :
```
docker exec -it my-app bash
```

Tester :
```
npm test
```

Générer le build pour l'image de production :
```
npm build
```

Pour quitter le container :
```
exit
```


## Image docker pour la production

Le fichier `DockerFile` à la racine du dossier est utilisé pour générer l'image Docker de production.

Cette image contient un serveur web NGINX et le build de l'application react.

**Pour générer l'image de production :**
```
docker build -t my-app:0.1 .
```

**Pour lancer l'image en local sur <http://localhost> :**
```
docker run -d -p 80:80 my-app:0.1
```
