
# Phase 3 — Storage with Amazon S3

## 🎯 Goal
Learn how to create, secure, and manage object storage in AWS using **Amazon S3**.  
You’ll explore versioning, encryption, and access management — foundational skills for secure cloud storage.

---

## 🧩 Tasks

### Step 1 — Create an S3 Bucket
**Goal:** Establish a secure, private location for object storage.  
**Actions:**  
1. In the **AWS Management Console**, navigate to **S3**.  
2. Click **Create bucket**.  
3. Configure your bucket:
   - **Bucket name:** `mesha-fundamentals-lab`
   - **Region:** Select the region nearest to you (e.g., `us-east-1`)
4. Under **Block Public Access settings**, leave **“Block all public access”** ✅ enabled.  
5. Scroll to the bottom and click **Create bucket**.

💡 *You’ve now created a secure, private S3 bucket for your cloud-based storage.*

---

### Step 2 — Upload a File
**Goal:** Store and organize an object inside your new bucket.  
**Actions:**  
1. Open your newly created bucket.  
2. Click **Upload** → **Add files**.  
3. Choose a file from your computer (for example, `hello.txt`).  
4. Under **Permissions**, keep it private.  
5. Click **Upload**.

✅ *You’ve successfully stored your first object in S3!*

---

### Step 3 — Enable Versioning
**Goal:** Maintain multiple versions of your files to protect against accidental deletion or overwriting.  
**Actions:**  
1. Open your bucket.  
2. Select the **Properties** tab.  
3. Scroll down to **Bucket versioning** → click **Edit**.  
4. Turn on **Versioning** and click **Save changes**.  
5. Re-upload your `hello.txt` file with a small change to test versioning.

💡 *S3 versioning lets you recover previous versions if a file is deleted or modified.*

---

### Step 4 — Enable Default Encryption
**Goal:** Protect data at rest with server-side encryption.  
**Actions:**  
1. Go to your bucket’s **Properties** tab.  
2. Scroll to **Default encryption** → click **Edit**.  
3. Choose **Enable** → Select **Amazon S3 managed keys (SSE-S3)**.  
4. Click **Save changes**.

🔒 *All future uploads are now automatically encrypted by AWS.*

---

### Step 5 — Add a Security Policy (Optional)
**Goal:** Restrict unsecure access attempts.  
**Actions:**  
1. Open your bucket → **Permissions** tab.  
2. Under **Bucket policy**, click **Edit policy** and paste this sample JSON:

   ```json
   {
     "Version": "2012-10-17",
     "Statement": [
       {
         "Sid": "EnforceSSLRequestsOnly",
         "Effect": "Deny",
         "Principal": "*",
         "Action": "s3:*",
         "Resource": [
           "arn:aws:s3:::mesha-fundamentals-lab",
           "arn:aws:s3:::mesha-fundamentals-lab/*"
         ],
         "Condition": {
           "Bool": {
             "aws:SecureTransport": "false"
           }
         }
       }
     ]
   }

### Step 6 — Verify Storage Properties
**Goal:** Review your bucket's security posture.  
**Actions:**  
   - Confirm Block Public Access = Enabled
   - Confirm Versioning = Enabled
   - Confirm Default encryption = Enabled
   - Confirm Policy status = Active

✅ Your S3 bucket now follows best-practice security standards.

## 💡 Notes
- S3 stores **objects**, not files — each has metadata and versioning.  
- Versioning + encryption = strong cloud security hygiene.  
- Use clear, unique bucket names (they’re global).
- Never disable “Block All Public Access” unless you need to host public assets.

## 📘 Reflection Questions
1. Why should all public access be blocked by default?
2. When might you enable public access intentionally?
3. How does encryption at rest protect data?  
4. What’s the benefit of object versioning in S3?  

## 📸 Screenshot
Add your screenshot(s):  
`../screenshots/phase3_s3_bucket.png`

🔙 [Back to Main README](../README.md) | ⏭ [Next Phase →](phase4_vpc.md)
