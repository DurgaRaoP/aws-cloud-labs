# EC2 Docker Deployment — Nginx Container

## Objective

To deploy a containerized web application using Docker on an EC2 instance and make it accessible over the internet.

---

## Services & Tools Used

* Amazon EC2
* Docker
* Nginx (containerized web server)

---

## Architecture

User → EC2 (Linux) → Docker → Nginx Container

---

## Environment Setup

* Region: ap-south-2 (Hyderabad)
* Instance Type: t2.micro
* OS: Amazon Linux
* Security Group:

  * SSH (22) → My IP
  * HTTP (80) → Anywhere

---

## Steps Performed

### 1. Launch EC2 Instance

* Created EC2 instance with public IP enabled
* Configured security group for SSH and HTTP access

---

### 2. Connect to Instance

```bash
ssh -i your-key.pem ec2-user@your-public-ip
```

---

### 3. Install Docker

```bash
sudo yum install docker -y
sudo systemctl start docker
sudo systemctl enable docker
```

---

### 4. Configure User Permissions

```bash
sudo usermod -aG docker ec2-user
```

* Reconnected SSH to apply changes

---

### 5. Verify Installation

```bash
docker --version
```

---

### 6. Run Nginx Container

```bash
docker run -d -p 80:80 nginx
```

---

### 7. Verify Running Container

```bash
docker ps
```

---

### 8. Access Application

* Opened browser:

```
http://<public-ip>
```

* Confirmed Nginx welcome page

---

## Observations

* Docker pulls images from Docker Hub automatically
* Port mapping (`-p 80:80`) is required to expose container services
* Containers run in isolation from the host system
* Application becomes inaccessible if container stops

---

## Key Learnings

* Docker simplifies application deployment and dependency management
* EC2 provides the compute layer for running containers
* Port mapping connects external traffic to containerized services
* Service lifecycle can be managed using Docker commands

---

## Outcome

Successfully deployed a containerized Nginx web server on EC2 using Docker and made it accessible over the internet.

---

## Cleanup

```bash
docker stop <container_id>
docker rm <container_id>
```

* Terminated EC2 instance to avoid charges
