# Azure Identity & Access Management Lab

## Overview
This lab demonstrates **Azure Identity & Access Management (IAM)** using **Azure AD, RBAC, Managed Identities**, and security best practices. It is **AZ-104 scoped** and **Free Tier compatible**.

### Skills Demonstrated
- Azure AD Users and Groups
- Role-Based Access Control (RBAC)
- Managed Identity configuration
- Storage Account access control
- Least privilege principle
- Conditional Access & location-based access (documented for Free Tier)
- Activity logs and auditing

---

## Architecture
- Users and groups represent roles: **Cloud Admin, Helpdesk, App Support, Employee**
- Resource Groups organize resources for scoped access: `rg-prod-app` and `rg-shared-services`
- VM `vm-prod-01` hosts a **Managed Identity**
- Storage Account `stsecureaccess` demonstrates secure service-to-service authentication

![IAM Architecture](diagrams/iam-architecture.png)

---

## Resource & Role Design

| Component        | Role / Access                      | Scope                          | Purpose                                             |
|-----------------|-----------------------------------|-------------------------------|---------------------------------------------------|
| Cloud Admins     | Contributor + User Access Admin    | Subscription level            | Manage all resources and assign roles            |
| Helpdesk         | Virtual Machine Contributor        | Resource Group `rg-prod-app`  | Start/stop/restart VMs, reset passwords         |
| App Support      | Contributor                        | Resource Group `rg-prod-app`  | Deploy/manage apps without subscription-level access |
| Employees        | None                               | N/A                           | No Azure access                                   |
| VM `vm-prod-01`  | System-assigned Managed Identity   | Storage Account `stsecureaccess` | Secure access to blobs without credentials     |

---

## Lab Steps
1. Created Azure AD users: `cloud-admin`, `helpdesk`, `app-support`, `employee`
2. Created security groups and added users to groups
3. Created Resource Groups: `rg-prod-app`, `rg-shared-services`
4. Deployed VM `vm-prod-01` in `rg-prod-app`
5. Enabled **system-assigned Managed Identity** on the VM
6. Assigned subscription-level roles: **Cloud Admins → Contributor + User Access Admin**
7. Assigned resource group roles:
Helpdesk → **VM Contributor**
App Support → **Contributor**
Employees → **None**
8. Assigned **Storage Blob Data Reader** role to VM’s Managed Identity for `stsecureaccess`
9. Validated role enforcement by logging in as each user
10. Documented **Conditional Access & location-based access** (Free Tier)
11. Reviewed Azure AD sign-in and activity logs

---

## Validation
- RBAC assignments tested: each user/group had correct permissions
- VM successfully accessed storage via Managed Identity
- Azure AD sign-in logs confirmed actions
- Conditional Access and location-based access documented

---

## Screenshots
Screenshots are in the `/screenshots` folder:

---

## Free Tier Documentation
> **Note:** Certain security features require Azure AD Premium licenses and are not available in the Free Tier.  
> If I had a full subscription, I would have configured the following additional features for stronger security:  
> - **Multi-Factor Authentication (MFA)** for all users  
> - **Conditional Access** with location-based access policies to restrict logins to trusted IP ranges  
> - **Privileged Identity Management (PIM)** to enable just-in-time privileged access for Cloud Admins and other sensitive roles  

This documentation shows awareness of **best practices and enterprise security** even when restricted by Free Tier limitations.

---

## Notes
- Focused on **Free Tier-compatible hands-on steps** while demonstrating AZ-104 IAM concepts
