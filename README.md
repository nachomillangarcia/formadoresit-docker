# Docker cheatsheet

## Enlace a DockerHub
[https://hub.docker.com](https://hub.docker.com)


## Levantar contenedores
`docker run -d -p <PUERTO LOCAL>:<PUERTO CONTENEDOR> <IMAGEN>`

Ejemplo:

`docker run -d -p 8080:80 nginx`


## Construir imagen de Docker

`docker build -t <USUARIO>/<NOMBRE IMAGEN> .`

## Subir imagen a DockerHub

`docker push USUARIO>/<NOMBRE IMAGEN>`