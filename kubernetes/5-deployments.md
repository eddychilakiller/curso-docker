# Deployments

Una implementación proporciona actualizaciones declarativas para pods y ReplicaSets.

En un deployment se  describe un estado deseado y mediante un controlador de deployments cambia el estado real al estado deseado a una velocidad controlada. Se pueden  definir deployments para crear nuevos ReplicaSets o para eliminar deployments existentes y adoptar todos sus recursos con nuevas Implementaciones.

![Deployment](images/deployment.png)


```yaml

apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:1.14.2
        ports:
        - containerPort: 80

```


`kubectl get deploy`
`kubectl get deploy nginx-deployment -o yaml`
`kubectl roolout status deployment nginx-deployment`
`kubectl get deploy --show-labels`
`kubectl get rs --show-labels`
`kubectl get po --show-labels`

## Rolling updates

```yml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx
spec:
  replicas: 3
  revisionHistoryLimit: 3
# revisionHistoryLimit: 10
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx
        ports:
        - containerPort: 80
```

# Histórico y revisiones de los despliegues

`kubectl rollout history deployment nginx-deployment`

```yml
apiVersion: apps/v1
kind: Deployment
metadata:
  annotations:
    kubernetes.io/change-cause: "Se agregan anotaciones de cambios"
  name: nginx-deployment
  labels:
    app: nginx
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx
        ports:        
        - containerPort: 80
```

Revisamos revisiones
`kubectl rollout history deployment nginx-deployment`

Revisamos una revision
`kubectl rollout history deployment nginx-deployment --revision=3`

Haciendo un rollback
`kubectl rollout undo deployment nginx-deployment --to-revision=2`