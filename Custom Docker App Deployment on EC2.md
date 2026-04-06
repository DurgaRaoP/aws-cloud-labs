# Project 4: Custom Docker App Deployment on EC2

## Objective

To build, containerize, and deploy a custom Python Flask application using Docker on an EC2 instance and make it accessible over the internet.

---

## Services and Tools Used

* Amazon EC2 (Amazon Linux)
* Docker
* Python Flask
* Gunicorn

---

## Architecture

User → EC2 → Docker → Flask Application

---

## Application Overview

A simple Flask-based web application that returns a response with version information. The version is controlled using environment variables, allowing dynamic behavior without rebuilding the image.

---

## Project Structure

app.py
requirements.txt
Dockerfile
README.md

---

## Application Code

from flask import Flask
import os

app = Flask(**name**)

version = os.getenv("VERSION", "v1")

@app.route("/")
def home():
return f"Project 4 Running - {version}"

---

## Dependencies

flask
gunicorn

---

## Dockerfile

FROM python:3.10-slim

WORKDIR /app

COPY requirements.txt .
RUN pip install -r requirements.txt

COPY . .

CMD ["gunicorn", "-w", "2", "-b", "0.0.0.0:5000", "app:app"]

---

## Environment Setup

1. Launch EC2 instance (Amazon Linux)
2. Connect using SSH
3. Install Docker
4. Start and enable Docker service

---

## Deployment Steps

### Build Docker Image

docker build -t myapp:v1 .

### Run Container

docker run -d -p 80:5000 myapp:v1

### Access Application

Open browser and use EC2 public IP

---

## Version Upgrade

### Build New Image

docker build -t myapp:v2 .

### Run with Environment Variable

docker run -d -p 80:5000 -e VERSION=v2 myapp:v2

---

## Key Concepts

Docker Image vs Container
An image is a blueprint, while a container is a running instance

Port Mapping
External port 80 is mapped to internal port 5000

Environment Variables
Used to dynamically control application behavior

Container Lifecycle
Containers are temporary and must be managed explicitly

Debugging
docker ps shows running containers
docker logs shows application logs

Production Server
Gunicorn is used instead of Flask development server

---

## Outcome

Successfully deployed a containerized application on EC2
Implemented version control using Docker images
Configured runtime behavior using environment variables
Handled real-world debugging scenarios

---

## Conclusion

This project demonstrates the complete lifecycle of building, deploying, and managing a containerized application using Docker on AWS EC2, including version upgrades and runtime configuration.

---
