FROM maven:3.9.3-eclipse-temurin-17 AS build

WORKDIR /opt/app

# Copy source code
COPY pom.xml .
COPY src ./src

# Run Sonar analysis
RUN mvn clean verify sonar:sonar -Dsonar.host.url=<SONAR_URL> -Dsonar.login=<SONAR_TOKEN>

# Package app
RUN mvn clean package -DskipTests

# Runtime image
FROM eclipse-temurin:17-jdk-alpine

WORKDIR /opt/app
COPY --from=build /opt/app/target/spring-boot-web.jar app.jar

ENTRYPOINT ["java","-jar","app.jar"]
