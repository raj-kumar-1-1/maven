# Use the official Maven image to build the application
FROM maven:3.8.1-openjdk-11 AS build

# Set the working directory
WORKDIR /app

# Copy the pom.xml and the source code
COPY pom.xml .
COPY src ./src

# Package the application
RUN mvn clean package -DskipTests

# Use a smaller image to run the application
FROM openjdk:11-jre-slim

# Copy the jar file from the build stage
COPY --from=build /app/target/my-java-app-0.0.1-SNAPSHOT.jar /app.jar

# Expose the port that the app runs on
EXPOSE 8080

# Run the application
ENTRYPOINT ["java", "-jar", "/app.jar"]
