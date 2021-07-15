# course_sonarqube

## 1.- Levantar el servicio de docker de Sonar View
```
docker run -d --name sonarqube -p 9000:9000 sonarqube:7.5-community
```

## 2.- Login en
- http://localhost:9000
- USR: admin
- PWD: admin

## 3.- Ir a ​ http://localhost:9000/account/security/​ para generar un nuevo token
para el escaneo de nuestro código a revisar


## 4.- Click en generar y guardar el token generado

## 5.- Generar el Sonar de SonarQube 

## 6.- Construir la imagen Sonar de SonarQube 

```
docker build --network=host --tag sonar-scanner-image:latest --build-arg  SONAR_HOST="http://localhost:9000" --build-arg SONAR_LOGIN_TOKEN="TOKEN_VALUE" .
```

## Test Código

```
docker pull sonarsource/sonar-scanner-cli 
```



```
FROM sonarsource/sonar-scanner-cli AS sonarqube_scan
WORKDIR /app
COPY . .
RUN ls -list
RUN sonar-scanner \
	-Dsonar.host.url="http://localhost:9000" \
	-Dsonar.projectKey="TOKEN_SONAR" \
	-Dsonar.sources="."
```


```
docker build --network=host --no-cache -t scanner-app -f  Dockerfile.test .
```





