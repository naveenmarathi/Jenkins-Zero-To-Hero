# Use Java 17 base image
FROM eclipse-temurin:17-jdk-alpine

# Artifact path
ARG artifact=target/spring-boot-web.jar

WORKDIR /opt/app

# Copy jar
COPY ${artifact} app.jar

# Run app
ENTRYPOINT ["java","-jar","app.jar"]
