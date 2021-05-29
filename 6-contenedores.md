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

## Ingresar a un contenedor

```bash

# Pull de una imagen 
$ docker pull jenkins/jenkins

# ejecución de un contenedor 
$  docker run -p 8080:8080 -p 50000:50000 -d --name=jenkins  jenkins/jenkins

# Ingreso a un contenedor
$ docker exec -it jenkins bash

# como otro usuario
$ docker exec -u root -it jenkins bash

```


## Ingresar a un contenedor

```bash

# Pull de una imagen 
$ docker pull jenkins/jenkins

# ejecución de un contenedor 
$  docker run -p 8080:8080 -p 50000:50000 -d --name=jenkins  jenkins/jenkins

# Ingreso a un contenedor
$ docker exec -it jenkins bash

# como otro usuario
$ docker exec -u root -it jenkins bash

```

## Creación de contenedores con variables de entorno

```bash
# Descarga de MySSQL 5.7.34
$ docker pull  mysql:5.7.34

#Ejecución del contenedor
$ docker run --name mysql-database -e MYSQL_ROOT_PASSWORD=password -e MYSQL_DATABASE=employees -p 3306:3306  -d mysql:5.7.34

# Copiar archivos a tu contenedor
docker cp test_db-master.zip mysql-database:/tmp/test_db-master.zip

# restaurar la base de datos
docker exec -it mysql-database bash
apt update
apt install unzip
unzip test_db-master.zip
mysql -u root -p employees < employees.sql








```