## Effectuer un mappage de port

### Créer une application de type "proxy" qui permet de retransmetre les requêtes "http" vers 2 serveurs web avec un loadbalancing de type "roundrobin"

![](/img/haproxy.png)


### Créer un réseau "web" de type bridge

### Créer un dossier "web1" et un fichier "index.html" contenant "Server One"

### Créer un dossier "web2" et un fichier "index.html" contenant "Server TWO"

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

### Créer un conteneur "web2" basé sur l'image "nginx" avec un montage du dossier partagé "web2" sans réaliser de mapping de port

### Créer un conteneur "haproxy" basé sur l'image "haproxy:2.3-alpine" avec un montage du fichier partagé "haproxy/haproxy.cfg" et un mapping de port "80:80"

### Réaliser plusieurs "curl" sur le host

