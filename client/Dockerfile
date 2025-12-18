FROM maven:3.9.6-eclipse-temurin-17 AS builder
WORKDIR /app
COPY ./src ./src
COPY ./pom.xml .
RUN mvn clean package -DskipTests

FROM openjdk:17-jdk-alpine
VOLUME /tmp
ARG JAR_FILE=target/*.jar
COPY ${JAR_FILE} client-service.jar
ENTRYPOINT ["java","-jar","/client-service.jar"]