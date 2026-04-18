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

## Screenshots:
<img width="1919" height="1016" alt="Screenshot 2026-04-18 212546" src="https://github.com/user-attachments/assets/dfde88d7-4424-477f-88a9-9d7a70e73444" />
<img width="1919" height="1014" alt="Screenshot 2026-04-18 212641" src="https://github.com/user-attachments/assets/b3424e38-0ad5-4302-b503-1c32d2c5650e" />
<img width="1908" height="971" alt="Screenshot 2026-04-18 212626" src="https://github.com/user-attachments/assets/0422c456-68e5-4a72-8147-547b12c9ab63" />

