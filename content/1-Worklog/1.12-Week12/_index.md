---
title: "Week 12 Worklog"
# date: "`r Sys.Date()`"
weight: 2
chapter: false
pre: " <b> 1.12. </b> "
---
<!-- {{% notice warning %}} 
⚠️ **Note:** The following information is for reference purposes only. Please **do not copy verbatim** for your own report, including this warning.
{{% /notice %}} -->

### Week 12 Objectives:

* Understand **AWS IAM Identity Center** (AWS SSO) and how it supports centralized identity & access management.
* Practice setting up a basic **multi-account structure** using **AWS Organizations** and role switching.
* Apply security concepts: **least privilege**, **time-based access control**, and **customer managed policies** in permission sets.
* Get exposure to automation via **IAM Identity Center Identity Store APIs** (Python/Boto3).

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | ---- | ---------- | --------------- | ------------------ |
| 2 | - Read workshop overview and scenario <br> - Identify prerequisites, recommended region, expected cost notes | 11/17/2025 | 11/17/2025 | <https://000012.awsstudygroup.com/1-prerequisite/> |
| 3 | - Create member accounts in **AWS Organizations** (Security/Shared Services/Logging/Application) <br> - Create and organize **Organizational Units (OUs)** | 11/18/2025 | 11/18/2025 | <https://000012.awsstudygroup.com/1-prerequisite/> |
| 4 | - Invite an existing AWS account into AWS Organizations (if needed) <br> - Practice **Switch Role** to member accounts (OrganizationAccountAccessRole) <br> - Understand least-privilege approach for assume-role permissions | 11/19/2025 | 11/19/2025 | <https://000012.awsstudygroup.com/1-prerequisite/4-switch-role/> |
| 5 | - Configure AWS CLI access using IAM Identity Center (SSO) <br> - Compare manual credential refresh vs `aws configure sso` automatic refresh (OIDC device code) | 11/20/2025 | 11/20/2025 | <https://000012.awsstudygroup.com/2-aws-cli-access/> |
| 6 | - Implement **time-based access control** using permission sets + inline policy conditions (`aws:CurrentTime`) <br> - Create group/user (e.g., securityAuditors / secAuditUser) and assign permission set to an AWS account <br> - Verify access before/after changing time window | 11/21/2025 | 11/21/2025 | <https://000012.awsstudygroup.com/3-using-time-based-access-control/> |
| 7 | - Implement **Customer Managed Policies (CMP)** with permission sets (policy name must match across accounts) <br> - Explore **Identity Store APIs** using Python/Boto3 sample repo (create group/user, add user to group, list members & memberships) <br> - Clean up resources (delete stack if created, remove IAM Identity Center configuration after documenting settings) | 11/22/2025 | 11/22/2025 | <https://000012.awsstudygroup.com/4-using-customer-managed-policies/> <br> <https://000012.awsstudygroup.com/%CC%805-iam-identity-center-identity-store-apis/> <br> <https://000012.awsstudygroup.com/6-clean-up/#resource-cleanup> |

### Week 12 Achievements:

* Understood the purpose and benefits of **AWS IAM Identity Center** for centralized identity management across multiple AWS accounts.

* Built foundational knowledge for multi-account governance with **AWS Organizations**, including:
  * creating member accounts,
  * organizing **OUs**,
  * accessing member accounts via **Switch Role**.

* Successfully configured **AWS CLI authentication** with IAM Identity Center and understood why automatic credential refresh improves security (short-lived sessions, less exposure of credentials).

* Implemented **least-privilege controls** using:
  * **time-based access control** in permission set inline policies (UTC time conditions),
  * **Customer Managed Policies (CMPs)** reused via permission sets across accounts.

* Learned how IAM Identity Center can be automated at scale using **Identity Store APIs** (Python/Boto3), including managing users, groups, and membership auditing.

* Completed **resource cleanup** steps to prevent unnecessary charges and remove workshop configurations after practice.
