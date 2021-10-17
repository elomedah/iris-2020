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

Si la commande échoue, vous pouvez démarrer mongod manuellement en suivant les étapes suivantes. Dans ce cas mongod ne sera pas un service mais ne vous empêchera pas de suivre le TP.
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
show dbs
```

## Commande de base
## Import de données et requetage
