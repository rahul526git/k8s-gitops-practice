# Step 1: Use a tiny, secure, production-ready Java Runtime Environment (JRE)
FROM eclipse-temurin:17-jre-alpine

# Step 2: Create a secure workspace directory
WORKDIR /app

# Step 3: Security Best Practice - Create a non-root system user
RUN addgroup -S appgroup && adduser -S appuser -G appgroup

# Step 4: Copy the pre-built JAR directly from the Jenkins build workspace
# (Jenkins just built this inside the 'target' folder)
COPY target/*.jar app.jar

# Step 5: Give ownership of the application folder to our secure user
RUN chown -R appuser:appgroup /app

# Step 6: Switch away from administrative 'root' privileges
USER appuser

# Step 7: Document the listening port
EXPOSE 8080

# Step 8: Define the runtime execution command
CMD ["java", "-jar", "app.jar"]
