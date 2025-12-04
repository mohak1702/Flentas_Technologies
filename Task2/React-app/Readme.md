# Static Resume Website Deployment on AWS EC2

## Overview
Visit http://40.192.119.95/ to check static resume
Check the Report_Task2.pdf for more description
This project demonstrates hosting a personal resume as a static website on an AWS EC2 instance using Nginx. The website includes `index.html`, `style.css`, and a profile image.

## Steps to Deploy

### 1. Launch EC2 Instance
- Launch a Free Tier EC2 instance (Amazon Linux 2023) in a public subnet.
- Create a key pair (`my-ec2-key.pem`) for SSH access.
- Configure Security Group:
  - Allow **SSH (22)** from your IP
  - Allow **HTTP (80)** from all
  - Allow **HTTPS (443)** from all

### 2. Install Nginx
SSH into the instance:

```bash
ssh -i "my-ec2-key.pem" ec2-user@<EC2_PUBLIC_IP>
