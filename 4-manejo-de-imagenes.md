# Manejo de imagenes de Docker
---
## Bajar imagenes del repositorio público

`docker pull httpd`

## Bajar imagenes del repositorio público con un tag


`docker pull httpd:alpine`

## Listar imagenes

`docker images`

## Borrar imágenes

`docker rm httpd`


## Plantilla básica de un dockerfile

```dockerfile
FROM centos
RUN yum install -y httpd
```

## Construcción y ejecución de una imagen 
```bash
# Se contruye la imagen
docker build --tag httpd-centos .
# Si se desea usar una versión en específico se anota
docker build --tag httpd-centos:1.0 .
# Ejecución de una imagen en un contenedor
docker run -d httpd-centos 
# Se inspecciona para ver sí está siendo ejecutado el contenedor
docker ps
# En este caso se ejecutó y acabó la tarea, por lo que hay que buscar en todas las imagenes ejecutadas
docker ps -a 
```
```