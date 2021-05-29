# Creación de imagenes de Docker
---

## Dockerfile Inicial

- Archivo **Dockerfile**
  Este archivo y todo el material se encuentra en el directorio httpd-centos

    ```dockerfile
    FROM centos
    RUN yum install -y httpd
    CMD apachectl -DFOREGROUND
    ```

