# Docker cheatsheet

## Links útiles Docker

DockerHub: [https://hub.docker.com](https://hub.docker.com)


## Levantar contenedores
`docker run -p <PUERTO LOCAL>:<PUERTO CONTENEDOR> <IMAGEN>`

Ejemplo:

`docker run -p 8080:80 nginx`

Para levantar en background: `-d`

Ejemplo:

`docker run -d -p 8080:80 nginx`

## Construir imagen de Docker

`docker build -t <USUARIO>/<NOMBRE IMAGEN>:<TAG OPCIONAL> .`

## Subir imagen a DockerHub

`docker push USUARIO>/<NOMBRE IMAGEN>:<TAG OPCIONAL>`

## Listar contenedores

Contenedores levantados

`docker ps`

Todos (parados y levantados)

`docker ps -a`

## Dar un nombre a un contenedor

Al levantarlo:

`docker run --name <NOMBRE> <IMAGEN>`

Renombrar uno ya existente

`docker rename <ACTUAL> <NUEVO>`

## Parar un contenedor

`docker stop <NOMBRE O ID>`

## Levantar un contenedor parado

`docker start <NOMBRE O ID>`

## Eliminar un contenedor

`docker rm <NOMBRE O ID>`

Eliminar un contenedor encendido

`docker rm -f <NOMBRE O ID>`


## Obtener todos los datos de un contenedor

`docker inspect <NOMBRE O ID>`

## Ejecutar comandos dentro del contenedor

`docker exec <NOMBRE O ID> <COMANDO>`

Abrir un terminal dentro de un contenedor

`docker exec -ti <NOMBRE O ID> bash` o `docker exec -ti <NOMBRE O ID> sh`

Crear un nuevo contenedor y abrir un terminal en su interior

`docker run -it <IMAGEN> bash`. Por ejemplo `docker run -it ubuntu bash`

## Imprimir logs de un contenedor

`docker logs <NOMBRE O ID> <COMANDO>`

Para actualización automática

`docker logs -f <NOMBRE O ID> <COMANDO>`

## Enlazar contenedores

`docker run --link <NOMBRE DE OTRO CONTENEDOR>:<ALIAS OPCIONAL> <IMAGEN>`

Desde dentro del nuevo contenedor podrás conectarte al otro con el nombre del otro contenedor o con el alias que le hayas dado

Ejemplo: 

`docker run --link mysql <IMAGEN>`

Podrás acceder a mysql a utilizando el host `mysql`

## Volumenes

### Montar un directorio o archivo local

`docker run -v <RUTA LOCAL>:<RUTA EN EL CONTENEDOR>:<PERMISOS OPCIONAL> <IMAGEN>`

### Crear un volumen nuevo

`docker volume create <NOMBRE VOLUMEN>`

### Montar un volumen en un contenedor

`docker run -v <NOMBRE VOLUMEN>:<RUTA EN EL CONTENEDOR>:<PERMISOS OPCIONAL> <IMAGEN>`

