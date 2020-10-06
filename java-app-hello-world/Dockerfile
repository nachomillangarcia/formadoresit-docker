FROM openjdk:8-jdk-alpine
WORKDIR /app
COPY target/hello-world-rest-api.jar hello-world-rest-api.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "/app/hello-world-rest-api.jar"]
