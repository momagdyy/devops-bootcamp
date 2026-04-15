# Lab 5: Multi-Stage Build

## Steps:
- Cloned Spring Boot app from GitHub
- Wrote Multi-Stage Dockerfile
- Built Docker image named: app3
- Ran container named: container3 from app3 image
- Tested app on: http://localhost:8080
- Stopped and deleted the container

## Image Size Comparison:
- app1 (Lab 3): Biggest  - Maven + Java + source code
- app2 (Lab 4): Smaller  - Java only, built outside
- app3 (Lab 5): Smallest - Multi-stage, no Maven in final image ✅

## Dockerfile Explanation:
- Stage 1: Use Maven image to build the app and generate JAR
- Stage 2: Use Java image to run the JAR only
- Result: Final image has no Maven = smallest size!
