# TP HADOOP

### Installation

#### Pré requis  
Pour installer hadoop nous avons besoin :   
1. java
```
sudo apt-get update
sudo apt-get install openjdk8-jdk -y
java -version 
```
2. ssh 
```
sudo apt install openssh-server openssh-client -y 
```
Vérifier si le service ssh est up
```
service ssh status
```

Si le service est down, redemarrez
```
sudo service ssh start
sudo service ssh --full-restart
```
3. Créer un user hdoop
```
sudo adduser hdoop
```
4. Configurer une clé ssh
```
sudo su - hdoop
ssh-keygen -t rsa -P '' -f ~/.ssh/id_rsa
cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys
chmod 0600 ~/.ssh/authorized_keys
```

#### Hadoop

Téléchargement du binaire hadoop

```
wget https://downloads.apache.org/hadoop/common/stable/hadoop-3.3.1.tar.gz
tar -xzvf hadoop-3.3.1.tar.gz
```

Modifier les variables 

```
export JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64/
export HADOOP_HOME=/home/hdoop/hadoop-3.3.1
export HADOOP_INSTALL=$HADOOP_HOME
export HADOOP_MAPRED_HOME=$HADOOP_HOME
export HADOOP_COMMON_HOME=$HADOOP_HOME
export HADOOP_HDFS_HOME=$HADOOP_HOME
export YARN_HOME=$HADOOP_HOME
export HADOOP_COMMON_LIB_NATIVE_DIR=$HADOOP_HOME/lib/native
export PATH=$PATH:$HADOOP_HOME/sbin:$HADOOP_HOME/bin
export HADOOP_OPTS="-Djava.library.path=$HADOOP_HOME/lib/native"
```



