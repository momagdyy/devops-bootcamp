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
<img width="1916" height="1022" alt="Screenshot 2026-04-20 022333" src="https://github.com/user-attachments/assets/64e5e07a-1272-4ef5-b22b-39014869c3e4" />
<img width="1919" height="966" alt="Screenshot 2026-04-20 022326" src="https://github.com/user-attachments/assets/f18df066-f75d-455e-9763-ef59885b1a2c" />
<img width="1919" height="1014" alt="Screenshot 2026-04-20 022310" src="https://github.com/user-attachments/assets/821521ff-dd8e-40ed-9cd1-fdcbaeed2202" />
<img width="651" height="48" alt="Screenshot 2026-04-20 022434" src="https://github.com/user-attachments/assets/68036f09-0b13-4d75-be0a-4af1fceb098a" />
<img width="1560" height="333" alt="Screenshot 2026-04-20 022358" src="https://github.com/user-attachments/assets/5aa5e116-f33f-41dc-976d-a257366580df" />




