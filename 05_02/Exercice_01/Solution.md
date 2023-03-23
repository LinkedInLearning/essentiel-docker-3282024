## Créer une image à partir d'un conteneur

### Créer un conteneur à partir de l'image de base centos:7

$ docker run -it --name centos_wget centos:7

### Ajouter le package wget

[root@414174c5fdae /]# yum install wget -y

### Utiliser la commande **commit** et créer une image **centos:wget**

$ docker commit centos_wget centos:wget

### Afficher les couches de cette nouvelle image avec la commande **history**

$ docker history centos:wget

### Tester la nouvelle image **centos:wget** 

$ docker run -it centos:wget
```
wget: missing URL
Usage: wget [OPTION]... [URL]...
``` 
