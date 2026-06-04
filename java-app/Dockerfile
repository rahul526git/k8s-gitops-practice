# Stage 1: Runtime environment
FROM openjdk:11-jre-slim
WORKDIR /app

# Copy the compiled .jar file from the target directory into the container
COPY target/java-app-1.0-SNAPSHOT.jar app.jar

# Command to run the application
CMD ["java", "-jar", "app.jar"]
