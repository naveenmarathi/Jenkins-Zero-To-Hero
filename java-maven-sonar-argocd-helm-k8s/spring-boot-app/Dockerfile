# Build stage
FROM maven:3.9.3-eclipse-temurin-17 AS build

WORKDIR /opt/app

# Copy pom and source
COPY pom.xml .
COPY src ./src

# Build the JAR (skip tests if needed)
RUN mvn clean package -DskipTests

# Runtime stage
FROM eclipse-temurin:17-jdk-alpine

WORKDIR /opt/app

# Copy JAR from build stage
COPY --from=build /opt/app/target/spring-boot-web.jar app.jar

# Run the app
ENTRYPOINT ["java", "-jar", "app.jar"]
