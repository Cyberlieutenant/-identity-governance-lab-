# 🔐 Identity Governance Lab
### Entra ID PIM · Access Reviews · Entitlement Management

> One-line takeaway: Built a hands-on identity governance lab demonstrating least-privilege access through just-in-time privileged access, recurring access certification, and self-service access requests with approval workflows.

![Entra ID](https://img.shields.io/badge/Entra%20ID-0078D4?style=for-the-badge&logo=microsoftazure&logoColor=white)
![Microsoft 365](https://img.shields.io/badge/Microsoft%20365-D83B01?style=for-the-badge&logo=microsoftoffice&logoColor=white)
![Identity Governance](https://img.shields.io/badge/Identity%20Governance-0078D4?style=for-the-badge&logo=microsoft&logoColor=white)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen?style=for-the-badge)

## 🎯 Goal

Built and tested a hands-on Microsoft Entra ID Identity Governance environment focused on least-privilege access.

The lab demonstrates three core governance capabilities:

- Just-in-time privileged access using PIM for Groups
- Recurring access certification using Access Reviews
- Self-service access requests using Entitlement Management

The environment uses test Finance, IT, and HR users to simulate real identity and access management scenarios.

## 🧱 Environment

| Component | Details |
|---|---|
| Tenant | Microsoft 365 with Entra ID P2 Trial |
| Test Users | 5 users representing Finance, IT, and HR |
| Groups | Finance-Team, IT-Admins, HR-Team |
| PIM Target | IT-Admins |
| Access Review Target | Finance-Team |
| Entitlement Management Target | HR-Team |

## 📊 Quick Summary

| Feature | What It Demonstrates | Status |
|---|---|---|
| PIM for Groups | Just-in-time privileged access | ✅ Complete |
| Access Reviews | Recurring access certification | ✅ Complete |
| Entitlement Management | Self-service access requests | ✅ Complete |

## 🔑 Skills Demonstrated

- Microsoft Entra ID Identity Governance
- Privileged Identity Management (PIM)
- Just-in-time (JIT) privileged access
- Multi-Factor Authentication (MFA)
- Access Reviews
- Access certification
- Entitlement Management
- Access Packages
- Approval workflows
- Group-based access management
- Identity lifecycle management
- Least-privilege access
- Microsoft 365 tenant administration
- Identity and access troubleshooting
- Root cause analysis

## 📦 What This Lab Covers

### 1. Privileged Identity Management (PIM)
Status: ✅ Complete

Configured PIM for the IT-Admins security group to provide temporary privileged access instead of permanent membership.

- Configured Priya Patel as an eligible IT-Admins member
- Required Azure MFA during activation
- Required written justification
- Required administrator approval
- Tested activation from the end-user account
- Approved the request from the administrator account
- Verified temporary active membership

### 🔄 PIM Workflow

`Eligible → Request → MFA → Justification → Approval → Temporary Access`

### 2. Access Reviews
Status: ✅ Complete

Configured a recurring Access Review for the Finance-Team security group.

- Created Finance-Team Quarterly Access Review
- Assigned Maria Lopez as the reviewer
- Configured quarterly recurrence
- Set a 7-day review period
- Enabled automatic application of review results
- Configured access removal when no response is received
- Required reviewer justification
- Enabled email notifications and reminders
- Enabled the "No sign-in within 30 days" decision helper

### 🔄 Access Review Workflow

`Group Membership → Manager Review → Approve/Deny → Apply Results → Retain/Remove Access`

### 3. Entitlement Management
Status: ✅ Complete

Created an HR onboarding access package to demonstrate controlled access requests and expiration.

- Created HR Onboarding Access Package
- Added HR-Team as the resource
- Scoped the request policy to David Kim
- Configured single-stage approval
- Assigned KokoriLab admin as approver
- Set a 14-day approval window
- Configured access to expire after 90 days
- Enabled email notifications

### 🔄 Entitlement Management Workflow

`Request Access → Approval → HR-Team Membership → 90-Day Access → Expiration`

## 🛠️ Notable Troubleshooting

| Issue | Root Cause | Resolution |
|---|---|---|
| PIM role assignment failed with "role is not found" | Issue isolated to the tenant's PIM Entra role assignment path | Pivoted to PIM for Groups and completed the JIT access workflow |
| PIM activation failed with "Role assignment already exists" | Priya still had permanent IT-Admins membership | Removed permanent membership and retained PIM eligibility |
| Access Reviews page had no "New access review" option | Search opened a limited interface | Navigated through Identity Governance > Access Reviews |
| HR-Team did not appear in the access package | Group was not already included in the General catalog | Expanded the search to groups outside the General catalog |

## 🏆 Project Outcomes

Through this lab, I configured and validated three Microsoft Entra ID Identity Governance scenarios.

### Privileged Access
Implemented just-in-time privileged group membership requiring MFA, justification, approval, and temporary activation.

### Access Certification
Implemented recurring manager-led access reviews with automatic result application and access removal.

### Access Lifecycle
Built an HR onboarding access package with request approval and 90-day access expiration.

### Troubleshooting
Diagnosed configuration issues by validating licensing, testing multiple roles, checking existing group membership, testing separate browser sessions, and isolating configuration paths.

## 💡 Key Takeaways

This project strengthened my hands-on experience with Microsoft Entra ID Identity Governance.

I gained practical experience controlling:

- Who receives access
- Who approves access
- When privileged access becomes active
- How long access stays active
- How access gets reviewed
- How unnecessary access gets removed

The troubleshooting process also strengthened my approach to diagnosing identity and access issues by checking licensing, role assignments, group membership, and governance policies before applying changes.

## 📅 Progress Log

### September 9, 2026 — Environment Setup & Licensing

- Created the GitHub repository
- Activated the Microsoft Entra ID P2 trial
- Confirmed the subscription was active
- Assigned the required license
- Verified access to Privileged Identity Management

### September 14, 2026 — Test Organization Setup

Created five test users:

- Sarah Chen — Finance Analyst
- Maria Lopez — Finance Manager
- James Okafor — IT Support Specialist
- Priya Patel — IT Manager
- David Kim — HR Coordinator

Created three security groups:

- Finance-Team
- IT-Admins
- HR-Team

### September 14, 2026 — PIM Configuration Started

- Accessed Privileged Identity Management
- Attempted an eligible Helpdesk Administrator assignment
- Encountered the "role is not found" error
- Tested the issue across different Entra roles
- Began isolating the source of the failure

### September 19, 2026 — PIM Completed

- Verified Entra ID P2 licensing
- Verified Entra role definitions
- Tested multiple Entra roles
- Isolated the Entra role assignment issue
- Pivoted to PIM for Groups
- Added Priya Patel as an eligible IT-Admins member
- Required MFA, justification, and approval
- Removed conflicting permanent membership
- Completed the activation request
- Approved the request as administrator
- Verified temporary active membership

### September 19, 2026 — Access Review Completed

- Created Finance-Team Quarterly Access Review
- Assigned Maria Lopez as reviewer
- Configured quarterly recurrence
- Set a 7-day review window
- Enabled automatic application of results
- Configured access removal for no response
- Enabled the 30-day sign-in decision helper
- Required justification
- Enabled notifications and reminders

### September 19, 2026 — Entitlement Management Completed

- Created HR Onboarding Access Package
- Added HR-Team as the resource
- Scoped requests to David Kim
- Configured single-stage approval
- Assigned KokoriLab admin as approver
- Set a 14-day approval window
- Configured 90-day access expiration
- Enabled email notifications
- Successfully created the access package

## 🚀 Future Improvements

- Add Conditional Access to privileged access scenarios
- Test additional PIM-managed groups
- Build access packages for additional departments
- Test automatic access expiration and removal
- Configure multi-stage approval workflows
- Add Microsoft Graph or PowerShell reporting
- Export PIM and audit activity for security monitoring

## 🚧 Status

✅ Complete — PIM for Groups, Access Reviews, and Entitlement Management configured and validated.
