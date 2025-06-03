# ✅ Azure Hands-On Task List

A curated list of practical tasks to help you get hands-on experience with the most widely used Azure services for developers, DevOps engineers, and administrators.

---

## 👤 Identity & Access Management

### 1. Create Azure AD User and Assign Role
- Go to **Azure Active Directory → Users → New user**.
- Create a user and assign a role (e.g., Contributor, Reader).
- Log in with the new user to test access.

### 2. Create and Use Service Principal
- Use Azure CLI:
  ```bash
  az ad sp create-for-rbac --name myServicePrincipal --role Contributor --scopes /subscriptions/<subscription-id>
  ```

---

## 🌐 Networking – VNets, Subnets, NSG, Peering

### 3. Create Virtual Network with Subnets
- Go to **Virtual Networks → Create**.
- Add two subnets: one public, one private.
- Create NSGs (Network Security Groups) for each subnet and associate them.

### 4. VNet Peering Between Two VNets
- Create another VNet.
- Enable peering between them via **Peerings** tab.
- Update route tables if needed.

---

## 🧠 Compute – Virtual Machines, AKS, Azure Functions

### 5. Launch a Virtual Machine
- Go to **Virtual Machines → Create VM**.
- Select Ubuntu or Windows image.
- Allow ports (22, 80, 443) in NSG.
- SSH or RDP into the instance.

### 6. Create Azure Kubernetes Service (AKS)
- Go to **Kubernetes Services → Create**.
- Configure Node Pool and Networking.
- After deployment, connect using:
  ```bash
  az aks get-credentials --resource-group <rg> --name <cluster-name>
  kubectl get nodes
  ```

### 7. Create Azure Function
- Go to **Function App → Create**.
- Choose runtime (Python, Node.js, C#).
- Create HTTP trigger function.
- Test using the generated URL.

---

## 💾 Storage – Blob Storage, SQL Database

### 8. Create Storage Account and Blob Container
- Go to **Storage Accounts → Create**.
- After creation, add a **Blob Container**.
- Upload files and test access via URL or Azure CLI.

### 9. Create Azure SQL Database
- Go to **SQL Databases → Create**.
- Select Server, compute tier, and size.
- Whitelist client IP and connect using Azure Data Studio or SQL Server Management Studio.

---

## 🌍 DNS, Load Balancer, SSL

### 10. Configure Azure DNS Zone
- Go to **DNS Zones → Create**.
- Add A record pointing to your VM or Load Balancer public IP.

### 11. Create Application Gateway with SSL
- Go to **Application Gateway → Create**.
- Upload SSL certificate (PFX).
- Configure backend pool, rules, and listener for HTTPS traffic.

---

## 🔐 Identity Protection & Security

### 12. Configure Azure Key Vault
- Go to **Key Vaults → Create**.
- Add secrets, keys, or certificates.
- Assign access policies to apps or users.

### 13. Create and Assign Azure Policy
- Go to **Policy → Definitions**.
- Assign built-in or custom policy (e.g., restrict VM sizes).
- Monitor compliance status.

---

## 🔄 Automation, Monitoring & Budgets

### 14. Create Logic App to Automate Workflow
- Go to **Logic Apps → Create**.
- Choose a trigger (e.g., HTTP request, timer).
- Add actions (send email, call API, etc.).

### 15. Configure Azure Monitor and Alerts
- Go to **Monitor → Alerts → New Alert Rule**.
- Create alert on VM CPU > 70%.
- Send notification via email or webhook.

### 16. Set Budget and Cost Alerts
- Go to **Cost Management → Budgets → Add**.
- Define budget and alert thresholds.
- Review usage vs. budget trends.

---
