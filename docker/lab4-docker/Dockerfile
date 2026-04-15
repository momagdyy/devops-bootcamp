# Use Java 17 base image
FROM eclipse-temurin:17-jre

# Create work directory
WORKDIR /app

# Copy only the JAR file into container
COPY target/demo-0.0.1-SNAPSHOT.jar .

# Expose port 8080
EXPOSE 8080

# Run the app
CMD ["java", "-jar", "demo-0.0.1-SNAPSHOT.jar"]