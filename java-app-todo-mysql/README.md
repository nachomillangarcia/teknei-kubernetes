
Para construir y ejecutar la app

```
docker volume create maven-repo
docker run --rm -v ${PWD}:/usr/src/myapp -v maven-repo:/root/.m2 -w /usr/src/myapp maven:3.6.3-jdk-8 mvn clean install
docker build -t java-todo .
docker network create java-todo
docker volume create java-mysql
docker run -d -e MYSQL_ROOT_PASSWORD=pass -e MYSQL_DATABASE=todo -e MYSQL_USER=todo -e MYSQL_PASSWORD=pass --name mysql --network java-todo -v java-mysql:/var/lib/mysql mysql
docker run -d --network java-todo -e DB_HOSTNAME=mysql -e DB_NAME=todo -e DB_USERNAME=todo -e DB_PASSWORD=pass -p 8080:8080 java-todo
```

Para simplemente ejecutar la imagen disponible en mi DockerHub:

```
docker network create java-todo
docker volume create java-mysql
docker run -d -e MYSQL_ROOT_PASSWORD=pass -e MYSQL_DATABASE=todo -e MYSQL_USER=todo -e MYSQL_PASSWORD=pass --name mysql --network java-todo -v java-mysql:/var/lib/mysql mysql
docker run -d --network java-todo -e DB_HOSTNAME=mysql -e DB_NAME=todo -e DB_USERNAME=todo -e DB_PASSWORD=pass -p 8080:8080 nachomillangarcia/java-todo-teknei
```

Acceder a [http://localhost:8080/login](http://localhost:8080/login)

Usuario: formadoresit

Contraseña: dummy
