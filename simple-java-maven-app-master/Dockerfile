#

# Build stage

#

FROM maven:3-jdk-11-slim AS build

COPY src /var/sapp/src

COPY pom.xml /var/sapp

RUN mvn -f /var/sapp/pom.xml clean package

#

# Package stage

#


FROM openjdk:11-jre-slim

COPY --from=build /var/sapp/target/my-app-1.0-SNAPSHOT.jar /usr/local/lib/

EXPOSE 8080

ENTRYPOINT ["java","-jar","/usr/local/lib/my-app-1.0-SNAPSHOT.jar"]

