# Phase 4 — Networking with Amazon VPC

## 🎯 Goal
Understand how AWS networks are structured using **Virtual Private Clouds (VPCs)** — and how subnets, route tables, and security groups control traffic within your cloud environment.

## 🧩 Tasks
1. Explore the default VPC and identify subnets, route tables, and gateways.  
2. Create a new Security Group `mesha-web-sg` allowing HTTP (80) and SSH (22).  
3. Attach it to your EC2 instance from Phase 2.  
4. Test connectivity using your EC2 public IP in a browser.  
5. (Optional) Create a custom VPC with subnets and an Internet Gateway.

## 💡 Notes
- VPCs isolate your AWS resources into secure, private networks.  
- Security Groups act like firewalls controlling inbound/outbound access.  
- Limiting SSH to “My IP” prevents unauthorized logins.  

## 📘 Reflection Questions
1. What is the purpose of an Internet Gateway?  
2. Why is a Security Group rule allowing 0.0.0.0/0 risky?  
3. How does the Route Table affect instance connectivity?  

## 📸 Screenshot
Add screenshots here:  
`../screenshots/phase4_vpc_dashboard.png`

