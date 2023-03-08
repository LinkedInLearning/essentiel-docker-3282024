# Créer une nouvelle image à partir de Centos:7

FROM centos:7

# Installer le compilateur gcc

RUN yum install -i gcc

# Copier le fichier source myhello.c

COPY myhello.c /

# Compiler et générer un binaire myhello

RUN gcc -o myhello myhello.c

# Modifier la variable CMD pour exécuter myhello

CMD ["/myhello"]

# Construire l'image Docker

$ docker build -t myhello:1.0 .
