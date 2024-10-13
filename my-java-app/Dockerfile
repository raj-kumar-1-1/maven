# Use the official Maven image to build the application
#FROM maven:3.8.1-openjdk-11 AS build

# Set the working directory
#WORKDIR /app

# Copy the pom.xml and the source code
#COPY pom.xml .
#COPY src ./src

# Package the application
#RUN mvn clean package -DskipTests

# Use a smaller image to run the application
#FROM openjdk:11-jre-slim

# Copy the jar file from the build stage
#COPY --from=build /app/target/my-java-app-1.0-SNAPSHOT.jar /app.jar

# Expose the port that the app runs on
#EXPOSE 8080

# Run the application
#ENTRYPOINT ["java", "-jar", "/app.jar"]
# Stage 1: Build the application
# Use an OpenJDK base image with Maven pre-installed
#FROM maven:3.8.5-openjdk-11 AS build

# Set the working directory inside the container
#WORKDIR /app

# Copy the pom.xml and source code to the container
#COPY pom.xml .
#COPY src ./src

# Build the application
#RUN mvn clean package -DskipTests

# Use a smaller base image for the final image
#FROM openjdk:11-jre-slim

# Set the working directory in the final image
#WORKDIR /app

# Copy the jar file from the build stage to the final image
#COPY --from=build /app/target/my-java-app-1.0-SNAPSHOT.jar /app.jar

# Command to run the application
#CMD ["java", "-jar", "my-java-app.jar"]

FROM maven:3.8.4-openjdk-11 AS build
WORKDIR /app
COPY pom.xml .
COPY src ./src
RUN mvn clean package -DskipTests

# Stage 2: Create a lightweight image with the application
FROM openjdk:11-jre-slim
COPY --from=build /app/target/my-java-app-1.0-SNAPSHOT.jar /app.jar  # Updated the JAR file name
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "/app/my-java-app-1.0-SNAPSHOT.jar"]

