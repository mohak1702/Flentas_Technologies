# High Availability Architecture on AWS using ALB + Auto Scaling Group

## 📌 Project Overview
This project demonstrates how to deploy a **highly available, scalable, and secure web application** on AWS using:

- Application Load Balancer (ALB)
- EC2 Instances in Private Subnets
- Auto Scaling Group (ASG)
- Multi-AZ Deployment
- VPC with public and private subnets

The goal is to ensure:
- High availability
- Automatic scaling during traffic peaks
- Secure architecture (no public EC2 instances)
- Proper routing from Internet → ALB → Private EC2

---

## 🏗️ **Architecture Diagram**
Internet → Public Subnets → ALB → Private Subnets → EC2 (ASG)

---

## 🚀 **Components Created**
### 1. **VPC**
- Custom VPC  
- 2 Public subnets  
- 2 Private subnets  
- Routing tables configured  
- NAT Gateway or Internet Gateway (depending on design)

### 2. **Application Load Balancer (ALB)**
- Internet-facing  
- Two public subnets  
- Listener on port 80  
- Security group allows HTTP (80) from Anywhere  

### 3. **Target Group**
- Target type: Instances  
- Health checks on `/`  
- Registered EC2 instances launched by the ASG  

### 4. **Launch Template**
- AMI  
- Instance type  
- User-data script for web server  
- Instance security group (allows HTTP only from ALB SG)

### 5. **Auto Scaling Group**
- Minimum: 1  
- Desired: 2  
- Maximum: 3  
- Spread across **2 Availability Zones**  
- Attached to ALB Target Group  

---

## ⚙️ **How to Deploy**
### 1. Clone the Repository
```bash
git clone https://github.com/<your-username>/<your-repo-name>.git
cd <your-repo-name>
