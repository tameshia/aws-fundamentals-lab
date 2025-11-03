# Phase 5 — Monitoring & Billing

## 🎯 Goal
Learn how to monitor AWS resources, track usage, and manage costs using **CloudWatch**, **CloudTrail**, **Budgets**, and **Trusted Advisor**.

By the end of this phase, you’ll understand how to collect performance data, set alerts, and stay on top of both your cloud activity and spending.

---

## 🧩 Tasks

### Step 1 — Enable CloudTrail
**Goal:** Track every action taken in your AWS account for accountability and auditing.

**Actions:**
1. Open the **AWS Management Console** and navigate to **CloudTrail**.  
2. Click **Create trail** → Name it `mesha-cloudtrail`.  
3. Choose **Create a new S3 bucket** → e.g., `mesha-cloudtrail-logs`.  
4. Enable **Log file validation** and ensure *Management Events* are selected.  
5. Click **Create trail**.  
6. Verify that logging is active under **Trails → Status: Logging**.

💡 *CloudTrail records who did what, when, and from where — giving you a full audit trail for your AWS environment.*

---

### Step 2 — Review CloudTrail Logs
**Goal:** Understand how actions are logged and stored.

**Actions:**
1. In the AWS Console, open **S3** → locate your `mesha-cloudtrail-logs` bucket.  
2. Navigate into the folder structure (organized by date and region).  
3. Download a recent log file and open it in a text editor or viewer.  
4. Search for entries like `"eventName": "RunInstances"` or `"CreateBucket"`.  
5. Observe details such as:
   - **Event time**
   - **User identity**
   - **Source IP address**
   - **AWS service and action performed**

💡 *Every AWS API call generates a CloudTrail log — perfect for auditing or investigating unusual activity.*

---

### Step 3 — Create a CloudWatch Dashboard
**Goal:** Visualize key metrics from your AWS resources in a single, customizable view.

**Actions:**
1. Open the **AWS Management Console** and navigate to **CloudWatch**.  
2. In the left-hand menu, click **Dashboards → Create dashboard**.  
3. Enter a name for your dashboard: `mesha-lab-dashboard` and select **Create dashboard**.  
4. Choose a widget type — select **Line** and click **Next**.  
5. Under **Metrics**, expand:
   - **EC2 → Per-Instance Metrics → CPUUtilization**  
   - Select your running EC2 instance.  
6. Click **Create widget** to add it to your dashboard.  
7. (Optional) Add additional widgets to monitor:
   - **NetworkIn** (incoming traffic)
   - **NetworkOut** (outgoing traffic)
   - **StatusCheckFailed** (instance health)  
8. Click **Save dashboard** when you’re finished.

💡 *CloudWatch Dashboards provide real-time visibility into your environment, helping you spot performance issues before they become problems.*

✅ *You now have a live dashboard tracking your EC2 instance metrics.*

---

### Step 4 — Create a CloudWatch Alarm
**Goal:** Set up automated alerts for high CPU utilization so you can detect performance spikes in real time.

**Actions:**
1. Open the **AWS Management Console** and navigate to **CloudWatch**.  
2. From the left menu, select **Alarms → All alarms → Create alarm**.  
3. Choose your metric:
   - Expand **EC2 → Per-Instance Metrics → CPUUtilization**.  
   - Select your running EC2 instance and click **Select metric**.
4. Configure the alarm:
   - **Statistic:** Average  
   - **Period:** 5 minutes  
   - **Threshold type:** Static  
   - **Condition:** Trigger when **CPUUtilization > 70%** for **5 minutes**.
5. Click **Next** and choose **Actions**:
   - (Optional) Create an **SNS topic** named `mesha-alerts`.  
   - Subscribe your email address to receive notifications.  
   - Attach the topic to your alarm for instant alerts.
6. Name the alarm: `mesha-high-cpu` and click **Create alarm**.
7. (Optional) Generate CPU load on your instance to test the alarm:
   ```bash
   sudo yum install stress -y
   stress --cpu 2 --timeout 120


### Step 5 — Create a Budget Alert
**Goal:** Monitor your monthly AWS spending and receive notifications before exceeding your limit.

**Actions:**
1. Open the **AWS Management Console** and navigate to **Billing & Cost Management → Budgets**.  
2. Click **Create budget → Cost budget** and select **Next**.  
3. Configure your budget details:
   - **Budget name:** `mesha-lab-budget`
   - **Period:** Monthly  
   - **Budget amount:** `$5.00`  
   - **Budget scope:** Include all AWS services  
4. Under **Alerts**, click **Add an alert threshold**:
   - **Alert type:** Actual  
   - **Threshold:** 80% of budgeted amount  
   - **Notification type:** Email  
   - **Email recipients:** Your preferred address (e.g., `mesha@example.com`)
5. Click **Next**, review your settings, and choose **Create budget**.  
6. After a few hours of AWS usage, return to the **Budgets** dashboard to view:
   - Your **Actual cost**  
   - **Forecasted cost**  
   - **Budget threshold**  
   - **Notification status**

💡 *Budgets help you stay aware of your AWS spending and avoid unexpected charges.*

✅ *You’ve successfully created a budget that will notify you when your monthly usage exceeds 80% of your $5.00 Free Tier allowance.*

### Step 6 — Enable Trusted Advisor
**Goal:** Use AWS Trusted Advisor to identify ways to improve security, reduce costs, and enhance performance.

**Actions:**
1. Open the **AWS Management Console** and navigate to **Trusted Advisor**.  
2. On the dashboard, select **Enable AWS Trusted Advisor** (if prompted).  
3. Once enabled, review the **Trusted Advisor Summary** which highlights key areas:
   - 🧠 **Security** – Checks for MFA on root account, open ports, exposed IAM keys  
   - 💰 **Cost Optimization** – Detects idle or underutilized resources  
   - ⚙️ **Performance** – Looks for instance type efficiency and service limits  
   - 🧩 **Fault Tolerance** – Suggests backups, redundancy, and multi-AZ setups  
   - 🛡️ **Service Limits** – Warns when you’re approaching AWS resource quotas  
4. Click into each category to explore individual recommendations.  
5. (Optional) Export a report:
   - Click **Download Report → Summary (Excel)** to keep a record of current findings.  
6. Review any flagged items and take corrective actions:
   - Enable MFA for all users  
   - Close unnecessary open ports  
   - Stop or delete unused EC2 instances or volumes  
   - Adjust instance sizes for better cost/performance balance  

💡 *Trusted Advisor acts like a personal cloud consultant, continuously scanning your AWS environment for best-practice improvements.*

✅ *You’ve successfully enabled AWS Trusted Advisor and gained actionable insights into the security and efficiency of your AWS environment.*


## 💡 Notes
- CloudTrail = **Who did what**.  
- CloudWatch = **How resources are performing**.  
- Budgets = **How much you’re spending**.  
- Monitoring and alerts are essential parts of cloud security and cost control.

## 📘 Reflection Questions
1. What are the differences between CloudWatch and CloudTrail?  
2. Why is budgeting important when using the Free Tier?  
3. How does monitoring contribute to proactive security?  

## 📸 Screenshot
Add your screenshots here:  
`../screenshots/phase5_cloudwatch_dashboard.png`

🔙 [Back to Main README](../README.md) 
