# ☁️ Microsoft Azure 10-Day Practical Course for Beginners

Welcome to your **10-day journey into Microsoft Azure**! This course is designed specifically for **absolute beginners**. No prior cloud experience is required. 

By the end of these 10 days, you will have hands-on experience deploying, managing, and securing cloud resources on Azure, aligning directly with key concepts tested in the **Microsoft Azure Fundamentals (AZ-900)** certification.

---

## 🛠️ Course Prerequisites & Setup
Before starting Day 1, set up your learning environment:
1. **Azure Account:** Sign up for a [Free Azure Account](https://azure.microsoft.com/free/). You get free credits and 12 months of free popular services.
2. **Web Browser:** Edge or Chrome recommended.
3. **Command Line (Optional for later days):** Terminal (Mac/Linux) or PowerShell/Command Prompt (Windows).

---

## 📅 Day-by-Day Syllabus

- [Day 1: Introduction to Cloud & Azure Overview](#day-1-introduction-to-cloud--azure-overview)
- [Day 2: Core Azure Architectural Components](#day-2-core-azure-architectural-components)
- [Day 3: Azure Compute - Virtual Machines (VMs)](#day-3-azure-compute---virtual-machines-vms)
- [Day 4: Azure Storage Essentials](#day-4-azure-storage-essentials)
- [Day 5: Hosting Your First Static Website (Mini-Project)](#day-5-hosting-your-first-static-website-mini-project)
- [Day 6: Networking Basics - Virtual Networks (VNets)](#day-6-networking-basics---virtual-networks-vnets)
- [Day 7: Serverless Computing - Azure Functions](#day-7-serverless-computing---azure-functions)
- [Day 8: Azure Databases - Azure SQL](#day-8-azure-databases---azure-sql)
- [Day 9: Identity & Access Management - Entra ID & RBAC](#day-9-identity--access-management---entra-id--rbac)
- [Day 10: Governance, Monitoring & Cost Control](#day-10-governance-monitoring--cost-control)

---

## Day 1: Introduction to Cloud & Azure Overview

### 🎯 Objective
Understand what cloud computing is, the main deployment models, and how to navigate the Azure Portal.

### 📚 Core Concepts
- **Cloud Computing:** Delivering computing services (servers, storage, databases, networking, software) over the Internet.
- **Service Models:**
  - **IaaS (Infrastructure as a Service):** Rent servers and networks (e.g., Virtual Machines).
  - **PaaS (Platform as a Service):** Focus on code while Azure handles infrastructure (e.g., Azure App Service).
  - **SaaS (Software as a Service):** Ready-to-use apps (e.g., Microsoft 365).
- **CapEx vs. OpEx:** Shifting from upfront capital investment to pay-as-you-go operational expenses.

### 🛠️ Practical Exercise: Navigating the Azure Portal
1. Open [portal.azure.com](https://portal.azure.com/) and sign in.
2. Explore the home screen:
   - **Search Bar (Top):** Used to quickly find any service, resource, or documentation.
   - **Left Navigation Menu:** Quick access to favorite services (Virtual Machines, Storage accounts, etc.).
   - **Global Search & Notifications:** Check alerts and resource deployment progress.
3. Customization: Click on **Dashboard** and try customizing your home dashboard layout.

---

## Day 2: Core Azure Architectural Components

### 🎯 Objective
Learn how Azure organizes physical and logical resources globally.

### 📚 Core Concepts
- **Regions:** Geographical areas containing one or more datacenters (e.g., East US, West Europe).
- **Availability Zones:** Physically separate datacenters within a region for high availability.
- **Management Groups → Subscriptions → Resource Groups → Resources:** The organizational hierarchy in Azure.
- **Resource Group (RG):** A logical container for holding and managing related Azure resources together.

### 🛠️ Practical Exercise: Creating Your First Resource Group
1. In the top search bar of the Azure Portal, type **Resource groups** and select it.
2. Click **+ Create**.
3. Fill in the details:
   - **Subscription:** Select your active free subscription.
   - **Resource Group Name:** `rg-learning-dev`
   - **Region:** Select a region closest to you (e.g., `East US`).
4. Click **Review + create**, then click **Create**.

---

## Day 3: Azure Compute - Virtual Machines (VMs)

### 🎯 Objective
Provision your first Virtual Machine (IaaS) and connect to it over the web.

### 📚 Core Concepts
- **Virtual Machine (VM):** An isolated, software-based computer running Windows or Linux in the cloud.
- **NIC (Network Interface Card):** Enables a VM to communicate with internet and local devices.
- **NSG (Network Security Group):** Acts as a virtual firewall controlling inbound/outbound network traffic.

### 🛠️ Practical Exercise: Deploying a Windows or Linux VM
1. Search for **Virtual machines** in the portal and click **+ Create** > **Azure virtual machine**.
2. **Basics Tab:**
   - **Resource Group:** `rg-learning-dev`
   - **Virtual machine name:** `vm-web-01`
   - **Region:** (Same as your Resource Group)
   - **Image:** Choose `Ubuntu Server 22.04 LTS` (or `Windows Server 2022`).
   - **Size:** Choose standard free/eligible size (e.g., `Standard_B1s`).
   - **Authentication:** Select *Password* and enter a secure username and password.
3. **Inbound Port Rules:**
   - Allow selected ports: Check **SSH (22)** for Linux or **RDP (3389)** for Windows.
   - Check **HTTP (80)** to allow web traffic.
4. Click **Review + create** and then **Create**.
5. Once deployed, locate the **Public IP address** on the overview page.

---

## Day 4: Azure Storage Essentials

### 🎯 Objective
Understand Azure Storage options and learn how to store unstructured data using Blob Storage.

### 📚 Core Concepts
- **Azure Blob Storage:** Object storage for unstructured data (images, videos, documents, backups).
- **Azure Files:** Managed file shares for cloud or on-premises deployments (SMB protocol).
- **Storage Redundancy:** Options like LRS (Locally-Redundant) vs. GRS (Geo-Redundant) to protect against hardware failures.

### 🛠️ Practical Exercise: Creating a Storage Account & Container
1. Search for **Storage accounts** and click **+ Create**.
2. **Basics:**
   - **Resource Group:** `rg-learning-dev`
   - **Storage account name:** `stlearn` + *your name/numbers* (must be globally unique and lowercase, e.g., `stlearnjohn2026`).
   - **Region:** Same as before.
   - **Redundancy:** Select `Locally-redundant storage (LRS)` to minimize costs.
3. Click **Review + create**, then **Create**.
4. Once deployed, open the resource:
   - Go to **Data storage** > **Containers**.
   - Click **+ Container**, name it `documents`, set Anonymous access level to **Private**, and click **Create**.
   - Open `documents`, click **Upload**, pick a file from your computer, and upload it!

---

## Day 5: Hosting Your First Static Website (Mini-Project)

### 🎯 Objective
Combine Blob Storage concepts to deploy a publicly accessible static website for free without servers.

### 📚 Core Concepts
- **Static Website Hosting:** Serving HTML, CSS, and JS files directly from a storage container without configuring a web server.

### 🛠️ Practical Mini-Project Step-by-Step

#### Step 1: Create a local HTML file
On your local computer, open Notepad or a text editor, create a file named `index.html`, and paste:
```html
<!DOCTYPE html>
<html>
<head>
    <title>My First Azure Website</title>
    <style>
        body { font-family: Arial, sans-serif; text-align: center; margin-top: 50px; background-color: #eef2f3; }
        h1 { color: #0078d4; }
    </style>
</head>
<body>
    <h1>Hello World from Microsoft Azure!</h1>
    <p>This website is hosted directly on Azure Blob Storage.</p>
</body>
</html>
```

#### Step 2: Enable Static Website Hosting in Azure
1. Open the Storage Account you created on Day 4 (`stlearn...`).
2. On the left menu, scroll to **Settings** > **Static website**.
3. Select **Enabled**.
4. Set **Index document name** to `index.html`.
5. Click **Save**.
6. Copy the generated **Primary endpoint URL**.

#### Step 3: Upload index.html
1. In your storage account, click **Containers** on the left menu.
2. Select the automatically created container named **`$web`**.
3. Click **Upload** and upload your `index.html` file.
4. Open a new web browser tab, paste the **Primary endpoint URL** you copied earlier, and press Enter. 🎉

---

## Day 6: Networking Basics - Virtual Networks (VNets)

### 🎯 Objective
Understand cloud network isolation, IP addresses, and firewall rules.

### 📚 Core Concepts
- **Virtual Network (VNet):** A private network dedicated to your Azure resources.
- **Subnets:** Sub-sections of a VNet used to segment workloads (e.g., Web Subnet, Database Subnet).
- **Public vs. Private IP:** Public IPs are internet-accessible; Private IPs are only accessible inside the network.
- **Network Security Group (NSG):** Security rules that allow or block traffic to subnets or individual network interfaces.

### 🛠️ Practical Exercise: Creating a Custom VNet and Subnet
1. Search for **Virtual networks** and click **+ Create**.
2. **Basics:**
   - **Resource Group:** `rg-learning-dev`
   - **Name:** `vnet-main-dev`
   - **Region:** Same as RG.
3. **IP Addresses Tab:**
   - IPv4 address space: `10.0.0.0/16`
   - Click **+ Add subnet**:
     - **Subnet name:** `WebSubnet`
     - **Subnet address range:** `10.0.1.0/24`
   - Click **Add**.
4. Click **Review + create** > **Create**.

---

## Day 7: Serverless Computing - Azure Functions

### 🎯 Objective
Explore Serverless architecture (PaaS) by building an event-driven function that runs code without managing servers.

### 📚 Core Concepts
- **Serverless Computing:** Infrastructure abstraction where cloud providers automatically manage compute allocation and scaling.
- **Azure Functions:** Small pieces of code (Python, Node.js, C#, etc.) triggered by events (HTTP requests, timers, database updates).

### 🛠️ Practical Exercise: Building an HTTP-Triggered Azure Function
1. Search for **Function App** and click **+ Create**.
2. **Settings:**
   - **Resource Group:** `rg-learning-dev`
   - **Function App name:** `func-demo-` + *your name*
   - **Runtime stack:** `Node.js` or `Python`
   - **Operating System:** Linux
   - **Hosting option:** `Consumption (Serverless)`
3. Click **Review + create**, then **Create**.
4. Once created, go to the Function App resource:
   - On the left menu, select **Functions** > **Create**.
   - Choose **HTTP trigger**.
   - Set **Authorization level** to `Anonymous`.
   - Click **Create**.
5. Select **Code + Test** on the left menu, click **Test/Run**, and click **Run**.
6. View the output response below!

---

## Day 8: Azure Databases - Azure SQL

### 🎯 Objective
Provision a fully managed cloud relational database using Azure SQL.

### 📚 Core Concepts
- **Azure SQL Database:** Managed relational database service based on Microsoft SQL Server.
- **PaaS Database Benefits:** Automated backups, patching, scaling, and high availability built-in.

### 🛠️ Practical Exercise: Deploying an Azure SQL Database
1. Search for **SQL databases** and click **+ Create**.
2. **Basics:**
   - **Resource Group:** `rg-learning-dev`
   - **Database name:** `sqldb-learning`
   - **Server:** Click **Create new**:
     - Server name: `sqlserver-` + *your name*
     - Location: Same region
     - Authentication: Use **SQL Authentication** (set admin username and password).
   - **Workload environment:** Development
   - **Compute + storage:** Choose lower-cost tier (e.g., *Serverless* or *Basic* for learning).
3. Click **Review + create** > **Create**.
4. **Configure Firewall:**
   - Once deployed, open `sqldb-learning` > click **Set server firewall** at the top.
   - Click **Add your client IPv4 address**.
   - Toggle **Allow Azure services and resources to access this server** to **Yes**.
   - Click **Save**.

---

## Day 9: Identity & Access Management - Entra ID & RBAC

### 🎯 Objective
Learn how Microsoft Entra ID (formerly Azure Active Directory) secures cloud resources and user identities.

### 📚 Core Concepts
- **Microsoft Entra ID:** Azure's cloud-based identity and access management service.
- **RBAC (Role-Based Access Control):** Granting users only the specific permissions needed to perform their jobs (Principle of Least Privilege).
  - *Owner:* Full access to resources, including access assignment.
  - *Contributor:* Can create/manage resources but cannot assign roles.
  - *Reader:* Can only view existing resources.

### 🛠️ Practical Exercise: Creating a User & Assigning an RBAC Role
1. Search for **Microsoft Entra ID**.
2. On the left menu under **Manage**, select **Users** > **+ New user** > **Create new user**.
3. Set **User principal name** (e.g., `johndoe`) and **Display name** (`John Doe`). Set a temporary password and click **Create**.
4. Assign RBAC Access:
   - Go back to your Resource Group `rg-learning-dev`.
   - Select **Access control (IAM)** on the left menu.
   - Click **+ Add** > **Add role assignment**.
   - Select the **Reader** role and click **Next**.
   - Select **+ Select members**, find `John Doe`, click **Select**, then click **Review + assign**.

---

## Day 10: Governance, Monitoring & Cost Control

### 🎯 Objective
Master tools to monitor costs, enforce compliance, and clean up cloud resources.

### 📚 Core Concepts
- **Azure Policy:** Enforces rules and guardrails across resources (e.g., restricting available VM sizes or regions).
- **Azure Cost Management & Budgets:** Monitor spending and set alert thresholds.
- **Resource Locks:** Prevents accidental deletion or modification of critical resources (e.g., *CanNotDelete* or *ReadOnly*).

### 🛠️️ Practical Exercise 1: Create a Cost Budget Alert
1. Search for **Cost Management + Billing**.
2. Select **Budgets** under *Cost Management*.
3. Click **+ Add**.
4. Set a budget name (e.g., `Monthly-Learning-Budget`) and an amount (e.g., `$10`).
5. Configure an alert to notify your email if costs reach **80%** of the budget.
6. Click **Create**.

### 🛠️ Practical Exercise 2: Resource Cleanup (Crucial!)
To ensure you are not charged for resources after completing this course:
1. Search for **Resource groups**.
2. Select `rg-learning-dev`.
3. Click **Delete resource group** from the top bar.
4. Type the resource group name to confirm and click **Delete**.
   *(This cleanly deletes all VMs, storage accounts, databases, and networks created inside it in one step).*

---

## 🎓 Next Steps on Your Azure Journey
- **Official Certification Path:** Prepare for the **[AZ-900: Microsoft Azure Fundamentals](https://learn.microsoft.com/en-us/credentials/certifications/azure-fundamentals/)** exam using Microsoft Learn.
- **Hands-On Practice:** Try recreating the static website project using Azure CLI or PowerShell commands!