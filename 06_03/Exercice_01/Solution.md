## Partager les volumes

### Créer un volume nommé "share"

$ docker volume create share

### Créer un conteneur en mode "dettach" basé sur "centos:7" nommé "host1" et monter le volume "share" sur "/datas"

$ docker run -it -d --name=host1 -v share:/datas centos:7

### Créer un conteneur en mode "dettach" basé sur "centos:7" nommé "host2" et monter le volume "share" sur "/datas"

$ docker run -it -d --name=host1 -v share:/datas centos:7

### S'attacher au conteneur "host1" et créer un fichier "/datas/hosts" qui contient le nom du conteneur

$ docker attach host1
```
[root@07103ae56774 /]# echo host1 >> /datas/hosts
```
#### Faire un CTRL+P+Q pour se détacher 
### S'attacher au conteneur "host2" et ajouter dans le fichier "/datas/hosts" le nom du conteneur

$ docker attach host2
```
[root@07103ae56774 /]# echo host2 >> /datas/hosts
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
[root@07103ae56774 /]# cat /datas/hosts
host1
host2
```
