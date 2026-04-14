# Lab 3: Run Java Spring Boot App in a Container

## Steps:
- Cloned Spring Boot app from GitHub
- Wrote Dockerfile using Maven + Java 17 base image
- Built Docker image named: app1
- Ran container named: container1 from app1 image
- Tested app on: http://localhost:8080
- Stopped and deleted the container

## Dockerfile Explanation:
- FROM: Base image with Maven and Java 17
- WORKDIR: Set working directory to /app
- COPY: Copy source code into container
- RUN: Build app and generate JAR file
- EXPOSE: Open port 8080
- CMD: Run the app when container starts
