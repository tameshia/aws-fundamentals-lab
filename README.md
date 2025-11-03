<h1 align="center">☁️ AWS Fundamentals Lab</h1>
<h3 align="center">Hands-on Cloud Labs for Security+ and AWS Learners</h3>

<p align="center">
A guided series of beginner-friendly AWS labs designed to strengthen your understanding of <strong>cloud architecture</strong>, <strong>network security</strong>, and <strong>automation</strong> — all built within the AWS Free Tier.
</p>

---

<h3 align="center">📘 Table of Contents</h3>

<p align="center">
  <a href="#-phase-1--identity-and-access-management-iam">Phase 1 — IAM</a> •
  <a href="#-phase-2--compute-ec2">Phase 2 — EC2</a> •
  <a href="#-phase-3--storage-s3">Phase 3 — S3</a> •
  <a href="#-phase-4--networking-vpc">Phase 4 — VPC</a> •
  <a href="#-phase-5--monitoring--billing">Phase 5 — Monitoring & Billing</a>
</p>

---

## 🔐 Phase 1 — Identity and Access Management (IAM)
**Goal:** Learn how to securely manage users, groups, and permissions with AWS IAM.  
You’ll implement MFA, create least-privilege users, and understand shared responsibility.

🔗 [View Phase 1 Guide →](phases/phase1_iam.md)

---

## 💻 Phase 2 — Compute (EC2)
**Goal:** Launch and connect to your first virtual server in the cloud.  
You’ll configure SSH access, security groups, and optional web hosting for hands-on practice.

🔗 [View Phase 2 Guide →](phases/phase2_ec2.md)

---

## 💾 Phase 3 — Storage (S3)
**Goal:** Explore AWS object storage by creating an encrypted, versioned S3 bucket.  
You’ll upload, manage, and protect files using bucket policies and server-side encryption.

🔗 [View Phase 3 Guide →](phases/phase3_s3.md)

---

## 🌐 Phase 4 — Networking (VPC)
**Goal:** Understand how AWS isolates and routes traffic using Virtual Private Clouds.  
You’ll create and modify security groups, explore route tables, and design a basic network.

🔗 [View Phase 4 Guide →](phases/phase4_vpc.md)

---

## 📈 Phase 5 — Monitoring & Billing
**Goal:** Learn how to track, log, and control your AWS environment using CloudWatch, CloudTrail, and Budgets.  
You’ll create dashboards, alarms, and cost alerts to ensure visibility and accountability.

🔗 [View Phase 5 Guide →](phases/phase5_monitoring.md)

---

<h3 align="center">🧩 Deliverables</h3>

<p align="center">
✅ 1 IAM user (MFA-enabled)  
✅ 1 EC2 instance (secured via SSH)  
✅ 1 S3 bucket (encrypted and versioned)  
✅ 1 VPC with configured Security Group  
✅ 1 CloudWatch dashboard, alarm, and budget alert  
</p>

---

<h3 align="center">📊 Skills Strengthened</h3>

<p align="center">
☁️ Cloud Architecture • 🔐 Identity & Access Management • 💾 Data Protection  
🌐 Network Security • 📈 Monitoring & Cost Optimization • ⚙️ Automation Foundations
</p>

---

<h3 align="center">📸 Screenshots</h3>

<p align="center">
<a href="screenshots/phase1_iam_setup.png">IAM Setup</a> •
<a href="screenshots/phase2_ec2_launch.png">EC2 Launch</a> •
<a href="screenshots/phase3_s3_bucket.png">S3 Bucket</a> •
<a href="screenshots/phase4_vpc_dashboard.png">VPC Dashboard</a> •
<a href="screenshots/phase5_cloudwatch_dashboard.png">CloudWatch Metrics</a>
</p>

---

<h3 align="center">🪞 Reflections</h3>

<p align="center">
<a href="Reflections.md">View My Learning Journal →</a>
</p>

---

<p align="center">✨ “Start small, think big — every cloud builds upward.” ✨</p>

<p align="center">
  <img src="https://img.shields.io/badge/AWS-Cloud_Fundamentals-FF9900?style=for-the-badge&logo=amazonaws&logoColor=white" alt="AWS Badge"/>
  <img src="https://img.shields.io/badge/Security+-SY0--701-181717?style=for-the-badge&logo=compTIA&logoColor=white" alt="Security+ Badge"/>
  <img src="https://img.shields.io/badge/Status-In_Progress-006400?style=for-the-badge" alt="Status Badge"/>
</p>


----
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

   ---

## 💾 Phase 3 — Storage with Amazon S3
**Goal:** Learn to store, secure, and manage objects using **S3**.

### 🪜 Tasks
1. Open **S3 → Create bucket** → Name: `mesha-fundamentals-lab`.  
2. Keep “Block all public access” ✅ enabled.  
3. Upload a file named `hello.txt` with the message “Hello from Mesha’s AWS Lab!”.  
4. Enable **Versioning** → re-upload a new version to test.  
5. Turn on **Default encryption** (SSE-S3).  
6. Add a bucket policy that denies non-HTTPS requests (optional).  
7. Test with:
   ```bash
   aws s3 ls s3://mesha-fundamentals-lab

