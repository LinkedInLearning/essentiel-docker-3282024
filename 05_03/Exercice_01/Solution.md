## Créer une image à partir d'un Dockerfile

### Créer dans un dossier projet1 un Dockerfile avec comme image de base centos:7

FROM centos:7

### Ajouter le package wget

RUN yum install wget -y

### Utiliser la commande build pour contruire une image nommée centos7:wget

$ docker build -t centos:wget .

### Afficher les couches de cette nouvelle image avec la commande **history**

$ docker history centos7:wget

### Créer dans un dossier projet2 avec le même Dockerfile que le projet1

FROM centos:7
RUN yum install wget -y

### Ajouter le package curl

RUN yum install curl -y

### Utiliser la commande build pour contruire une nouvelle image nommée centos7:curl

$ docker build -t centos:curl .

### Afficher les couches de cette nouvelle image avec la commande **history**

$ docker history centos7:curl
