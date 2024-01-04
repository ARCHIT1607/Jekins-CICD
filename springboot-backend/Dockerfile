# Use an official Maven image with OpenJDK 17 as the base image
FROM maven:3-openjdk-17-slim AS builder

# Set the working directory in the container
WORKDIR /app

# Copy the POM file to the container
COPY ./ .

# Download the dependencies and package the application
RUN mvn clean install -DskipTests

# Copy the application JAR file to the container
# COPY target/springboot-backend-0.0.1-SNAPSHOT.jar /app/app.jar

# Use a smaller base image for the final image
FROM openjdk:17-slim

# Set the working directory in the container
WORKDIR /app

# Copy the JAR file from the builder stage
COPY --from=builder /app/target/springboot-backend-0.0.1-SNAPSHOT.jar /app/app.jar

# Set the entry point for the container
ENTRYPOINT ["java", "-jar", "app.jar"]
