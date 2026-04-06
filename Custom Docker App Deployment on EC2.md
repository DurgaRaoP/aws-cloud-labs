Good constraint. Clean, professional, no clutter. Use this directly.

---

Project 4: Custom Docker App Deployment on EC2

Overview
This project demonstrates how to build, containerize, and deploy a custom Python Flask application using Docker on an AWS EC2 instance. The application is exposed publicly via port 80 and supports runtime configuration using environment variables.

---

Objective
Deploy a custom application inside a Docker container and make it accessible through a public EC2 instance while understanding container lifecycle, debugging, and runtime configuration.

---

Architecture
User sends request to EC2 public IP on port 80
EC2 forwards request to Docker container
Docker container runs Flask application on port 5000

---

Technologies Used
AWS EC2 (Amazon Linux)
Docker
Python Flask
Gunicorn

---

Project Structure
app.py
requirements.txt
Dockerfile
README.md

---

Application Code (app.py)

from flask import Flask
import os

app = Flask(**name**)

version = os.getenv("VERSION", "v1")

@app.route("/")
def home():
return f"Project 4 Running - {version}"

---

Dependencies (requirements.txt)

flask
gunicorn

---

Dockerfile

FROM python:3.10-slim

WORKDIR /app

COPY requirements.txt .
RUN pip install -r requirements.txt

COPY . .

CMD ["gunicorn", "-w", "2", "-b", "0.0.0.0:5000", "app:app"]

---

Setup Steps

1. Connect to EC2 using SSH

2. Create project directory
   mkdir project4-docker-app
   cd project4-docker-app

3. Create required files
   app.py
   requirements.txt
   Dockerfile

4. Build Docker image
   docker build -t myapp:v1 .

5. Run container
   docker run -d -p 80:5000 myapp:v1

6. Access application
   Open browser and enter EC2 public IP

---

Version Upgrade

Build new image
docker build -t myapp:v2 .

Run with environment variable
docker run -d -p 80:5000 -e VERSION=v2 myapp:v2

---

Key Concepts Learned

Docker image vs container
Image is a blueprint, container is a running instance

Port mapping
Port 80 on EC2 is mapped to port 5000 inside container

Environment variables
Used to control application behavior without rebuilding image

Container lifecycle
Containers can stop or be removed, they are not permanent

Debugging
docker ps shows running containers
docker logs shows container logs

Production server
Flask development server is not suitable for production
Gunicorn is used for handling real traffic

---

Outcome

Successfully deployed a containerized application on EC2
Implemented version control using Docker images
Used environment variables for dynamic behavior
Handled real-world debugging scenarios

