# Instalación
---
## Minikube

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

## Instalación de Kubernetes

`curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-latest.x86_64.rpm`
`sudo rpm -Uvh minikube-latest.x86_64.rpm`
`minikube start`
`minikube start --driver=docker`
`minikube config set driver docker`
# Instalación de Kubectl
`curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"`
`sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl`



## minikube kubectl 
`kubectl version --client`

`kubectl get namespaces`

`kubectl get pod --all-namespaces`

`minikube status`

`minikube stop`

`minikube start`

`kubectl api-resources`

`kubectl api-resources -o wide`
