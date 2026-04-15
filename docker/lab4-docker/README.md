# Lab 4: Run Java Spring Boot App in a Container

## Steps:
- Cloned Spring Boot app from GitHub
- Built app locally using: mvn package -DskipTests
- Wrote Dockerfile using Java 17 base image
- Built Docker image named: app2
- Ran container named: container2 from app2 image
- Tested app on: http://localhost:8080
- Stopped and deleted the container

## Difference from Lab 3:
- Lab 3: Build inside container using Maven image
- Lab 4: Build outside container, copy only JAR file
- Result: app2 is smaller in size than app1 ✅

## Dockerfile Explanation:
- FROM: Base image with Java 17 only
- WORKDIR: Set working directory to /app
- COPY: Copy only JAR file into container
- EXPOSE: Open port 8080
- CMD: Run the app when container starts
