# Creación de imagenes de Docker
---

## Dockerfile Inicial
### LABELS
- Archivo **Dockerfile**
  Este archivo y todo el material se encuentra en el directorio httpd-centos

    ```dockerfile
        FROM centos
        LABEL version=1.0
        LABEL uso="curso de docker"

        RUN yum install -y httpd
        WORKDIR /var/www/html
        COPY sitio .
        ENV contenido prueba
        RUN echo "$contenido" > /var/www/html/prueba.html
        EXPOSE 8080
        CMD apachectl -DFOREGROUND
    ```
## Construcción

```bash
docker build --tag httpd-centos .
docker history httpd-centos 
docker rm -fv sitio
docker run -d --name sitio -p 80:80 httpd-centos 
docker exec sitio env
docker exec sitio ls /var/www/html
```