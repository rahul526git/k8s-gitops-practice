# === STAGE 1: Cached Builder Sandbox ===
FROM maven:3.9.6-eclipse-temurin-17 AS builder
WORKDIR /app

# Cache dependency layer cleanly for Java 17 plugins
COPY pom.xml .
RUN mvn dependency:go-offline -B

# Copy source directory and package verified jar
COPY src ./src
RUN mvn clean package -DskipTests

# === STAGE 2: Secure Production Runtime ===
FROM eclipse-temurin:17-jre-alpine
WORKDIR /app

# Establish restricted system security user
RUN addgroup -S appgroup && adduser -S appuser -G appgroup

# Extract only the final artifact from Stage 1
COPY --from=builder /app/target/*.jar app.jar
RUN chown -R appuser:appgroup /app

# Drop root privilege access entirely
USER appuser

EXPOSE 8080
CMD ["java", "-jar", "app.jar"]
