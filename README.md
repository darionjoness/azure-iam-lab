Azure Identity & Access Management Lab

Overview

This project demonstrates identity and access management in Azure using Azure AD, Role-Based Access Control, and Managed Identities to enforce least-privilege access for different user roles.

The lab focuses on core AZ-104 IAM concepts including:

Azure AD Users and Groups

Role-Based Access Control 

Managed Identities

Least Privilege Principle

Storage Account Access

Conditional Access & Location-Based Access (documented for Free Tier)

Activity Logs and Auditing

Architecture

Users and groups represent roles: Cloud Admin, Helpdesk, App Support, Employee

Resource Groups organize resources: rg-prod-app for apps, rg-shared-services for storage

VM vm-prod-01 hosts a Managed Identity

Storage Account stsecureaccess demonstrates secure service-to-service authentication

Lab Architecture Diagram:


Resource & Role Design

Component	Role / Access	Scope	Purpose

Cloud Admins - Contributor + User Access Admin at	Subscription level to	Manage all resources and assign roles

Helpdesk - Virtual Machine Contributor at	Resource Group rg-prod-app to	Start/stop/restart VMs, reset passwords

App Support -	Contributor at	Resource Group rg-prod-app to	Deploy/manage apps without subscription-level access

Employees	- No Azure Access

VM vm-prod-01 -	System-assigned Managed Identity at	Storage Account stsecureaccess to	Secure access to blobs without credentials
Key Configuration Steps

Created Azure AD users: cloud-admin, helpdesk, app-support, employee

Created security groups and added users to groups

Created Resource Groups: rg-prod-app, rg-shared-services

Deployed VM vm-prod-01 in rg-prod-app

Enabled system-assigned Managed Identity on VM

Assigned subscription-level roles: Cloud Admins → Contributor + User Access Admin

Assigned resource group roles:

Helpdesk → VM Contributor

App Support → Contributor

Employees → None

Assigned Storage Blob Data Reader role to VM’s Managed Identity for stsecureaccess

Validated role enforcement by logging in as each user

Documented Conditional Access & location-based access (Free Tier)

Validation

RBAC assignments tested: each user/group had correct permissions

VM successfully accessed storage via Managed Identity

Azure AD sign-in logs confirmed actions

Conditional Access and location-based access documented

Screenshots are in the /screenshots folder:

Users & Groups

VM with Managed Identity

Role Assignments

Storage Access from Managed Identity

Skills Demonstrated

Azure AD Users and Groups

Role-Based Access Control (RBAC)

Managed Identity configuration

Storage Account access control

Least Privilege Principle

Conditional Access & Location-Based Policies (documented)

Azure Activity Logs and Auditing
