# Contenedores
---
- Son una instancia de ejecución de una imagen
- Son temporales
- Estan construidos sobre capas

## Puertos

```bash 
# Descarga de imagenes
$ docker pull httpd


# Ayuda de Docker
$ docker run --help|less

# Ejecución de un contenedor 
$ docker run -d --name sitio80 -p 80:80 httpd

# Ejecución de un contenedor con otro puerto
docker run -d --name sitio81 -p 81:80 httpd


# Ejecución de un contenedor con otro puerto
docker run -d --name sitio8081 -p 8081:80 httpd

# Eliminacion de contenedores
docker rm -fv sitio80 sitio81 sitio8081
```

## Iniciar, detener y reiniciar un contendor

```bash 
# arrancar un contenedor
$ docker run -d --name sitio80 -p 80:80 httpd

# cambiar el nombre del contenedor
$ docker rename sitio80 sitio

# Listar el contenedor 
$ docker ps

# reiniciar un contenedor
$ docker restart sitio

# detener un contenedor
$ docker stop sitio

# iniciar un contenedor
$ docker start sitio

```

