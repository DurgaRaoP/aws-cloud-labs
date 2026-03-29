# CloudWatch Monitoring Setup

## What was built
- CloudWatch alarm on EC2 CPUUtilization > 70%
- SNS topic with email subscription
- Alarm triggers SNS notification

## Steps
1. EC2 → CloudWatch → Create Alarm
2. Metric: AWS/EC2 → CPUUtilization
3. Threshold: Greater than 70 for 1 period (300s)
4. Action: Send to SNS topic → email

## Key concepts
- Default EC2 metrics: CPU, Network, Disk (not memory)
- Memory requires CloudWatch Agent
- Alarm states: OK, ALARM, INSUFFICIENT_DATA
