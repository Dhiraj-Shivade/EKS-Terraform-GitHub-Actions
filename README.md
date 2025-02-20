# Terraform Infrastructure Provisioning

## 📌 Project Overview
This project automates the provisioning of an **AWS EKS cluster** using **Terraform** and **Jenkins**/**Gihub Actions**, enabling Infrastructure as Code (IaC) for streamlined and scalable deployments. The Jenkins pipeline automates the execution of Terraform commands, ensuring efficient infrastructure management.

---

## 📂 Project Structure
```
├── assets
│   ├── Null
│   ├── Presentation1.gif
│
├── eks
│   ├── .terraform.lock.hcl
│   ├── backend.tf
│   ├── dev.tfvars
│   ├── main.tf
│   ├── variables.tf
│
├── module
│   ├── data.tf
│   ├── eks.tf
│   ├── iam.tf
│   ├── variables.tf
│   ├── vpc.tf
│
└── Jenkinsfile  (CI/CD Pipeline Configuration)
```

---

## 🛠️ Tools & Technologies Used
- **Terraform** - Infrastructure as Code (IaC) to provision AWS resources.
- **Jenkins** - Automating Terraform workflow using a CI/CD pipeline.
- **AWS EKS** - Kubernetes cluster management on AWS.
- **AWS IAM** - Identity and Access Management for security.
- **AWS CLI** - Command-line interface to interact with AWS services.
- **Git** - Version control system for managing infrastructure code.
- **Jenkins Pipeline** - Automates Terraform execution based on user input.
- **S3 & DynamoDB** - Backend storage for Terraform state management.

---

## 🚀 Jenkins Pipeline Workflow
This Jenkins pipeline provides an automated approach to manage AWS infrastructure using Terraform. It supports:
1. **`plan`** - Generates and displays execution plans without applying changes.
2. **`apply`** - Deploys the infrastructure automatically.
3. **`destroy`** - Tears down the infrastructure when no longer needed.

### 📜 Jenkinsfile Workflow
1. **Preparing Stage**: Prints an initial message for debugging.
2. **Git Checkout**: Clones the repository to fetch the latest Terraform code.
3. **Terraform Init**: Initializes Terraform with AWS credentials.
4. **Terraform Validate**: Checks syntax correctness and resource configurations.
5. **Action Stage**: Executes `plan`, `apply`, or `destroy` based on user input.

---

## 🛠️ Setting Up Jenkins for Terraform Automation
### 1️⃣ **Install Required Plugins**
Ensure that the following Jenkins plugins are installed:
- **Pipeline**
- **Git Plugin**
- **AWS Credentials Plugin**
- **Terraform Plugin**

### 2️⃣ **Configure AWS Credentials in Jenkins**
- Navigate to **Manage Jenkins → Manage Credentials**.
- Add AWS access key and secret key as **global credentials** with ID `aws-creds`.

### 3️⃣ **Set Up a Jenkins Job**
1. Go to **Jenkins Dashboard** → Click on **New Item**.
2. Select **Pipeline**, name it (e.g., `Terraform-EKS-Deployment`), and click **OK**.
3. In the **Pipeline** section, choose **Pipeline script from SCM**.
4. Add your **Git repository URL**.
5. Set the **Branch** as `master`.
6. Under **Script Path**, specify `Jenkinsfile`.
7. Click **Save & Build**.

---

## ⚙️ Running the Pipeline
After configuring the Jenkins job:
1. Click **Build with Parameters**.
2. Choose `Environment` (`dev` by default).
3. Select `Terraform_Action`: `plan`, `apply`, or `destroy`.
4. Click **Build** and monitor logs for progress.

---

## 🔍 Terraform Configuration Breakdown
### **eks/main.tf**
Defines AWS resources such as **VPC, EKS cluster, IAM roles, and security groups**.

### **eks/variables.tf**
Stores input parameters such as **AWS region, cluster name, and node group configurations**.

### **eks/backend.tf**
Configures Terraform backend using **S3 for remote state storage** and **DynamoDB for state locking**.

### **module/**
Contains reusable Terraform modules for **VPC, IAM, and EKS**.

---

## ✅ Best Practices Implemented
✔ **Modular Terraform Code** - Follows best practices for scalability and maintainability.
✔ **State Management** - Uses **S3 and DynamoDB** to ensure safe and persistent state handling.
✔ **Jenkins Automation** - Eliminates manual Terraform execution, ensuring reliability.
✔ **AWS IAM Security** - Follows **least privilege principle** for IAM roles and policies.
✔ **Parameterization** - Uses **environment-specific variables** for flexibility.

---

## 🎯 Future Enhancements
🔹 Implement **ArgoCD** for GitOps-based deployments.
🔹 Integrate **Prometheus & Grafana** for monitoring EKS resources.
🔹 Automate Jenkins setup using Terraform and Ansible.

---

