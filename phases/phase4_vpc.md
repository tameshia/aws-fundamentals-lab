# Phase 4 — Networking with Amazon VPC

## 🎯 Goal
Learn how to design a secure, isolated cloud network using **Amazon Virtual Private Cloud (VPC)**.  
You’ll build your own VPC with a subnet, route table, and internet gateway — then connect your EC2 instance to it.

---

## 🧩 Tasks

### Step 1 — Create a Custom VPC
**Goal:** Establish a private, logically isolated section of the AWS Cloud.  
**Actions:**  
1. In the **AWS Management Console**, navigate to **VPC**.  
2. Choose **Your VPCs → Create VPC**.  
3. Configure:
   - **Name tag:** `mesha-lab-vpc`
   - **IPv4 CIDR block:** `10.0.0.0/16`
   - **Tenancy:** Default
4. Click **Create VPC**.

💡 *You’ve created a secure virtual network with your own IP address range.*

---

### Step 2 — Create a Subnet
**Goal:** Divide your VPC into smaller networks for organizing resources.  
**Actions:**  
1. In the left menu, choose **Subnets → Create subnet**.  
2. Select your VPC: `mesha-lab-vpc`.  
3. Configure:
   - **Subnet name:** `mesha-public-subnet`
   - **Availability Zone:** (choose one, e.g. `us-east-1a`)
   - **IPv4 CIDR block:** `10.0.1.0/24`
4. Click **Create subnet**.

💡 *This subnet will host your EC2 instance and connect it to the internet.*

---

### Step 3 — Attach an Internet Gateway
**Goal:** Allow resources inside your VPC to communicate with the internet.  
**Actions:**  
1. From the left menu, go to **Internet Gateways → Create internet gateway**.  
2. Name it: `mesha-igw` and click **Create internet gateway**.  
3. Select your new gateway → **Actions → Attach to VPC → mesha-lab-vpc**.

💡 *Your VPC can now route external traffic securely through this gateway.*

---

### Step 4 — Create a Route Table
**Goal:** Define how traffic flows within your VPC.  
**Actions:**  
1. In the **VPC Dashboard**, go to **Route Tables → Create route table**.  
2. Configure:
   - **Name:** `mesha-public-rt`
   - **VPC:** `mesha-lab-vpc`
3. Click **Create route table**.  
4. Select the new route table → **Routes → Edit routes → Add route**:
   - **Destination:** `0.0.0.0/0`
   - **Target:** *mesha-igw* (the Internet Gateway you created)
5. Save changes.
6. Under **Subnet associations → Edit subnet associations**, select your `mesha-public-subnet` and save.

💡 *Now, any resource in this subnet can reach the internet using your internet gateway.*

---

### Step 5 — Create a Security Group
**Goal:** Control inbound and outbound traffic to your EC2 instance.  
**Actions:**  
1. Navigate to **EC2 → Network & Security → Security Groups → Create security group**.  
2. Configure:
   - **Name:** `mesha-vpc-sg`
   - **Description:** `Allow SSH and HTTP access`
   - **VPC:** `mesha-lab-vpc`
3. Under **Inbound rules**, add:
   - SSH (22) → *My IP*
   - HTTP (80) → `0.0.0.0/0`
4. Save rules.

💡 *Security groups act as a virtual firewall for your instances.*

---

### Step 6 — Launch an EC2 Instance into the New VPC
**Goal:** Deploy a server that lives inside your new custom network.  
**Actions:**  
1. Go to **EC2 → Launch instance**.  
2. Configure:
   - **AMI:** `Amazon Linux 2`
   - **Instance type:** `t2.micro`
   - **Key pair:** `mesha-keypair.pem`
   - **Network:** `mesha-lab-vpc`
   - **Subnet:** `mesha-public-subnet`
   - **Auto-assign Public IP:** Enable
   - **Security group:** `mesha-vpc-sg`
3. Click **Launch Instance**.
4. Once running, connect using:
   ```bash
   ssh -i mesha-keypair.pem ec2-user@<public-ip>
✅ Your EC2 instance now lives in your own virtual network — fully under your control.

### Step 7 — Verify Connectivity
**Goal:** Confirm your instance can reach the internet and web traffic flows correctly.  
**Actions:**  
1. Run inside your EC2 terminal:
     ```bash
     ping -c 3 google.com
2. If you installed Apache earlier (Phase 2), open your browser to:
  `http://<public-ip>`
You should see your web page or test page.
💡 This confirms your routes, gateway, and security group are configured correctly.

---
### Step 8 — Clean Up
**Goal:** Avoid charges and maintain a tidy environment.
**Actions:**  
1. Terminate your EC2 instance
2. Detach and delete the Internet Gateway
3. Delete your Route Table, Subnet, and finally the VPC
🧹 Always remove unused network resources when done.

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
