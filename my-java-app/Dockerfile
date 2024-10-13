# Use a base image that has Java installed
FROM openjdk:11-jre-slim

# Set the working directory inside the container
WORKDIR /app

# Copy the pom.xml and download dependencies
COPY pom.xml .
RUN mvn dependency:go-offline

# Copy the entire project
COPY . .

# Package the application (this will create the jar file)
RUN mvn package

# Command to run the application
CMD ["java", "-jar", "target/my-java-app-1.0-SNAPSHOT.jar"]
