# Stage 1: Build with Maven
FROM maven:3.9.5-eclipse-temurin-17 AS build

WORKDIR /app
COPY . .

RUN mvn clean package -DskipTests

# Stage 2: Run the app with a lightweight JDK image
FROM eclipse-temurin:17-jdk-alpine

WORKDIR /app
COPY --from=build /app/target/proddaturiMinApp.jar app.jar

EXPOSE 8080

CMD ["java", "-jar", "app.jar"]
