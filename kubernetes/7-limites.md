# Limites

Cuando especificas un pod, puedes especificar opcionalmente cuánto de cada recurso necesita un contenedor. Los recursos más comunes para especificar son CPU y memoria (RAM).

Cuando especificas la solicitud de recursos para los contenedores en un pod, el scheduler usa esta información para decidir en qué nodo colocar el pod. Cuando especificas un límite de recursos para un contenedor, kubelet aplica esos límites para que el contenedor en ejecución no pueda usar más de ese recurso que el límite que estableciste. kubelet también reserva al menos la cantidad de solicitud de ese recurso del sistema específicamente para que lo use ese contenedor.

## Límites
Cantidad máxima (no garantizada) de recursos que puede consumir el pod.

* spec.containers[].resources.limits.cpu
* spec.containers[].resources.limits.memory
* spec.containers[].resources.limits.hugepages-<size>
## Request
Cuantos recursos garantizados va a disponer el pod.

* spec.containers[].resources.requests.cpu
* spec.containers[].resources.requests.memory
* spec.containers[].resources.requests.hugepages-<size>


Los límites y las solicitudes de recursos de CPU se miden en unidades de CPU. Una cpu, en Kubernetes, equivale a 1 vCPU / Core para proveedores de nube y 1 hyperthread en procesadores Intel bare-metal.
La cantidad de CPU se puede dar como: 0.5 (mitad de cpu), que es equivalente a 100m (100 milicores)

La memoria está medida en bytes,  se puede usar potencias de 2 como Ei, Pi, Ti, Gi, Mi, Ki por ejemplo:
9048, 128Mi, 345Gi