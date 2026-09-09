# 🔐 Identity Governance Lab
### Entra ID PIM · Access Reviews · Entitlement Management

![Entra ID](https://img.shields.io/badge/Entra%20ID-0078D4?style=for-the-badge&logo=microsoftazure&logoColor=white)
![Intune](https://img.shields.io/badge/Intune-0078D4?style=for-the-badge&logo=microsoft&logoColor=white)
![PowerShell](https://img.shields.io/badge/PowerShell-5391FE?style=for-the-badge&logo=powershell&logoColor=white)
![Status](https://img.shields.io/badge/Status-In%20Progress-yellow?style=for-the-badge)

## 🎯 Goal
Building a hands-on identity governance lab demonstrating least-privilege access
principles — just-in-time privileged role activation, recurring access certification,
and self-service access requests with approval workflows — in a Microsoft 365 tenant.

## 🧱 Environment
| Component | Details |
|---|---|
| Tenant | Microsoft 365 (Entra ID P2 — licensing to be confirmed) |
| Identities | Test user accounts simulating a real org structure |
| Groups | Security groups representing sample departments/roles |

## 🔑 Skills Demonstrated
- Microsoft Entra ID Privileged Identity Management (PIM)
- Just-in-time (JIT) privileged access activation with approval workflows
- Access Reviews — recurring group/role membership certification
- Entitlement Management — access packages, request/approval policies, expiration
- Least-privilege access design principles
- Entra ID licensing and tenant administration

## 📦 What This Lab Covers

### 1. Privileged Identity Management (PIM)
*Status: not started*
- Configure eligible (not permanent) role assignments
- Require justification, MFA, and approval on activation
- Review activation audit logs

### 2. Access Reviews
*Status: not started*
- Set up a recurring review on group membership
- Configure self-review vs. manager-review
- Document a full review cycle

### 3. Entitlement Management
*Status: not started*
- Build an access package bundling group + app + role
- Configure request/approval policy with expiration
- Walk through a full request → approval → expiration cycle

## 🛠️ Notable Troubleshooting
| Issue | Root Cause | Resolution |
|---|---|---|
| *(populated as the lab progresses)* | | |

## 📋 Documentation Approach
Each stage of this lab documents:
- What I configured and why
- What errors I hit, and how I diagnosed them — not just the fix
- What I'd do differently next time

## 📅 Progress Log

### [Date] — Environment Setup
- Repo created to document the build as I go
- Next: confirm Entra ID P2 licensing availability

## 🚧 Status
In progress — environment setup phase
