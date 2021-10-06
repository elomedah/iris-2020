# Kafka Training
https://dzone.com/articles/running-apache-kafka-on-windows-os   
Dans ce TP, nous allons installer une plateforme Kafka.

### Etape 1: Télécharger les fichiers 

Pour faciliter le TP, créer un répertoire de travail kafka. 
La variable $HOME est le répertoire courant de votre utilisateur. Vous pouvez créer le repertoire kafka où vous voulez.  
```
mkdir $HOME/kafka
```
Télécharger Kafka : http://kafka.apache.org/downloads.html  (https://dlcdn.apache.org/kafka/3.0.0/kafka_2.13-3.0.0.tgz)
Télécharger Java : http://www.oracle.com/technetwork/java/javase/downloads/jre8-downloads-2133155.html (optionnel si vous avez déjà java)
Télécharger zookeeper : http://zookeeper.apache.org/releases.html  (optionnel)

Copier les fichiers téléchargés dans le repertoire kafka.

### Etape 2 : Décompresser et vérification java

Décompresser le fichier kafka télécharger à l'étape 1
```
tar zxvf kafka_2.13-3.0.0.tgz
```

Vérifier que java est bien installé sur votre poste.  
Sinon vous devriez procéder à l'installation de java  
https://www.java.com/fr/download/help/windows_manual_download.html#download

### Etape 3 : Lancement de zookeeper et kafka

Pour lancer Kafka sur votre machine, vous devez avoir deux serveurs :

*Le Zookeeper (le gestionnaire de cluter kafka).
*Le serveur Kafka.

Pour faciliter les configurations, vous devez créer ces deux répertoires. On découvrira le long du temps à quoi ils vont servir.

```
cd $HOME/kafka/
mkdir log_zookeeper
mkdir log_kafka
```

##### Lancement zookeeper

La version de Kafka que vous avez téléchargée contient déjà Zookeeper et son fichier de configuration.

Avant de lancer Zookeeper ouvrez le fichier de configuration ./config/zookeeper.properties avec votre éditeur de texte préferé.

```
cd $HOME/kafka/kafka_2.13-3.0.0
vi ./config/zookeeper.properties
```
Ce fichier contient plusieurs lignes. Vous devez modifier la ligne suivante en settant le chemin absolu du répertoire log_zookeeper.

Pour lancer Zookeeper il faut exécuter la commande suivante :
```
cd $HOME/kafka/kafka_2.13-3.0.0

Pour Linux
./bin/zookeeper-server-start.sh ./config/zookeeper.properties

Pour windows
./bin/windows/zookeeper-server-start.bat ./config/zookeeper.properties
```

Zookeeper comme configuré dans le fichier zookeeper.properties se lance sur le port 2181.

