# Project 5: Multi-Container Application using Docker Compose

## Objective

To deploy a multi-container application using Docker Compose, where a Flask application communicates with a PostgreSQL database.

---

## Architecture

User → EC2 → Docker Compose → Flask App → PostgreSQL

---

## Technologies Used

AWS EC2 (Amazon Linux)
Docker
Docker Compose
Python (Flask)
PostgreSQL

---

## Project Structure

app/
    app.py
    requirements.txt
    Dockerfile

docker-compose.yml
README.md

---

## Application Overview

This project demonstrates how a backend application connects to a database running in a separate container using Docker networking. The application verifies database connectivity and returns a response in the browser.

---

## Setup Instructions

1. Launch an EC2 instance and connect via SSH

2. Install Docker

3. Clone the repository

4. Navigate to project directory

5. Start services
   docker compose up -d

6. Access application
   http://<EC2-Public-IP>

---

## Key Concepts

Multi-container architecture
Running multiple services using Docker Compose

Service-to-service communication
Containers communicate using service names as hostnames

Environment variables
Used to configure database connection dynamically

Container networking
Docker automatically creates a network for services

Data persistence
PostgreSQL data is stored using Docker volumes

---

## Data Persistence

A Docker volume is used to store PostgreSQL data.
This ensures that data remains intact even after containers are stopped or recreated.

---

## Outcome

Successfully deployed a multi-container application
Established communication between application and database
Implemented persistent storage using Docker volumes
Gained hands-on experience with real-world debugging

---

## Conclusion

This project demonstrates how to build and manage a multi-container application using Docker Compose. It highlights key concepts such as container networking, environment configuration, and persistent storage, which are essential for real-world deployments.
