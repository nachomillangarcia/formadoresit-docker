# Kubernetes cheatsheet

Kubernetes es un **orquestador de contenedores**:

- Administra el despliegue de contenedores
- Preparado para entornos de producción

Kubernetes dispone de herramientas para levantar contenedores:

- En alta disponibilidad
- De forma segura
- Aislados de otras cargas de trabajo
- Conectados entre sí
- Expuestos a Internet
- Conectados con servicios en la nube

## Links de introducción

- [¿Qué es Kubernetes? Web oficial](https://kubernetes.io/es/docs/concepts/overview/what-is-kubernetes/)
- [Cómic](https://cloud.google.com/kubernetes-engine/kubernetes-comic)
- [Guía ilustrada](https://www.cncf.io/wp-content/uploads/2020/08/The-Illustrated-Childrens-Guide-to-Kubernetes.pdf)

## Instala Kubernetes en local
- [Windows](https://docs.docker.com/docker-for-windows/#kubernetes)
- [Mac](https://docs.docker.com/docker-for-mac/#kubernetes)
- [Linux](https://microk8s.io/)


# Comandos básicos
Crear objetos a partir de archivos YAML: `kubectl create -f <ARCHIVO>`
Listar objetos: `kubectl get <OBJETO>`. Por ejemplo: `kubectl get pod`
Ver detalles de un objeto en concreto: `kubectl get <OBJETO> <NOMBRE> -o yaml`. Por ejemplo: `kubectl get pod nginx -o yaml`
Ver descripción y eventos de un objeto en concreto: `kubectl describe <OBJETO> <NOMBRE>`. Por ejemplo: `kubectl describe pod nginx`
Eliminar un objeto en concreto: `kubectl delete <OBJETO> <NOMBRE>`


# Objetos de Kubernetes
## Nodos
Son los servidores físicos que forman parte del clúster.

Lista todos los nodos con `kubectl get nodes`

## Pod
Un Pod en Kubernetes es un objeto que define una **carga de trabajo**. Es decir, un Pod es uno o varios contenedores que son ejecutados conjuntamente en Kubernetes.

Crea un pod con `kubectl apply -f pod-nginx.yaml`

Lista todos los pod con `kubectl get pod`

Ver la descripción del pod:  `kubectl describe pod nginx`

## Deployments
El objeto Deployment define una aplicación con varias réplicas. El Deployment a su vez crea y gestiona los pods que corresponden a esa definición.

Crea un deployment con `kubectl apply -f deployment.yaml`

Lista todos los deployment con `kubectl get deploy`

## DaemonSet
El objeto DaemonSet despliega un pod (solo uno) en cada nodo del clúster

Crea un DaemonSet con `kubectl apply -f daemonset.yaml`

Lista todos los DaemonSet con `kubectl get ds`

## Statefulset
El objeto Statefulset define una aplicación que tiene datos persistentes en disco (por ejemplo una base de datos). Es prácticamente igual que el deployment, pero levanta los pods siempre con un nombre fijo de forma que los datos pueden persistir entre despliegues y reinicios.

Crea un statefulset con `kubectl apply -f statefulset.yaml`

Lista todos los statefulset con `kubectl get statefulset`

## Job
El objeto Job define una carga de trabajo puntual, una tarea que finalizará con éxito en algún momento.

Crea un job con `kubectl apply -f job.yaml`

Lista todos los job con `kubectl get job`

## CronJob
El objeto CronJob crea jobs de forma periódica. Por ejemplo, todas las noches, para ejecutar tareas cada cierto tiempo

Crea un job con `kubectl apply -f cronjob.yaml`

Lista todos los job con `kubectl get cronjob`