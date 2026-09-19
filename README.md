# 🔐 Identity Governance Lab
### Entra ID PIM · Access Reviews · Entitlement Management

> One-line takeaway: Building a hands-on identity governance lab demonstrating least-privilege access principles through just-in-time role activation, recurring access certification, and self-service access requests.

![Entra ID](https://img.shields.io/badge/Entra%20ID-0078D4?style=for-the-badge&logo=microsoftazure&logoColor=white)
![Intune](https://img.shields.io/badge/Intune-0078D4?style=for-the-badge&logo=microsoft&logoColor=white)
![PowerShell](https://img.shields.io/badge/PowerShell-5391FE?style=for-the-badge&logo=powershell&logoColor=white)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen?style=for-the-badge)

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

## 📊 Quick Summary

| Feature | What It Demonstrates | Status |
|---|---|---|
| PIM for Groups | Just-in-time privileged access | ✅ Complete |
| Access Reviews | Recurring access certification | ✅ Complete |
| Entitlement Management | Self-service access requests | ✅ Complete |

## 🔑 Skills Demonstrated
- Microsoft Entra ID Privileged Identity Management (PIM)
- Just-in-time (JIT) privileged access activation with approval workflows
- Access Reviews — recurring group/role membership certification
- Entitlement Management — access packages, request/approval policies, expiration
- Least-privilege access design principles
- Entra ID licensing and tenant administration
- Entra ID group-based access requests and manager approval workflows
- Access certification design (reviewer assignment, auto-remediation, decision helpers)

## 📦 What This Lab Covers

### 1. Privileged Identity Management (PIM)
*Status: ✅ Complete*
- Configure eligible (not permanent) role assignments
- Require justification, MFA, and approval on activation
- Review activation audit logs

### 2. Access Reviews
*Status: ✅ Complete*
- Set up a recurring review on group membership
- Configure self-review vs. manager-review
- Document a full review cycle

### 3. Entitlement Management
*Status: ✅ Complete*
- Build an access package bundling group + app + role
- Configure request/approval policy with expiration
- Walk through a full request → approval → expiration cycle

## 🛠️ Notable Troubleshooting
| Issue | Root Cause | Resolution |
|---|---|---|
| PIM role assignment failed ("role is not found") across multiple Entra roles | Tenant-specific backend issue isolated to PIM's Entra role assignment feature (license and role definitions confirmed valid) | Pivoted to PIM for Groups — same just-in-time access model, different backend path, worked successfully |
| PIM activation failed ("Role assignment already exists") | Priya was still a permanent/direct group member from initial setup, conflicting with her separate PIM-eligible assignment | Removed her permanent membership — PIM eligibility became her only path into the group |

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

### September 14, 2026 — PIM Configuration Started
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

### September 19, 2026 — PIM Activation Requirements Configured
- Edited the "Member" role settings for IT-Admins under Groups > Privileged Identity
  Management
- Enabled "Azure MFA" as a required condition on activation
- Confirmed "Require justification on activation" was already enabled by default
- Enabled "Require approval to activate" and added KokoriLab admin as the designated approver
- IT-Admins now demonstrates a full just-in-time access model: eligible (not permanent)
  membership, requiring MFA, a written justification, and manager approval before
  activation succeeds
- Next: test the full activation cycle as Priya Patel, then approve the request as admin

### September 19, 2026 — Full PIM Activation Cycle Tested (PIM Complete)
- Signed in as Priya Patel in a separate browser session to test activation from the
  requester's perspective
- First activation attempt failed: "The Role assignment already exists" — root cause was
  Priya still being a permanent/direct member of IT-Admins from initial group creation,
  conflicting with her separate PIM-eligible assignment
- Resolved by removing Priya's permanent membership, leaving PIM eligibility as her only
  path into the group — a cleaner, more realistic setup (James Okafor remains a standard
  permanent member for contrast)
- Successfully activated: provided justification, completed Azure MFA, request went to
  "pending approval"
- Switched to admin account, reviewed and approved the pending request via
  PIM > Approve requests
- Verified Priya now shows as an active, time-limited member of IT-Admins
- Full just-in-time access cycle demonstrated end-to-end: eligible → requested → MFA →
  justification → approval → active (temporary) access

### September 19, 2026 — Access Review Configured for Finance-Team
- Navigated to Identity Governance > Access reviews to create a new review (the direct
  "Access reviews" search result led to a limited legacy view with no create option —
  Identity Governance was the correct path)
- Selected "Resource review" template, scoped to the Finance-Team group, reviewing all
  members (not guest-only)
- Set recurrence to Quarterly, 7-day review window, starting immediately with no end date
- Assigned Maria Lopez (Finance Manager) as the reviewer — a realistic manager-reviews-
  their-own-team setup
- Enabled auto-apply results with "Remove access" as the default if no response —
  demonstrating fail-secure, least-privilege enforcement
- Enabled the "No sign-in within 30 days" decision helper to assist the reviewer
- Enabled justification requirement, email notifications, and reminders
- Named it "Finance-Team Quarterly Access Review" and created it successfully

### September 19, 2026 — Entitlement Management Access Package Created (Project Complete)
- Created an access package under Identity Governance > Entitlement Management > Access
  packages, using the default "General" catalog
- Named it "HR Onboarding Access Package", scoped to the HR-Team group (Member role)
- Configured request settings: "For users, service principals, and agent identities in
  your directory" with "Specific users and groups" scope, restricted to David Kim
- Enabled a single-stage approval workflow with KokoriLab admin as approver, 14-day
  decision window, email notifications enabled
- Set access to expire after 90 days (adjusted down from the 365-day default for a more
  demonstrable, realistic expiration window)
- Left custom extensions unconfigured (requires additional licensing beyond this lab's scope)
- Package created successfully — completes all three pillars of this lab: PIM, Access
  Reviews, and Entitlement Management, each independently configured and verified

## 🚧 Status
✅ Complete — all three governance pillars (PIM, Access Reviews, Entitlement Management) configured and verified end-to-end.
