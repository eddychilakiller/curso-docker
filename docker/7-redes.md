# Redes

- Tipos:
  - Bridge: Red por defecto
  - Host:  Red de la máquina en la que estamos trabajando
  - None: una red sin conectividad 
  - Overlay: está disponible cuando trabajamos en un formato clúster, es decir que tenemos más de un host de Docker trabajando como uno solo, por lo que necesito que los contenedores puedan hablar entre sí, independientemente de dónde les haya tocado ejecutarse dentro del clúster.
- Conexión entre contenedores



La red de docker por defecto se llama docker0, por ejemplo

```bash

$ docker start centos1
$ docker inspect start centos1
$ docker network ls
$ docker network inspect bridge
$ docker start centos2
$ docker exec -it centos1 bash -c "ping 172.17.0.3"
$ docker exec -it centos1 bash -c "ping 172.17.0.2"

```

# Creacion de red

```bash

$ docker network create curso-network
$ docker network ls
$ docker network create -d bridge  --subnet 172.130.10.0/24 --gateway=172.130.10.1 docker-curso-network
$ docker network ls
$ docker network inspect docker-curso-network

# Para agregar un contenedor a una red distinta a la por defecto 
$ docker run  --network=docker-curso-network  --name=centos3 -d httpd-centos
$ docker run  --network=docker-curso-network  --name=centos4 -d httpd-centos

# Revisión sobre la visibilidad entre host
$ docker exec -it centos3 bash -c "ping 172.130.10.3"
$ docker exec -it centos4 bash -c "ping 172.130.10.2"


#Crear una nueva network
$ docker network create -d bridge  --subnet 172.130.11.0/24 --gateway=172.130.11.1 docker-curso-network-1
#Se agrega un contenedor a una nueva network
$ docker run  --network=docker-curso-network-1  --name=centos5 -d httpd-centos

# Prueba de conectividad 
$ docker exec -it centos3 bash -c "ping 172.130.11.2"
$ docker exec -it centos3 bash -c "ping centos5"

# Conectamos un contenedor en una network distinta a la recien creada 
$ docker network connect docker-curso-network-1 centos3
$ docker inspect centos3

# Prueba de conectividad 
$ docker exec -it centos3 bash -c "ping 172.130.11.2"
$ docker exec -it centos3 bash -c "ping centos5"

# Desconectamos un contenedor de una red 
$ docker network disconnect docker-curso-network-1 centos3

# Prueba de conectividad 
$ docker exec -it centos3 bash -c "ping 172.130.11.2"
$ docker exec -it centos3 bash -c "ping centos5"
$ docker inspect centos3


# Borrar contenedores
$ docker  network rm docker-curso-network docker-curso-network-1

```

# Generar un contenedor con una ip fija 
``bash 

$ docker network create -d bridge  --subnet 172.130.12.0/24 --gateway=172.130.12.1 docker-curso-network-2
$ docker run  --network=docker-curso-network-2 --ip 172.130.12.100 --name=centos6 -d httpd-centos
