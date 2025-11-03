
# Phase 2 — Launching an EC2 Instance

## 🎯 Goal
Learn how to launch, connect to, and secure a virtual machine (EC2 instance) in AWS — introducing you to the “Compute” part of the cloud.

## 🧩 Tasks

### Step 1 — Launch an Instance
**Goal:** Create a virtual server in the cloud.  
**Actions:**  
1. Open the **AWS Management Console → EC2**.  
2. Click **Launch Instance**.  
3. Configure your instance:
   - **AMI:** `Amazon Linux 2`
   - **Instance Type:** `t2.micro` (Free Tier)
   - **Key Pair:** Create or select `mesha-keypair.pem`
   - **Network:** Default VPC  
4. Leave all other settings at their defaults and click **Launch Instance**.

---

### Step 2 — Configure Network Access
**Goal:** Ensure secure SSH access to your instance.  
**Actions:**  
1. Navigate to **EC2 → Instances → Your Instance → Security → Security Groups**.  
2. Edit inbound rules:  
   - **Type:** SSH | **Port:** 22 | **Source:** *My IP*  
3. Save rules.

---

### Step 3 — Connect to the Instance
**Goal:** Access your EC2 instance via SSH.  
**Actions:**  
1. Copy the **Public IPv4 address** of your instance.  
2. Open your terminal and run:
   ```bash
   ssh -i mesha-keypair.pem ec2-user@<public-ip>

---

### Step 4 — Optional: Install a Web Server
**Goal:** Explore hosting and network accessibility.  
**Actions:**  
1. In your SSH session, install Apache:
   ```bash
   sudo yum update -y
   sudo yum install httpd -y
   sudo systemctl start httpd
   sudo systemctl enable httpd


## 💡 Tips
- Always use the Free Tier (`t2.micro`) for practice.  
- Keep your `.pem` file private!  
- Update your security group if SSH fails.
- Always use SSH from your own IP for security.

## 📘 Reflection Questions
1. What is a key pair used for?  
2. How do security groups protect EC2 instances?  
3. What happens if you leave an instance running overnight?

## 📸 Screenshot
Add screenshots to: `../screenshots/phase2_ec2_launch.png`
