### Reprendre le Dockerfile de l'exercice 01 et ajouter un nom de build sur le premier FROM avec l'argument AS

FROM alpine:3.17 AS first

### Ajouter à la fin du Dockerfile un nouveau FROM pour repartir d'une image de base alpine:3.17

FROM alpine:3.17 AS second

### Copier le fichier hello à partir du premier build 

COPY --from=first hello /

### Construire l'image Docker

$ docker build -t hello:1.1 .
