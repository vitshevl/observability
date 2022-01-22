
FROM maven:3.8-jdk-11 as app-builder
WORKDIR /var/src/app
COPY . .
RUN mvn -DskipTests package && mv target/*.jar target/app.jar

FROM adoptopenjdk:11-jre-hotspot

#Copy executable jar file from the builder image
COPY ./target/health-service-1.0-SNAPSHOT.jar $APP_HOME/health-service-1.0-SNAPSHOT.jar
WORKDIR $APP_HOME

ENTRYPOINT [ "sh", "-c", "java $JAVA_OPTS -jar health-service-1.0-SNAPSHOT.jar"]