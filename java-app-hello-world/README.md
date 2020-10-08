# java-app-hello-world

## Construir y desplegar
```
mvn package
docker build -t java-hello .
docker run -p 8080:8080 java-hello 
```

## Desplegar la imagen subida a DockerHub
```
docker run -p 8080:8080 nachomillangarcia/java-hello 
```

Accede a [http://localhost:8080/hello-world](http://localhost:8080/hello-world)