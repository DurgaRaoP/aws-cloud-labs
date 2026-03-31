# AWS CloudWatch Alarm Lab

## 📌 Objective

To monitor EC2 CPU utilization using Amazon CloudWatch and trigger an alarm when CPU usage exceeds a defined threshold.

---

## 🧰 Services Used

* Amazon EC2
* Amazon CloudWatch

---

## 🖥️ Environment Setup

* Instance Type: t2.micro
* OS: Amazon Linux
* Monitoring: Basic (default)

---

## ⚙️ Steps Performed

### 1. Launch EC2 Instance

* Created EC2 instance using Amazon Linux
* Configured security group:

  * SSH (Port 22) → My IP
  * HTTP (Port 80) → Anywhere

---

### 2. Install Stress Tool

```bash
sudo yum install stress -y
```

---

### 3. Create CloudWatch Alarm

* Metric: CPUUtilization
* Threshold: > 50%
* Period: 1 minute
* Evaluation Periods: 1
* Statistic: Average

---

### 4. Generate CPU Load

```bash
stress --cpu 1 --timeout 300
```

* Used 1 CPU to match t2.micro (1 vCPU)
* Duration: 5 minutes to ensure CloudWatch captures metrics

---

### 5. Monitor System (Linux)

```bash
top
```

* Observed `stress` process consuming ~100% CPU
* Verified real-time system load

---

### 6. Background Process Handling

* Sent process to background:

```bash
CTRL + Z
bg
```

* Allowed simultaneous monitoring and control

---

### 7. Stop Stress Process

```bash
pkill stress
```

---

## 📊 Observations

* CPU utilization reached ~100% during stress test
* CloudWatch alarm triggered after threshold breach
* Alarm response delayed due to metric collection intervals
* After stopping stress, CPU gradually returned to normal

---

## 🧠 Key Learnings

* t2.micro has only 1 vCPU → multiple workers do not increase CPU capacity
* CloudWatch metrics are not real-time (delay due to collection and evaluation)
* Alarm configuration (period & evaluation) directly affects triggering
* Foreground vs background processes impact terminal usability
* `top` helps identify high CPU-consuming processes

---

## ⚠️ Challenges Faced

* Initial confusion with `ps aux | grep stress` showing grep process
* Alarm not triggering due to short stress duration
* Terminal blocked due to foreground process execution

---

## 🚀 Outcome

Successfully implemented monitoring and alerting for EC2 CPU utilization using CloudWatch and validated behavior through load testing.

---

## 📎 Commands Summary

```bash
# Install stress
sudo yum install stress -y

# Generate load
stress --cpu 1 --timeout 300

# Check processes
top

# Kill process
pkill stress
```

---


