<h1 align="center">☁️ AWS Fundamentals Lab</h1>
<h3 align="center">Hands-On Practice for Cloud Practitioner & Security+ Learners</h3>

<p align="center">
A guided, free-tier friendly lab designed to strengthen your understanding of AWS cloud services and core concepts through real-world practice.
</p>

---

## 🧭 Overview

This lab helps you explore the foundational elements of **AWS Cloud Fundamentals**, perfect for those studying for:
- **AWS Cloud Practitioner Certification**
- **CompTIA Security+ (SY0-701)**
- **Cloud security and infrastructure fundamentals**

You’ll build and manage basic cloud resources to understand **compute, storage, networking, and IAM** — the essential pillars of AWS.

---

## ☁️ Lab Objectives

By completing this lab, you will:
- Understand how to create and secure AWS resources  
- Launch and connect to an EC2 instance  
- Configure IAM users and roles  
- Set up an S3 bucket for data storage  
- Explore VPC networking and security groups  
- Monitor with CloudWatch  
- Review billing and cost management best practices  

---

## 🧱 Phase 1 — Identity and Access Management (IAM)
**Goal:** Learn how to securely manage users, roles, and permissions.

**Tasks**
1. Log in as your AWS root account **only once** to set up IAM.
2. Create an **Admin user** named `mesha-admin` with:
   - MFA enabled  
   - `AdministratorAccess` policy  
3. Create an **IAM Group** (`Admins`) and attach your user.
4. Enable a strong **password policy** for all users.
5. Sign out and only use your IAM user going forward.

💡 *You’ve implemented the first step in AWS’s Shared Responsibility Model — protecting access!*

---

## 💻 Phase 2 — Launching an EC2 Instance
**Goal:** Understand AWS compute basics and remote access.

**Tasks**
1. Open **EC2** → “Launch Instance.”  
2. Choose:
   - AMI: `Amazon Linux 2`  
   - Instance Type: `t2.micro` (Free Tier)  
   - Key Pair: `mesha-keypair.pem`  
   - Network: Default VPC  
3. Launch and connect:
   ```bash
   ssh -i mesha-keypair.pem ec2-user@<public-ip>
