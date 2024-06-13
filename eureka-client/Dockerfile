FROM maven:3.8.4-openjdk-17 as build
WORKDIR /app

COPY pom.xml .
COPY src ./src

RUN mvn clean package -DskipTests

FROM openjdk:17-slim
COPY --from=buld /app/target/*.jar app.jar
ENTRYPOIN ["java", "-jar", "/app.jar"]