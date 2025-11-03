# Phase 5 — Monitoring & Billing

## 🎯 Goal
Learn how to monitor, log, and manage costs in your AWS environment using **CloudWatch**, **CloudTrail**, and **AWS Budgets**.  
You’ll track activity, visualize metrics, and set up cost alerts to help you stay proactive with your cloud usage.

---

## 🧩 Tasks

### Step 1 — Enable CloudTrail
**Goal:** Record all AWS account activity for security and auditing.  
**Actions:**  
1. In the **AWS Management Console**, search for **CloudTrail**.  
2. Click **Create trail** → configure:
   - **Trail name:** `mesha-cloudtrail`
   - **Storage location:** Create a new S3 bucket → `mesha-cloudtrail-logs`
   - **Log file validation:** Enable  
   - **Event type:** Management events only (default)
3. Click **Create trail**.  
4. Verify the trail appears under **Trails** → `mesha-cloudtrail`.

💡 *CloudTrail logs every API call — who did what, when, and from where.*

---

### Step 2 — Review CloudTrail Logs
**Goal:** Explore activity records stored in your S3 bucket.  
**Actions:**  
1. Go to **S3 → mesha-cloudtrail-logs**.  
2. Open the latest log folder and click a `.json.gz` file.  
3. Download and open it — you’ll see entries like this:
   ```json
   {
     "eventName": "RunInstances",
     "userIdentity": {"userName": "mesha-admin"},
     "sourceIPAddress": "98.xx.xx.xx"
   }
💡 These logs are your security timeline — every AWS action leaves a footprint.

---

Step 3 — Create a CloudWatch Dashboard

Goal: Visualize resource performance and trends.
Actions:

Go to CloudWatch → Dashboards → Create dashboard.

Name it: mesha-lab-dashboard.

Add a widget → Line graph → Metric → EC2 → Per-Instance Metrics → CPUUtilization.

Select your EC2 instance → click Create widget.

Add another widget (optional):

NetworkIn or StatusCheckFailed for health monitoring.

💡 Dashboards make it easy to spot trends and issues across your cloud environment.

Step 4 — Create a CloudWatch Alarm

Goal: Set up automated alerts for high CPU usage.
Actions:

Go to CloudWatch → Alarms → Create alarm.

Choose metric: EC2 → CPUUtilization.

Set conditions:

Threshold type: Static

Whenever CPUUtilization is > 70% for 5 minutes

Name the alarm: mesha-high-cpu.

(Optional) Add an email notification by creating an SNS topic.

💡 Alarms notify you when something unusual happens, so you can respond fast.

Step 5 — Create a Budget Alert

Goal: Track and control your spending with AWS Budgets.
Actions:

Go to Billing → Budgets → Create budget.

Choose Cost budget and click Next.

Configure:

Budget name: mesha-lab-budget

Period: Monthly

Budget amount: $5.00

Under Alerts, add your email address to get notifications.

Review and click Create budget.

After a few hours, check for data under Budgets.

💡 Budgets help you learn cloud cost management — a key certification skill.

Step 6 — (Optional) Enable Trusted Advisor

Goal: Get recommendations for improving security and reducing costs.
Actions:

Open Trusted Advisor → Dashboard.

Review checks under:

🧠 Security (e.g., open ports, MFA not enabled)

💰 Cost Optimization (e.g., idle instances)

Note one area you could improve in your setup.

💡 Trusted Advisor gives real-time best-practice insights for your account.

Step 7 — Verify Everything Works

Goal: Confirm monitoring and alerts are functioning.
Actions:

View your CloudWatch dashboard — check for CPU metrics.

Open your CloudTrail S3 logs — confirm new activity entries.

Verify your Budget alert email arrives when costs increase.

✅ Your environment is now fully observable — performance, security, and cost visibility all in one place.

Step 8 — Clean Up

Goal: Keep your account organized and cost-free.
Actions:

Delete the CloudWatch dashboard and alarm.

Delete your CloudTrail trail and associated S3 bucket.

Delete the budget if no longer needed.

🧹 Keep a clean AWS account to avoid confusion or unexpected charges.
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

