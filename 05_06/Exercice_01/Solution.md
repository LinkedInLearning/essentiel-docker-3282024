### Créer un conteneur à partir de l'image de base alpine:3.17

$ docker run -it --name=alpine_curl alpine:3.17

### Ajouter le package curl

/ # apk add curl

### Exporter le conteneur dans une archive alpine-curl.tar

$ docker export alpine_curl -o alpine_curl.tar

### Créer un Dockerfile avec une image de base FROM scratch

FROM scratch

### Ajouter l'archive alpine-curl.tar avec la commande ADD

ADD alpine_curl.tar /

### Ajouter l'instruction CMD avec la commande **/bin/sh**

CMD ["/bin/sh"]

### Construire une image **alpine:curl** à partir de ce Dockerfile

$ docker build -t alpine:curl .

### Tester la nouvelle image **alpine:curl**

$ docker run -it alpine:curl

/ # curl

curl: try 'curl --help' or 'curl --manual' for more information

/ # 
