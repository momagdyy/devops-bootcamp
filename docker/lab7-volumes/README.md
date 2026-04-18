# Lab 7: Docker Volume and Bind Mount with Nginx

## Steps:
- Created nginx_logs volume
- Created nginx-bind/html directory
- Created index.html with Hello from Bind Mount
- Ran Nginx container with Volume and Bind Mount
- Tested on: http://localhost
- Updated index.html and verified change immediately
- Verified logs stored in nginx_logs volume
- Deleted the volume

## Key Concepts:
- Volume: Docker manages storage, good for logs/databases
- Bind Mount: You manage storage, good for development
