
FROM maven:3.8.6 AS build-stage

WORKDIR /app

COPY pom.xml .
COPY src ./src

RUN mvn clean package -DskipTests

FROM openjdk:8-jdk-alpine

WORKDIR /app

COPY --from=build-stage /app/target/users-api-0.0.1-SNAPSHOT.jar  .

EXPOSE 8080

CMD ["java", "-jar", "users-api-0.0.1-SNAPSHOT.jar"]