# Lab 8: Custom Docker Network for Microservices

## Application Structure:
- backend/app.py  → Simple Flask API returns 'Hello from Backend!'
- frontend/app.py → Calls backend using http://backend:5000

## Steps:

### 1. Clone the Code
git clone https://github.com/Ibrahim-Adel15/Docker5.git

### 2. Create Dockerfile for Backend
- Used Python 3.9-slim image
- Installed Flask
- Exposed port 5000
- Runs app.py on startup

### 3. Create Dockerfile for Frontend
- Used Python 3.9-slim image
- Installed packages from requirements.txt
- Exposed port 5000
- Runs app.py on startup

### 4. Build Both Images
docker build -t backend-image ./backend
docker build -t frontend-image ./frontend

### 5. Create Custom Network
docker network create ivolve-network

### 6. Run Backend on ivolve-network
docker run -d --name backend --network ivolve-network backend-image
- No port mapping needed (only frontend talks to it)
- Container named 'backend' so frontend can find it by name

### 7. Run Frontend1 on ivolve-network
docker run -d -p 5001:5000 --name frontend1 --network ivolve-network frontend-image
- Same network as backend
- CAN communicate with backend

### 8. Run Frontend2 on Default Network
docker run -d -p 5002:5000 --name frontend2 frontend-image
- Different network from backend
- CANNOT communicate with backend

## Test Results:
- http://localhost:5001 → 'Frontend received: Hello from Backend!'✅
- http://localhost:5002 → 'Could not connect to backend.' ❌

## Key Concepts:

### Docker Network:
- Containers are isolated by default
- Same network = can communicate
- Different network = cannot communicate

### Docker DNS:
- Docker resolves container NAMES to IP automatically
- frontend calls 'http://backend:5000'
- Docker finds container named 'backend' automatically
- Only works on same network!

### Why Custom Network:
- Better isolation
- Better security
- Containers communicate by name not IP
- Professional microservices setup
