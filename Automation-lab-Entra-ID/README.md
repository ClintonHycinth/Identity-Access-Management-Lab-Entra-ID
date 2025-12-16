# Microsoft Entra ID Identity & RBAC Automation Lab (PowerShell)

This repository contains the **automated version** of an Entra ID and Azure RBAC lab built with PowerShell.  
The same lab was first completed manually using the Azure Portal, and this script recreates the entire setup in a repeatable, one-click way.

The goal is to practice **identity management, role-based access control, and VM deployment**, exactly as expected in real Azure admin work and the AZ-104 exam.

---

## What This Lab Automates

The script performs the following actions from start to finish:

### Entra ID (Azure AD)
- Creates two users:
  - Engineer1  
  - Engineer2
- Creates a security group:
  - **lab engineers**
- Adds both users to the group

### Azure Resources
- Creates or reuses a resource group: **rg-104**
- Deploys networking:
  - Virtual Network
  - Subnet
  - Public IP
  - Network Interface
- Creates a **Windows Server 2025 Datacenter VM** with:
  - Size: `Standard_D2ads_v6`
  - Region: West Europe
  - Availability Zone: 1
  - Spot VM enabled
  - Eviction policy: Deallocate

### RBAC
- Assigns **Virtual Machine Contributor** role
- Scope: Resource Group (`rg-104`)
- Role is assigned to the **lab engineers** group, not individual users

This mirrors real-world best practice where access is granted to groups, not people.

---

## Why This Lab Matters

This lab covers multiple core Azure admin skills in one setup:

- Entra ID user and group management
- Group-based RBAC
- Understanding role scope and permissions
- VM deployment with availability zones
- Cost optimization using Spot VMs
- Translating portal actions into automation

---

## Prerequisites

Before running the script, make sure you have:

- An active Azure subscription
- Azure PowerShell modules installed:
  - `Az`
  - `AzureAD`
- Logged in to Azure:
  ```powershell
  Connect-AzAccount
  Connect-AzureAD

## How to Run
Basic run:
powershell^
./Deploy-Lab.ps1

Automatically pick the cheapest VM size
powershell^
./Deploy-Lab.ps1 -AutoPickCheapest

## Requirements
Azure Cloud Shell (recommended)

Az PowerShell modules

AzureAD module

Azure subscription with permissions to:

Create users

Create groups

Deploy VMs

Assign RBAC roles

## What I Learned
Working on this project helped me deepen my understanding of real‑world cloud automation and sharpen several engineering skills:

🔹 PowerShell Automation at Scale
I learned how to structure PowerShell scripts that are modular, predictable, and resilient — the kind of scripts that behave well even when cloud APIs don’t.

🔹 Identity & Access Management in Microsoft Entra ID
Automating user creation, group management, and RBAC assignments gave me hands‑on experience with:

Entra ID object models

Role‑based access control

Secure identity provisioning

🔹 Designing for Reliability (Error Handling + Retry Logic)
I gained a deeper appreciation for defensive scripting:

Using try/catch blocks

Implementing retry logic for transient Azure failures

Validating resources before creating them

Ensuring the script is idempotent and safe to run multiple times

🔹 Smart Resource Selection in Azure
Building the VM‑size selection logic taught me how to:

Query available VM SKUs in a region

Compare sizes based on cores and memory

Automatically choose the cheapest or closest match

🔹 Infrastructure as Code Mindset
This project reinforced the value of:

Repeatability

Consistency

Version control

Documentation

Automation over manual configuration

🔹 Cloud Networking & VM Deployment
Deploying a full VM stack helped me practice:

VNet and subnet creation

NIC and public IP configuration

Image selection and OS provisioning

🔹 Writing Clean, Documented, Shareable Code
Publishing this on GitHub pushed me to:

Organize the project into a clear folder structure

Write a professional README

Use meaningful commit messages

Treat the script like a real engineering deliverable


## Challenges I Faced
This project wasn’t just about writing PowerShell — it pushed me to solve real‑world cloud engineering problems.

🔹 Handling Azure’s Inconsistent API Behavior
Azure operations don’t always behave the same way twice. Some commands succeed instantly, others fail due to transient issues like throttling or propagation delays. This forced me to implement:

Retry logic

Error handling

Validation checks

🔹 Ensuring the Script Was Idempotent
I needed the script to run multiple times without breaking anything. That meant handling cases where:

Users already existed

Groups were already created

VM resources partially deployed

🔹 Smart VM Size Selection
Azure regions don’t always support the same VM sizes. I had to:

Query available sizes

Compare them

Select the closest match

Optionally pick the cheapest

🔹 Managing Dependencies Between Azure Resources
Deploying a VM requires:

A VNet

A subnet

A NIC

A public IP

If any of these fail, the whole deployment fails. I had to structure the script so each dependency was created in the correct order with proper validation.

🔹 Balancing Simplicity With Professional‑Grade Reliability
I wanted the script to be:

Easy to read

Easy to run

Easy to modify

But also:

Robust

Fault‑tolerant

Production‑ready

🔹 Logging and Troubleshooting
Cloud Shell sessions can be short‑lived, so I needed a reliable way to capture logs. Using PowerShell transcripts helped me:

Track failures

Debug issues

Understand script behavior over time



## License
MIT License — feel free to use, modify, and build upon this project.
