FROM maven:3.6.3-jdk-8 AS build

WORKDIR /app

COPY . .

RUN mvn clean install

FROM tomcat:8.0.51-jre8

RUN rm -rf /usr/local/tomcat/webapps/*

COPY --from=build /app/target/*.war /usr/local/tomcat/webapps/ROOT.war

CMD ["catalina.sh","run"]
