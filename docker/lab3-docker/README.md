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

## ScreenShots:
<img width="1916" height="972" alt="Screenshot 2026-04-14 231653" src="https://github.com/user-attachments/assets/353d1cb9-e2c0-4556-930b-beacd80a5321" />
<img width="642" height="136" alt="Screenshot 2026-04-14 233348" src="https://github.com/user-attachments/assets/f73fd9db-863d-4958-a4b1-66c9964850b4" />


