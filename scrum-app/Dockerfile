FROM maven:3.6.1-jdk-8-slim AS build

WORKDIR /workspace
COPY pom.xml /workspace
COPY src /workspace/src
RUN mvn clean package -DskipTests

FROM openjdk:8-alpine
COPY --from=build /workspace/target/*.jar app.jar
EXPOSE 8080
ENTRYPOINT ["java","-jar","app.jar"]
