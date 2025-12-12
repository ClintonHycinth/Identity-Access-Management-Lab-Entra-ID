# **Azure Lab Automation Script (PowerShell)**  
This project automates the full setup of a Microsoft Azure lab environment using PowerShell in Azure Cloud Shell. It replaces a multi-step manual process with a single, reliable and repeatable script.

---

## **Features**  

### 🔐 **Identity Automation**  
- Creates Microsoft Entra ID users  
- Generates secure passwords  
- Creates a security group  
- Adds users to the group with validation checks  

### ⚙️ **Smart VM Sizing**  
- Uses your preferred VM size if available  
- Selects the closest valid size in the region  
- Optional: automatically selects the cheapest VM size  

### 🖥️ **Virtual Machine Deployment**  
- Deploys Windows Server 2025 Datacenter  
- Creates VNet, subnet, NIC and public IP  
- Supports custom admin credentials  
- Includes retry logic for transient Azure issues  

### 🛡️ **RBAC Assignment**  
- Assigns **Virtual Machine Contributor** to the group  
- Ensures proper access control at the resource group level  

### 🏗️ **Enterprise Reliability**  
- Full try and catch error handling  
- Retry logic for Azure API operations  
- Logging through PowerShell transcript  
- Idempotent behavior  
- Validation before every major step  

---

## **How to Run**  

**Basic run**
```powershell
./Deploy-Lab.ps1
Use a specific VM size

powershell
Copy code
./Deploy-Lab.ps1 -PreferredVMSize "Standard_D2s_v5"
Pick the cheapest VM size automatically

powershell
Copy code
./Deploy-Lab.ps1 -AutoPickCheapest

### **Requirements**
Azure Cloud Shell (recommended)

Az PowerShell modules

AzureAD module

Azure subscription with permissions to:

Create users

Create groups

Deploy VMs

Assign RBAC roles

### **What I Learned**
Working on this project helped me build real cloud engineering skills.

### PowerShell Automation at Scale
I learned how to structure scripts that are modular, predictable and resilient.

### Identity and Access Management
Hands-on experience with:

Entra ID object models

RBAC

Secure identity provisioning

### Designing for Reliability
I practiced:

try and catch logic

retry handling

validation before creation

building scripts that are safe to run many times

### Smart Azure Resource Selection
I learned how to:

query VM sizes

compare CPU and memory

select the closest or cheapest match

### Infrastructure as Code Mindset
This reinforced:

repeatability

consistency

documentation

version control

###🌐 Networking and VM Deployment
I gained hands-on experience with:

VNet and subnet creation

NIC and public IP setup

VM provisioning

### Writing Clean and Shareable Code
This project pushed me to:

organize folders

create a proper README

use meaningful commits

treat the script like a real engineering deliverable

### **Challenges I Faced**
⚠ Azure API Inconsistency
Some commands behave differently at different times. I handled this with:

retry logic

error handling

validation checks

🌀 Idempotency
The script needed to run multiple times safely. This required handling cases where:

users already existed

groups were already created

resources were partially deployed

📦 VM Size Selection
I had to:

query available SKUs

compare them

select the closest or cheapest

###🔗 **Resource Dependencies**
A VM depends on:

VNet

subnet

NIC

public IP

Each needed proper ordering and validation.

### **Balancing Simplicity and Reliability**
The script had to be simple enough to read but reliable enough for real use.

📝 Logging and Troubleshooting
PowerShell transcripts helped me track errors and understand script behavior during Cloud Shell sessions.

### **License**
MIT License. You can use, modify and build on this project.
