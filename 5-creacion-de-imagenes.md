# Creación de imagenes de Docker
---

## Dockerfile Inicial
### ENV
- Archivo **Dockerfile**
  Este archivo y todo el material se encuentra en el directorio httpd-centos

    ```dockerfile
        FROM centos
        RUN yum install -y httpd
        CMD apachectl -DFOREGROUND
        COPY sitio /var/www/html
        ENV contenido prueba
        RUN echo "$contenido" > /var/www/html/prueba.html
        CMD apachectl -DFOREGROUND
    ```
## Construcción

```bash
docker build --tag httpd-centos .
docker history httpd-centos 
docker run -d --name sitio -p 80:80 httpd-centos 
docker exec sitio env
docker exec sitio ls /var/www/html
```