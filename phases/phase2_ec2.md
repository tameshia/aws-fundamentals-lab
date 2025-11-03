
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
3. *(Optional)* Add a second rule for web access:  
   - **Type:** HTTP | **Port:** 80 | **Source:** `0.0.0.0/0`  
4. Save rules.

---

### Step 3 — Connect to the Instance
**Goal:** Access your EC2 instance via SSH.  
**Actions:**  
1. Copy the **Public IPv4 address** of your instance.  
2. Open your terminal and run:
   ```bash
   ssh -i mesha-keypair.pem ec2-user@<public-ip>

3. Verify the connection:
   ```bash
   uname -a
   ```
   You should see <i>Amazon Linux 2</i> system details.
   
---

### Step 4 — Optional: Install a Web Server
**Goal:** Explore hosting and network accessibility.  
**Actions:**  
1. In your SSH session, install Apache:
   ```bash
   sudo yum update -y
   sudo yum install httpd -y
2. Start and enable the Apache service so it automatically runs on boot:
    ```bash
   sudo systemctl start httpd
   sudo systemctl enable httpd
    ```
3. Open a browser and visit `http://<public-ip>`  
   _(Example: [http://3.145.78.12](http://3.145.78.12))_

   🔍 **How to Find Your EC2 Public IP:**
      - Open the **AWS Management Console**
     - Go to **EC2 → Instances**
     - Select your running instance (**Amazon Linux 2**)
     - Check the **Public IPv4 address** in the details panel (for example: `3.145.78.12`)
       
---

4. You should see the default Apache Test Page confirming that the web server is active.
    ```bash
   (Optional) Customize your web page:
   echo "Hello from Mesha’s AWS EC2 Lab!" | sudo tee /var/www/html/index.html
    
Refresh your browser - your message should now display instead of the default page.
   ---
### Step 5 - Clean Up
**Goal:** Prevent unnecessary costs by stopping or terminating your instance when finished.
**Actions:**
1. In the AWS Console, go to EC2 → Instances.
2. Select your instance and choose Instance State → Terminate.
3. Confirm that the instance status changes to terminated.
4. Delete unused key pairs if you no longer need them.

## 💡 Tips
- Always use the Free Tier (`t2.micro`) for practice.  
- Keep your `.pem` file private!  
- If SSH fails, double-check your security group inbound rules.
- Always use SSH from your own IP for security.

## 📘 Reflection Questions
1. What is a key pair used for?  
2. How do security groups protect EC2 instances?  
3. What happens if you leave an instance running overnight?
4. How could you automate EC2 deployment in the future?

## 📸 Screenshot
Add screenshots to: `../screenshots/phase2_ec2_launch.png`

🔙 [Back to Main README](../README.md) | ⏭ [Next Phase →](phase3_s3.md)

