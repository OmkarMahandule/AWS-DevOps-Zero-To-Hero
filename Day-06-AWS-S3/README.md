# Day 6 – Amazon S3

## Topic
**Amazon S3 (Simple Storage Service)** – Object storage, versioning, lifecycle policies, security, and access control.

---

## Objective
To understand how Amazon S3 works by performing end-to-end hands-on practice, covering real-world use cases like storage management, security, and cost optimization.

---

## Key Concepts Learned
- Bucket vs Object
- Global uniqueness of bucket names
- Object-based storage (not file/block storage)
- Bucket versioning & delete markers
- Storage classes (Standard, IA, Glacier)
- Lifecycle policies
- Access control (Bucket policy vs ACL)
- Encryption at rest & in transit
- IAM integration with S3

---

## Hands-On Tasks Performed

### 1️ S3 Bucket Creation
- Bucket Name: `omkar-s3-day6-bucket`
- Region: Same as EC2
- Public Access: **Blocked**
- Encryption: **Enabled (SSE-S3)**

  <img width="850" height="600" alt="image" src="https://github.com/user-attachments/assets/1468f161-83d2-4c7c-9b15-fa91938503fe" />

---

### 2️⃣ Object Upload
- Uploaded `.txt`, `.pdf`, and image files
- Explored object metadata and object keys

  <img width="1912" height="968" alt="image" src="https://github.com/user-attachments/assets/24c8577c-513e-443a-8fc0-20bbe7b335bd" />


---

### 3️⃣ Folder Structure (Logical)
- Created logical folders using prefixes: logs/
- Learned that S3 does **not** have real directories

---

### 4️⃣ Enabled Versioning
- Enabled bucket versioning
- Uploaded the same file multiple times
- Verified multiple versions of the same 

<img width="1912" height="968" alt="image" src="https://github.com/user-attachments/assets/142182d6-cc90-4293-b88e-9a9fbae536ea" />


---

### 5️⃣ Delete & Recovery Test
- Deleted an object
- Observed delete marker behavior
- Restored object by removing delete marker

  <img width="1912" height="968" alt="image" src="https://github.com/user-attachments/assets/39f461ce-3137-401e-922d-f6f70ffd91f8" />

  <img width="1912" height="968" alt="image" src="https://github.com/user-attachments/assets/09c89532-6203-402e-8ceb-5a2ca165deea" />

---

### 6️⃣ Storage Classes
- Changed object storage class to:
- `Standard-IA` (Standard – Infrequent Access)
- Understood cost-based storage optimization

  <img width="1912" height="968" alt="image" src="https://github.com/user-attachments/assets/02008eb5-1574-4030-8e8b-cf39978e82c3" />


---

### 7️⃣ Lifecycle Policy
Configured lifecycle rule:
- Transition objects to **Glacier after 30 days**
- Permanently delete objects after **365 days**

Purpose: **Automated cost optimization**

<img width="1912" height="968" alt="image" src="https://github.com/user-attachments/assets/5c8517a9-1cc4-4ad3-8551-9b73a64bc64e" />
<img width="1912" height="968" alt="image" src="https://github.com/user-attachments/assets/11df3f7b-371c-4c89-babf-9b549ae05eb7" />



---

### 8️⃣ Access Control & Security
- Verified:
- Block public access enabled
- No public bucket policy
- ACL set to private
- Practiced object-level public access safely

---

### 9️⃣ Encryption
- Encryption at rest: **SSE-S3**
- Encryption in transit: **HTTPS (default)**

---

### 🔐 10️⃣ IAM Integration
- Created IAM policy with limited permissions:
- `s3:GetObject`
- `s3:ListBucket`
- Applied **Principle of Least Privilege**

  <img width="1912" height="968" alt="image" src="https://github.com/user-attachments/assets/dfd39dfc-ce4a-4894-acfa-45fd32492006" />


---

### 🧹 11️⃣ Cleanup
- Deleted all objects and versions
- Deleted bucket to avoid unnecessary charges

  <img width="1912" height="968" alt="image" src="https://github.com/user-attachments/assets/d593fb8b-3094-4dfa-8836-e415b52dbc62" />


---

## Real-World Learnings
- Never make S3 buckets public unintentionally
- Versioning increases safety but also storage cost
- Lifecycle rules are essential for cost control
- S3 is heavily used in CI/CD, backups, logs, and static websites

---

## Summary
Day 6 provided a solid understanding of **secure, scalable, and cost-optimized object storage** using Amazon S3 — a core service in real-world DevOps workflows.

---

📅 **Next:** AWS CLI with S3 / Static Website Hosting / Event Notifications

  
