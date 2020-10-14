# Despliegue de Oracle DB
```
docker run -d -it --name db -p 1521:1521 -p 8080:8080 store/oracle/database-enterprise:12.2.0.1
```

# Despliegue de weblogic
```
docker run --rm --name webl -p  7001:7001 -p 9002:9002 -e DOMAIN_NAME=base_domain -v <RUTA COMPLETA A domain.properties>:/u01/oracle/properties/domain.properties store/oracle/weblogic:12.2.1.3-dev
```