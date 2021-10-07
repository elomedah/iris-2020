# Kafka Training
https://dzone.com/articles/running-apache-kafka-on-windows-os   
Dans ce TP, nous allons installer une plateforme Kafka.
Il est recommandé de faire le tp sur le linux.  
Si vous utilisez windows vous avez la possibilité d'installer wsl en suivant les instructions sur ce lien
https://docs.microsoft.com/fr-fr/windows/wsl/install
### Etape 1: Télécharger les fichiers 

Pour faciliter le TP, créer un répertoire de travail kafka. 
La variable $HOME est le répertoire courant de votre utilisateur. Vous pouvez créer le repertoire kafka où vous voulez.  
```
mkdir $HOME/kafka
cd $HOME/kafka
```
Télécharger Kafka : http://kafka.apache.org/downloads.html  (https://dlcdn.apache.org/kafka/3.0.0/kafka_2.13-3.0.0.tgz)
```
wget https://dlcdn.apache.org/kafka/3.0.0/kafka_2.13-3.0.0.tgz
```

Télécharger Java : http://www.oracle.com/technetwork/java/javase/downloads/jre8-downloads-2133155.html (optionnel si vous avez déjà java)  

```
java -version
sudo apt install default-jre
```


Télécharger zookeeper : http://zookeeper.apache.org/releases.html  (optionnel)

Copier les fichiers téléchargés dans le repertoire kafka.

### Etape 2 : Décompresser et vérification java

Décompresser le fichier kafka télécharger à l'étape 1
```
tar zxvf kafka_2.13-3.0.0.tgz
```

### Etape 3 : Lancement de zookeeper et kafka

Pour lancer Kafka sur votre machine, vous devez avoir deux serveurs :

* Le Zookeeper (le gestionnaire de cluter kafka).  
* Le serveur Kafka.  


##### Lancement zookeeper

La version de Kafka que vous avez téléchargée contient déjà Zookeeper et son fichier de configuration.

Avant de lancer Zookeeper ouvrez le fichier de configuration ./config/zookeeper.properties avec votre éditeur de texte préferé.

```
cd $HOME/kafka/kafka_2.13-3.0.0
vi ./config/zookeeper.properties
```

Pour lancer Zookeeper il faut exécuter la commande suivante :
```
cd $HOME/kafka/kafka_2.13-3.0.0
./bin/zookeeper-server-start.sh ./config/zookeeper.properties
```

Zookeeper comme configuré dans le fichier zookeeper.properties se lance sur le port 2181.

##### Lancement serveur kafka

De même que zookeeper nous devons configurer le fichier le configuration kafka  config/server.properties

```
Ouvrir un autre terminal
cd $HOME/kafka/kafka_2.13-3.0.0
vi config/server.properties
```


Maintenant vous pouvez lancer le serveur kafka avec la commande suivante :

```
./bin/kafka-server-start.sh ./config/server.properties
```

Par défaut le broker kafka va tourner sur le port 9092

### Etape 4 : Topic, Producteur, Consomateur

Grâce aux étapes précedentes notre cluster (à ce stade composé d'un seul broker kafka et une instance zookeeper) kafka est prêt à être utilisé.  
Pour commencer à envoyer des messages, créons un topic.

```
Ouvrir un autre terminal
cd $HOME/kafka/kafka_2.13-3.0.0
Création de topic
./bin/kafka-topics.sh --create  --replication-factor 1 --partitions 1 --topic mon-tunnel-topic --bootstrap-server localhost:9092
Lister les topics
 ./bin/kafka-topics.sh --list --bootstrap-server localhost:9092

```

