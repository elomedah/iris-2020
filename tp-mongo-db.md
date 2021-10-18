# Mongodb TP
## Introduction  

Rappels :

MongoDB est un système de gestion de bases de données (SGBD) qui gère plusieurs bases de données.   
Ce concept est identique dans un SGBD relationnel.

Chaque base contient plusieurs collections. La collection peut être vue comme une table.   

Chaque collection contient des documents. Le document peut être vu comme un tuple (une ligne) d’une table.   

## Installation

### Pré requis
Vous devez installer le système ubuntu sur votre machine
Si vous utilisez déja une distribution linux vous pouvez installer mongodb en suivant la documentation de votre distribution.

Documentation officielle d'installation sur ubuntu https://doc.ubuntu-fr.org/mongodb
Documentation officielle d'installation sur Mac https://docs.mongodb.com/manual/tutorial/install-mongodb-on-os-x/

### Installation et démarrage

##### Installation
Ouvrir le terminal ubuntu en tant qu'administrateur

```
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 68818C72E52529D4
sudo echo "deb http://repo.mongodb.org/apt/ubuntu bionic/mongodb-org/4.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.0.list
sudo apt-get update
sudo apt-get install -y mongodb-org
```

##### Démarrage

Lancer mongodb :
```
sudo service mongod start
```

Si la commande échoue, vous pouvez démarrer mongo manuellement en suivant les étapes suivantes. Dans ce cas mongo ne sera pas un service mais ne vous empêchera pas de suivre le TP.
```
sudo mkdir -p /data/db
sudo  nohup mongod & 
```

Pour vérifier que mongo est bien demarré vous pouvez exécuter cette commande.
La ligne de commande de mongo devrait s'activer.

```
mongo
```

Exécuter cette requête
```
>show dbs
```

## Commande de base

Connexion à une base : use nom_de_la_base. Cette commande possède une double fonction, elle assure la connexion si la base existe, elle la crée puis s’y connecte si la base n’existe pas encore. Une fois connecté, la commande db permet de connaître la base.

```
> use iris_user_db
switched to db iris_user_db
> db
iris_user_db
>
```

La syntaxe utilisée est une syntaxe JavaScript  

#### Les collections
MongoDB est dit schemaless (sans schéma de base de données), on ne précise rien de la structure des données qui seront insérées par la suite dans la collection.

###### Création de collections
Exécuter la commande suivante pour créer une collection.
```
> db.createCollection('etudiant')
{ "ok" : 1 }
```
SQL : create table etudiant ... 

show collections permet de lister toutes les collections de la base courante.
```
> show collections
etudiant
```

Supprimer une collection
```
> db.etudiant.drop()
true
```
En SQL : drop table etudiant

## Import de données et requetage
