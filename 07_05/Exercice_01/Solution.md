## Effectuer un mappage de port

### Créer un réseau "web" de type bridge

$ docker network create web

### Créer un dossier "web1" et un fichier "index.html" contenant "Server One"

$ cat web1/index.html
```
Server ONE
```

### Créer un dossier "web2" et un fichier "index.html" contenant "Server TWO"

$ cat web2/index.html
```
Server TWO
```

### Créer un dossier "haproxy" et le fichier "haproxy.cfg" suivant

$ cat haproxy/haproxy.cfg
```
frontend http_frontend
        bind *:80
        default_backend http_backend
backend http_backend
        mode http
        balance roundrobin
        server server1 web1:80 check
        server server2 web2:80 check
```

### Créer un conteneur "web1" basé sur l'image "nginx" avec un montage du dossier partagé "web1" sans réaliser de mapping de port

$ docker run -d --network=web --name=web1 -v /home/centos/web1:/usr/share/nginx/html nginx:1.23-alpine

### Créer un conteneur "web2" basé sur l'image "nginx" avec un montage du dossier partagé "web2" sans réaliser de mapping de port

$ docker run -d --network=web --name=web2 -v /home/centos/web2:/usr/share/nginx/html nginx:1.23-alpine

### Créer un conteneur "haproxy" basé sur l'image "haproxy" avec un montage du fichier partagé "haproxy/haproxy.cfg" et un mapping de port "80:80"

$ docker run -d --network=web --name=haproxy -p 80:80 -v /home/centos/hapoxy/haproxy.cfg:/usr/local/etc/haproxy/haproxy.cfg haproxy:2.7-alpine

### Réaliser plusieurs "curl" sur le host

$ curl 127.0.0.1



