### Créer une nouvelle image à partir de l'image de base alpine:3.17

FROM alpine:3.17

### Copier le fichier source hello.c

COPY hello.c /

### Installer le compilateur gcc et la librairie libc-dev, puis compiler et générer l'exécutable hello

RUN apk add gcc libc-dev \
 && gcc -o hello hello.c

### Modifier la variable CMD pour exécuter hello

CMD ["/hello"]

### Construire l'image Docker A

$ docker build -t hello:1.0 .
