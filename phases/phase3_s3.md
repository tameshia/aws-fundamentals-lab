
# Phase 3 — Storage with Amazon S3

## 🎯 Goal
Learn how to store, secure, and manage objects in AWS using **Simple Storage Service (S3)**. You’ll create a private, encrypted, versioned S3 bucket and explore how access control works in AWS.

## 🧩 Tasks
1. Create an S3 bucket named `mesha-fundamentals-lab`.  
2. Block all public access.  
3. Upload a text file named `hello.txt`.  
4. Enable **versioning** and **server-side encryption (SSE-S3)**.  
5. Add a bucket policy denying unencrypted (non-HTTPS) requests.  
6. Test access via AWS Console and AWS CLI.  

## 💡 Notes
- S3 stores **objects**, not files — each has metadata and versioning.  
- Versioning + encryption = strong cloud security hygiene.  
- Buckets are globally named — use unique identifiers if needed.

## 📘 Reflection Questions
1. Why should all public access be blocked by default?  
2. How does encryption at rest protect data?  
3. What’s the benefit of object versioning in S3?  

## 📸 Screenshot
Add your screenshot(s):  
`../screenshots/phase3_s3_bucket.png`
