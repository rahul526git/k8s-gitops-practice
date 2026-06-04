# Use the official, production-ready Eclipse Temurin Java 11 runtime image
FROM eclipse-temurin:11-jre-alpine
WORKDIR /app

# Copy the compiled .jar file from the target directory into the container
COPY target/java-app-1.0-SNAPSHOT.jar app.jar

# Command to run the application
CMD ["java", "-jar", "app.jar"]
