# Creación de imagenes de Docker
---

## Dockerfile Inicial
### ADD
- Archivo **Dockerfile**
  Este archivo y todo el material se encuentra en el directorio httpd-centos

    ```dockerfile
        FROM centos
        RUN yum install -y httpd
        ADD sitio /var/www/html
        CMD apachectl -DFOREGROUND
    ```
## Construcción

```bash
docker build --tag httpd-centos .
docker history httpd-centos 
docker run -d --name sitio -p 80:80 httpd-centos 
docker exec sitio ls /var/www/html
```