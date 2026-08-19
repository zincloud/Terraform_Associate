# Day 4: State File Management – Remote Backend

## 📚 Topics Covered
- How Terraform updates infrastructure  
- Terraform state file  
- State file best practices  
- Remote backend setup with S3  
- S3 native state locking (no DynamoDB required)  
- State management  

---

## 🎯 Key Learning Points

### 🔧 How Terraform Updates Infrastructure
- Goal: Keep actual state same as desired state  
- State file: Actual state stored in `terraform.tfstate`  
- Process: Terraform compares current state with desired configuration  
- Updates: Only modifies resources that changed  

### 📄 Terraform State File Contains
- Resource metadata  
- Resource dependencies  
- Provider information  
- Resource attribute values  

---

## 🛡️ State File Best Practices
- ❌ Never edit state file manually  
- ☁️ Store state file remotely (S3)  
- 🔒 Enable state locking  
- 💾 Backup state files  
- 🌍 Use separate state files per environment  
- 🔐 Restrict access (contains sensitive data)  
- 🔏 Encrypt state files at rest & in transit  

---

## ☁️ Remote Backend Benefits
- Collaboration  
- Locking  
- Security  
- Backup  
- Durability  

---

## 🧱 AWS Remote Backend Components
- **S3 Bucket:** Stores state  
- **S3 Native State Locking:** Conditional writes  
- **IAM Policies:** Access control  

---

## 🔒 S3 Native State Locking (Terraform 1.10+)
### How It Works
- Terraform tries to create a lock file  
- S3 conditional write checks if lock exists  
- If exists → lock fails  
- If not → lock created  
- After apply → lock file deleted (versioning delete marker)

### Old Method (DynamoDB)
- Required DynamoDB table  
- Extra IAM permissions  
- Extra cost  
- More complexity  
- Now discouraged  

---
  