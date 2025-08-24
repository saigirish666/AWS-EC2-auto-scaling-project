# AWS EC2 Auto Scaling Project 🚀

This guided project explores how to launch and manage **Auto Scaling Groups (ASG)** for EC2, enabling your infrastructure to dynamically adjust to demand.  
The project builds practical skills in creating launch templates, configuring scaling groups, and verifying automatic replacement of instances.

---

## 🚀 Table of Contents
- [Lab Sections Overview](#-lab-sections-overview)
  - [1. Creating a Security Group](#1-creating-a-security-group)
  - [2. Creating a Launch Template](#2-creating-a-launch-template)
  - [3. Creating an Auto Scaling Group](#3-creating-an-auto-scaling-group)
  - [4. Verifying Auto Scaling Behavior](#4-verifying-auto-scaling-behavior)
  - [5. Cleanup: Terminating Scaling Infrastructure](#5-cleanup-terminating-scaling-infrastructure)
- [🌟 Observations & Console Evolution](#-observations--console-evolution)
- [✅ Summary of Skills Acquired](#-summary-of-skills-acquired)

---

## 🔍 Lab Sections Overview

### 1. Creating a Security Group
**Objective:** Configure secure instance-level access.  

**Steps:**
- Created new security group: `autoscalingprojectsecuritygroup`
- Allowed inbound **SSH (port 22)** for management access.
- Left outbound rules as default (allow all).

**Key Learnings:**
- Security groups act as virtual firewalls at the instance level.  
- Best practice: restrict inbound rules and allow **least privilege access**.

---

### 2. Creating a Launch Template
**Objective:** Define instance configuration for Auto Scaling.  

**Steps:**
- Created launch template: `autoscalingprojextLaunchtemplate`
- Used **Amazon Linux AMI** as base image and selected free tier eligible instance type.
- Configured storage and other basics for template.

**Console Differences:**
- **Older console:** had option to choose Networking Platform (VPC/EC2-Classic).  
- **Latest console:**  
  - Networking Platform option removed.  
  - Advanced Network Configuration panel includes **network interfaces** (previously a separate tab).  

**Key Learnings:**
- Launch templates define EC2 blueprint (**AMI, instance type, security group, storage**).  
- Templates can have **multiple versions** to support updates.

---

### 3. Creating an Auto Scaling Group
**Objective:** Configure automatic scaling from the launch template.  

**Steps:**
- Created Auto Scaling Group: `project4scalinggroup`  
- Linked to the previously created launch template.  
- Did **not** configure a load balancer for this project.

**Console Differences:**
- **Old console:** Instance Purchase Option had  
  - *Adhere to launch template*  
  - *Combine purchase options and instance types*  
- **Latest console:**  
  - Shows **Instance Type Requirements** (default from template).  
  - Option to **Override Launch Template** for more flexibility.

**Key Learnings:**
- Auto Scaling **replaces missing/unhealthy instances** automatically.  
- Flexible setup allows combining different instance types if needed.

---

### 4. Verifying Auto Scaling Behavior
**Objective:** Validate that Auto Scaling replaces terminated instances.  

**Steps:**
- Upon group creation, ASG launched an initial instance automatically.  
- Verified scaling behavior by observing health checks:  
  - Auto Scaling polls instances every **5 minutes**.  
  - If an instance fails/terminated, ASG launches a replacement.

**Key Learnings:**
- Auto Scaling ensures **fault tolerance** by maintaining desired capacity.  
- Default checks take ~5 minutes before replacement action triggers.

---

### 5. Cleanup: Terminating Scaling Infrastructure
**Objective:** Avoid ongoing costs by deleting all resources.  

**Steps:**
- Deleted Auto Scaling Group first (to avoid re-launches of terminated instances).  
- Confirmed that associated instances were automatically terminated with ASG.  
- Deleted the launch template (noting that multiple versions can exist).  
- Deleted the security group after use.

**Key Learnings:**
- Always remove scaling groups before instances.  
- Launch templates persist until deleted manually.  
- Cleanup is essential to prevent unintended charges.

---

## 🌟 Observations & Console Evolution

### Networking Settings
- Older console allowed selecting **EC2-Classic vs VPC** platform.  
- Latest console removed this option.  
- Advanced network configuration now consolidates features.

### Instance Options
- Old console referenced **purchase option modes**.  
- New console offers **Instance Type Requirements + Override Template** flexibility.  

### User Experience
- Current console simplifies setup into fewer, more intuitive steps.  
- Automation-first design: scaling groups immediately spin up initial instances.

---

## ✅ Summary of Skills Acquired
By completing this project, I demonstrated the ability to:

- Create and configure **security groups** for safe inbound/outbound traffic.  
- Build **launch templates** with reusable EC2 settings.  
- Design and deploy **Auto Scaling Groups** to ensure high availability.  
- Understand **console evolution** (differences between older UI and 2025 updates).  
- Verify scaling behaviors by simulating **instance termination and ASG recovery**.  
- Clean up AWS resources efficiently to prevent unexpected charges.  

These skills strengthen my **cloud infrastructure knowledge**, enabling me to architect secure, fault-tolerant, and cost-effective AWS environments.

---
