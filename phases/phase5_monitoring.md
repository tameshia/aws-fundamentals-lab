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

