# 🔐 Identity Governance Lab
### Entra ID PIM · Access Reviews · Entitlement Management

> One-line takeaway: Building a hands-on identity governance lab demonstrating least-privilege access principles through just-in-time role activation, recurring access certification, and self-service access requests.

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
| Tenant | Microsoft 365 with Entra ID P2 (Trial) — confirmed active |
| Test Users | 5 users simulating Finance, IT, and HR roles |
| Groups | Finance-Team, IT-Admins, HR-Team — each mapped to a governance feature |

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
| PIM role assignment failed ("role is not found") | Likely first-time PIM backend sync delay after enabling P2 licensing | Under investigation — retry planned after wait period |
| PIM role assignment failed ("role is not found") across multiple Entra roles | Tenant-specific backend issue isolated to PIM's Entra role assignment feature (license and role definitions confirmed valid) | Pivoted to PIM for Groups — same just-in-time access model, different backend path, worked successfully |

## 📋 Documentation Approach
Each stage of this lab documents:
- What I configured and why
- What errors I hit, and how I diagnosed them — not just the fix
- What I'd do differently next time

## 📅 Progress Log

### September 9, 2026 — Environment Setup & Licensing
- Repo created to document the build as I go
- Checked Microsoft 365 admin center Marketplace for Entra ID P2 trial availability
- Added the trial package; confirmed active in Billing > Subscriptions
- Assigned the license to admin account via Users > Licenses and Apps
- Verified P2 features unlocked by successfully loading Privileged Identity Management
  in Entra ID with no licensing error
- Next: create test users and security groups to simulate a sample org structure,
  then begin PIM configuration
  ### September 14, 2026 — Test Org Structure Setup
- Created 5 test users representing a small sample organization:
  Sarah Chen (Finance Analyst), Maria Lopez (Finance Manager),
  James Okafor (IT Support Specialist), Priya Patel (IT Manager),
  David Kim (HR Coordinator)
- Created 3 security groups mapped to different governance features to demo:
  Finance-Team (for Access Reviews), IT-Admins (for PIM), HR-Team (for Entitlement Management)
- Next: configure PIM on IT-Admins — eligible role assignment with approval workflow
- ### September 14, 2026 — PIM Configuration Started
- Navigated to Privileged Identity Management > Microsoft Entra roles for the first time
  on this tenant, confirming P2-licensed features are accessible
- Located the Helpdesk Administrator role and attempted to add James Okafor as an
  Eligible assignment (not Active/permanent) — the correct just-in-time access model
- First attempt failed: "Role assignment failed... The role is not found" — likely a
  first-time PIM backend sync delay on a freshly-licensed trial tenant
- Next: retry after allowing backend sync time; if it persists, test with a different
  role to isolate the cause
  ### September 19, 2026 — PIM Troubleshooting & Successful Pivot
- Attempted to assign James Okafor as Eligible for the Helpdesk Administrator role via
  PIM > Microsoft Entra roles — failed with "Role assignment failed... The role is not
  found"
- Isolated the cause methodically: retried with a different role (User Administrator) —
  same error; retried in a fresh incognito session to rule out stale tokens — same error;
  confirmed via Billing that the Entra ID P2 license was genuinely active and assigned;
  confirmed via Roles & admins (outside PIM) that role definitions exist normally in
  the directory
- Concluded this was a tenant-specific backend issue isolated to PIM's Entra role
  assignment path, not a licensing or configuration problem
- Pivoted to PIM for Groups instead — a legitimate, commonly-used alternative that
  demonstrates the same just-in-time access concept applied to group membership
- Successfully added Priya Patel as an Eligible member of IT-Admins via
  Groups > Privileged Identity Management > IT-Admins > Add assignments
- Next: configure activation requirements (MFA, approval, justification) and test a
  full activation cycle

### 1. Privileged Identity Management (PIM)
*Status: 🔄 in progress — using PIM for Groups*
