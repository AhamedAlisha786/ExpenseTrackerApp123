# --- Backend Dockerfile ---

# Build stage (Maven + Java 22)
FROM maven:3.9.6-eclipse-temurin-22 AS build
WORKDIR /app

COPY pom.xml .
RUN mvn dependency:go-offline

COPY src ./src
RUN mvn clean package -DskipTests

# Runtime stage (JDK 22 only, lighter image)
FROM openjdk:22-slim
WORKDIR /app

COPY --from=build /app/target/*.jar app.jar

EXPOSE 8090
ENTRYPOINT ["java","-jar","app.jar"]
