# Lab 6: Managing Docker Environment Variables

## Steps:
- Cloned Python Flask app from GitHub
- Wrote Dockerfile using Python image
- Built Docker image named: app4

## 3 Ways to Pass Environment Variables:

### 1. Directly in command:
docker run -e APP_MODE=development -e APP_REGION=us-east

### 2. From a file:
docker run --env-file env.file

### 3. In Dockerfile using ENV:
ENV APP_MODE=production
ENV APP_REGION=canada-west

## Tested on:
- http://localhost:8081 → development, us-east
- http://localhost:8082 → staging, us-west
- http://localhost:8083 → production, canada-west
