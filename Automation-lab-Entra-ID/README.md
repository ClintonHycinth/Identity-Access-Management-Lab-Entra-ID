Azure Lab Automation Script (PowerShell)
This project automates the full setup of a Microsoft Azure lab environment using PowerShell in Azure Cloud Shell. It replaces a multi‑step manual process with a single, reliable, repeatable script designed with production‑grade engineering practices.

✅ Features
Identity Automation
Creates Microsoft Entra ID users

Generates secure passwords

Creates a security group

Adds users to the group with validation checks

Smart VM Sizing
Uses your preferred VM size if available

Automatically selects the closest available size in the region

Optional: auto‑selects the cheapest VM size

Virtual Machine Deployment
Deploys Windows Server 2025 Datacenter

Creates VNet, subnet, NIC, and public IP

Supports custom admin credentials

Includes retry logic for transient Azure failures

RBAC Assignment
Assigns “Virtual Machine Contributor” to the group

Ensures proper access control at the resource‑group level

Enterprise‑Grade Reliability
Full try/catch error handling

Retry logic for Azure API operations

Logging via PowerShell transcript

Idempotent behavior (safe to run multiple times)

Validation before every major step


✅ How to Run
Basic run:
powershell^
./Deploy-Lab.ps1


Use a specific VM size
powershell^
./Deploy-Lab.ps1 -PreferredVMSize "Standard_D2s_v5"


Automatically pick the cheapest VM size
powershell^
./Deploy-Lab.ps1 -AutoPickCheapest


✅ Requirements
Azure Cloud Shell (recommended)

Az PowerShell modules

AzureAD module

Azure subscription with permissions to:

Create users

Create groups

Deploy VMs

Assign RBAC roles


✅ What I Learned
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


✅ Challenges I Faced
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



✅ License
MIT License — feel free to use, modify, and build upon this project.
