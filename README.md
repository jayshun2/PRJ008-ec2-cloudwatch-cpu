# Set up a Basic CloudWatch Alarm to Monitor EC2 CPU Usage  

## Project Overview  
This project sets up a **CloudWatch alarm** to track the CPU usage of an EC2 instance.  
Think of it like adding a smoke detector to your server — it alerts you when things start heating up so you can take action before problems affect users.  

## Architecture  
- **Amazon EC2** – The virtual server running an application.  
- **Amazon CloudWatch** – Collects CPU metrics and monitors performance.  
- **Amazon SNS (Simple Notification Service)** – Sends notifications (email/SMS) when the alarm is triggered.  

Together, these services create a simple monitoring system that keeps you informed of performance issues.  

## Steps to Build  
1. Launch or select an EC2 instance.  
2. Open **CloudWatch** in the AWS Console.  
3. Create a new alarm:  
   - Choose the EC2 CPUUtilization metric.  
   - Set a threshold (e.g., 80%).  
   - Define the evaluation period (e.g., 5 minutes).  
4. Configure an **SNS topic** to send notifications.  
5. Attach the SNS topic to the alarm.  
6. Test by stressing the EC2 CPU and verifying the alarm triggers.  

## What You’ll Learn  
- How to navigate **CloudWatch metrics**.  
- How to set up **basic monitoring and alerting** in AWS.  
- The importance of visibility in cloud systems — you can’t fix what you can’t see.  

## Testing  
- Run a CPU stress test on the EC2 instance (e.g., `stress` or similar tool).  
- Watch the alarm trigger and confirm you receive the SNS notification.  

## Cleanup  
To avoid extra charges:  
- Delete the CloudWatch alarm.  
- Remove the SNS topic if not needed.  
- Stop or terminate the EC2 instance (if it was only for testing).  

## Future Enhancements  
- Add monitoring for memory, disk, and network metrics.  
- Use multiple alarms to build a more complete monitoring system.  
- Automate the setup with **CloudFormation** or **Terraform**.  

---
✨ Part of the *52 AWS Projects in 52 Weeks* challenge.  


