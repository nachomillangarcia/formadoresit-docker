# OpenShift

OpenShift es una distribución de Kubernetes que añade funcionalidades centradas en la automatización, seguridad y *developer experience*.

Es una distribución propietaria de RedHat, muy utilizada a nivel empresarial por estas nuevas capas y por el soporte de esta compañía.

Puede ser desplegada en cualquier entorno (cloud, on-premise, local).

También puedes verla como OCP (OpenShift Container Platform)

Sitio web oficial: [https://www.openshift.com](https://www.openshift.com)

### OKD

OKD es la distribución de Kubernetes en la que se basa OpenShift. La principal diferencia entre ambos es que OKD es la distribución de código abierto, y sobre ella RedHat añade la capa de funciones *enterprise* que forman Openshift.

La arquitectura de ambas es exactamente la misma y todas las aplicaciones son compatibles. Puedes desplegar OKD de forma gratuita en cualquier entorno compatible. Las versiones de Openshift y OKD van de la mano.s

Anteriormente era llamada OpenShift Origin, es posible que aún veáis ese término.

Sitio web oficial: [https://www.okd.io](https://www.okd.io)

Diferencas entre Kubernetes, OKD y OpenShift: [https://www.openshift.com/learn/topics/kubernetes](https://www.openshift.com/learn/topics/kubernetes)

Más diferencias entre Kubernetes y OKD/OpenShift: [https://cloudowski.com/articles/10-differences-between-openshift-and-kubernetes](https://cloudowski.com/articles/10-differences-between-openshift-and-kubernetes)

### Versiones

Actualmente hay dos versiones con soporte: v3 y v4. Las aplicaciones desplegadas en cualquiera de ellas son completamente compatibles entre sí. Las mayores diferencias son a nivel de arquitectura y despliegue, nuevas funcionalidades en todos los campos, y una experiencia de usuario reformada.

Novedades de la v4:
- [https://www.openshift.com/blog/introducing-red-hat-openshift-4](https://www.openshift.com/blog/introducing-red-hat-openshift-4)
- [https://docs.okd.io/latest/whats_new/new-features.html]()

### Distribuciones para local

Minishift: Es OKD v3 para levantar en local. Crea una máquina virtual con una distribución de OKD v3 atuomáticamente.

CodeReady Containers (CRC): Es la v4. El funcionamiento es exactamente igual (una máquina virtual en local que levanta la plataforma), pero en este caso permite levantar tanto OpenShift con todas las funciones, como OKD.

CRC OpenShift: [https://developers.redhat.com/products/codeready-containers/overview](https://developers.redhat.com/products/codeready-containers/overview)

CRC OKD: [https://www.okd.io/crc.html](https://www.okd.io/crc.html)


### oc CLI

OpenShift incluye su propio CLI aparte de `kubectl`. Los comandos de ambos son prácticamente iguales, `oc` añade algunas funcionalidades interesantes e incluye todo lo necesario para trabajar con los objetos propios de OpenShift.

Instalación de oc: [https://docs.openshift.com/container-platform/4.5/cli_reference/openshift_cli/getting-started-cli.html#installing-the-cli](https://docs.openshift.com/container-platform/4.5/cli_reference/openshift_cli/getting-started-cli.html#installing-the-cli)

# Objetos propios de OpenShift

Todos los objetos que hemos visto en Kubernetes son válidos en OpenShift. Además de éstos, OpenShift añade nuevos objetos para soportar sus funcionalidades propias. Los más importantes que hemos visto son:

## BuildConfig

Define todo lo relativo a la construcción de un proyecto. En concreto tiene la información sobre el origen del código (`source`), la estrategia o método para construirlo (`strategy`) y el resultado (`output`), que en todo caso será siempre una imagen de Docker

Puedes crear una buildConfig con `oc apply -f bc.yaml`

Una BuildConfig puede construir Dockerfiles, código utilizando source2image o también Jenkinsfiles.

Referencia de las estrategias posibles: [https://docs.openshift.com/container-platform/4.5/builds/build-strategies.html](https://docs.openshift.com/container-platform/4.5/builds/build-strategies.html)

## Build 

Es simplemente una ejecución de una buildConfig

Puedes lanzar una build con `oc start-build`

## ImageStream

Es una abstracción de una imagen de Docker para su uso en OpenShift. No contiene imágenes en sí, sino simplemente referencias a éstas, que en realidad están alojadas en un Docker registry (por ejemplo, dockerHub o el registry interno en OpenShift)

El archivo `bc.yaml` también contiene una definición de ImageStream

## DeploymentConfig

Es equivalente al objeto Deployment en Kubernetes. De hecho, en OpenShift puedes desplegar aplicaciones utilizando cualquiera de los dos.
 
Añade la posibilidad de configurar `triggers` que lancen una actualización del deployment automáticamente. También permite distintas estrategias de actualización.

## Route

Permite configurar el router incluido con OpenShift para que dirija tráfico a tu aplicación. El router expone una IP pública, hacia la que se puede dirigir cualquier dominio. Con un Route se define qué dominio deber ser dirigido a tu servicio en concreto. También se pueden configurar distintas rutas y dividir el tráfico entre distintos servicios.

Puedes crear un Route con `oc apply -f route.yaml`

Referencia de todas las posibilidades de Route: [https://docs.openshift.com/container-platform/4.5/welcome/index.html](https://docs.openshift.com/container-platform/4.5/welcome/index.html)


# Componentes más importantes incluidos con OpenShift

[Docker Registry privado](https://docs.openshift.com/container-platform/4.5/registry/architecture-component-imageregistry.html)

[Operators](https://docs.openshift.com/container-platform/4.5/operators/understanding/olm-what-operators-are.html) (v4)

[Service Mesh](https://docs.openshift.com/container-platform/4.5/service_mesh/v1x/servicemesh-release-notes.html)  (v4)

[Monitorización](https://docs.openshift.com/container-platform/4.5/monitoring/cluster_monitoring/about-cluster-monitoring.html)




