# Lab 9: Containerized Node.js and MySQL Stack Using Docker Compose

## Application Structure:
- server.js  → Main Node.js app connects to MySQL
- db.js      → Creates database and tables
- frontend/  → HTML page showing iVolve offices
- Dockerfile → Build Node.js app image

## What is Docker Compose:
- Tool to run multiple containers at once
- One file describes all containers
- One command starts everything

## Services:

### App Service:
- Built from local Dockerfile
- Runs on port 3000
- Connects to MySQL using environment variables:
  - DB_HOST=db
  - DB_USER=root
  - DB_PASSWORD=rootpassword
  - DB_NAME=ivolve

### DB Service:
- Uses MySQL 8.0 image
- Creates ivolve database automatically
- Data persisted using db_data volume

## Steps:

### 1. Clone the Code
git clone https://github.com/Ibrahim-Adel15/kubernets-app.git

### 2. Create docker-compose.yml
- Defined app and db services
- Set environment variables
- Created db_data volume for MySQL data
- Created logs volume for app logs

### 3. Start Everything
docker-compose up -d

### 4. Verify App
- http://localhost:3000       → Main page
- http://localhost:3000/health → Health check
- http://localhost:3000/ready  → Ready check

### 5. Verify Logs
docker exec kubernets-app-app-1 cat /app/logs/access.log

### 6. Push to DockerHub
docker tag kubernets-app-app your-dockerhub-username/ivolve-app:latest
docker push your-dockerhub-username/ivolve-app:latest

## Test Results:
- Main page    → iVolve offices page ✅
- /health      → iVolve web app is working! ✅
- /ready       → iVolve web app is ready! ✅
- Logs         → access.log created ✅
- DockerHub    → Image pushed successfully ✅
