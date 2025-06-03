# ✅ AWS Hands-On Task List

A practical guide to learn and implement widely used AWS services. Follow each task to get hands-on experience with AWS infrastructure and services.

---

## 👤 IAM & Access Management

### 1. Create IAM User with Programmatic Access
- Log in to the AWS Console.
- Navigate to **IAM → Users → Add User**.
- Enable **Access key – Programmatic access**.
- Attach policy: `AmazonEC2FullAccess` or a custom policy.
- Save the **Access Key ID** and **Secret Access Key** securely.

---

## 🌐 Networking – VPC, Subnets, Peering, Security

### 2. Create Custom VPC with Public & Private Subnets
- Create VPC with CIDR: `10.0.0.0/16`.
- Create:
  - **Public Subnet**: `10.0.1.0/24`
  - **Private Subnet**: `10.0.2.0/24`
- Attach Internet Gateway to VPC.
- Update Route Table for Public Subnet to allow outbound internet access.

### 3. Create Another VPC and Configure VPC Peering
- Create another VPC with CIDR: `10.1.0.0/16`.
- Set up VPC Peering between both VPCs.
- Update route tables in both VPCs to allow inter-VPC traffic.

### 4. Create Bastion Host in Public Subnet
- Launch EC2 instance (Amazon Linux) in Public Subnet.
- Add SSH key pair.
- Configure Security Group to allow SSH (port 22) from your IP.
- SSH into Bastion → Connect to private EC2 instances using private IPs.

### 5. Understand and Configure Security Groups and NACLs
- Create separate **Security Groups** for Bastion and Private EC2.
- Create **NACLs** and configure rules to allow/deny access per subnet.

---

## 🧠 Compute – EC2, Lambda, EKS (GKE Equivalent)

### 6. Launch EC2 Instance
- Use Amazon Linux 2.
- Install Apache: `sudo yum install -y httpd`.
- Create and assign **Elastic IP** to the instance.

### 7. Create and Deploy AWS Lambda Function
- Go to **Lambda → Create Function** → Author from scratch.
- Choose runtime (e.g., Python, Node.js).
- Write a simple function to return “Hello from Lambda”.
- Create test event and run the function.

### 8. Create Amazon EKS Cluster (GKE Equivalent)
- Set up EKS using the Console or CLI.
- Ensure correct VPC/Subnets are used.
- Deploy Worker Nodes (EC2 or Fargate).
- Use `kubectl` to deploy and manage apps.

---

## 💾 Storage – S3, RDS

### 9. Create and Use S3 Bucket
- Create S3 bucket: `my-bucket-<unique-id>`.
- Upload a file.
- Enable/disable public access.
- Enable versioning, logging, and set lifecycle rules.

### 10. Create RDS MySQL Instance
- Choose **MySQL** and launch a single-AZ instance.
- Create DB subnet group and security group.
- Connect using MySQL Workbench or CLI tool.

---

## 🌐 Domain & DNS – Route 53 / Cloudflare

### 11. Register Domain and Configure DNS with Route 53
- Register or transfer a domain.
- Create a hosted zone.
- Add A/AAAA/CNAME records to route traffic to EC2 or ALB.

### 12. Use Cloudflare for Domain with SSL
- Add domain to Cloudflare.
- Update NS records at registrar to point to Cloudflare.
- Enable SSL (Flexible/Full mode).
- Configure caching, DNS, and WAF rules.

---

## 🔐 SSL Certificate

### 13. Update or Install SSL Certificate
- Use **AWS Certificate Manager (ACM)**.
- Request a public certificate.
- Validate ownership via DNS or Email.
- Attach the certificate to Application Load Balancer (ALB) or CloudFront.

---
