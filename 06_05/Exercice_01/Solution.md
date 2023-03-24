## Créer et partager un conteneur de données

### Créer deux volumes nommés "datas" et "html"

$ docker volume create datas

$ docker volume create html

### Créer un conteneur basé sur "centos:7" nommé "app_volumes" et monter le volume "datas" sur "/datas" et le volume "html" sur "/html"

$ docker run -it --name=app_volumes -v datas:/datas -v html:/html centos:7

### Créer un fichier "config" sur /datas et un fichier "index.html" sur /html

```
[root@07103ae56774 /]# echo "111" > /datas/config
[root@07103ae56774 /]# echo "222" > /html/index.html
[root@07103ae56774 /]# exit
```

### Créer un conteneur "web" basé sur "nginx:1.23-alpine" et monter les volumes référencés par le conteneur "app_volumes"

$ docker run -it -d --name=web --volumes-from=app_volumes nginx:1.23-alpine

### Se connecter sur le conteneur web et vérifier les volumes

$ docker exec -it app_volumes -- sh
```
[root@07103ae56774 /]# echo host1 >> /datas/hosts
```
#### Faire un CTRL+P+Q pour se détacher 
### S'attacher au conteneur "host2" et ajouter dans le fichier "/datas/hosts" le nom du conteneur

$ docker attach host2
```
[root@02e7a9c7aecf /]# echo host2 >> /datas/hosts
```

#### Faire un CTRL+P+Q pour se détacher 
### Vérifier dans les deux conteneurs le contenu du fichier "/datas/hosts"

$ docker attach host1
```
[root@07103ae56774 /]# cat /datas/hosts
host1
host2
```
#### Faire un CTRL+P+Q pour se détacher 

$ docker attach host2
```
[root@02e7a9c7aecf /]# cat /datas/hosts
host1
host2
```
