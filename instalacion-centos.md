# Instalación con CentOS
---

## Utilidades

`sudo yum install -y yum-utils device-mapper-persistent-data lvm2`

## Agregar el repo de docker

`sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo`


## Instalar docker

`sudo yum install docker-ce -y`


## Iniciar el servicio

`sudo systemctl start docker`


## Iniciarlo con el sistema

`sudo systemctl enable docker`


## Agregar usuario al grupo docker 

`whoami # Saber el nombre de tu usuario`
`sudo usermod -aG docker nombre_de_salida_en_whoami`


## Salir de la sesión

`exit`


## Iniciar de nuevo con el usuario y probar 

`docker run hello-world`
