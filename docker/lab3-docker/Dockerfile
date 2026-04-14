# Use Maven base image with Java 17
FROM maven:3.9.6-eclipse-temurin-17

# Create work directory
WORKDIR /app

# Copy source code into container
COPY . .

# Build the app
RUN mvn package -DskipTests

# Expose port 8080
EXPOSE 8080

# Run the app
CMD ["java", "-jar", "target/demo-0.0.1-SNAPSHOT.jar"]