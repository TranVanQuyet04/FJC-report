---
title: "Week 2 Worklog"
# date: "`r Sys.Date()`"
weight: 1
chapter: false
pre: " <b> 1.2. </b> "
---
<!-- {{% notice warning %}} 
⚠️ **Note:** The following information is for reference purposes only. Please **do not copy verbatim** for your own report, including this warning.
{{% /notice %}} -->


### Week 2 Objectives:

* Learn and practice **AWS Identity and Access Management (IAM)** with a focus on secure access control.
* Understand IAM core components: **User / Group / Policy / Role** and the **Least Privilege** principle.
* Build a recommended administration model:
  * Create an **Admin Group + Admin User** for daily administration instead of using the root user.
  * Create **AdminRole** and **OperatorUser**, then practice **AssumeRole** and **Switch Role**.
* Understand the difference between **Trust policy** (who can assume a role) and **Permission policy** (what the role can do).
* Perform **cleanup** of IAM lab resources to maintain security hygiene.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - Read IAM overview (concepts: user/group/policy/role) <br>- Take notes on best practices (MFA, root user, least privilege, CloudTrail) | 09/12/2025 | 09/12/2025 | <https://000002.awsstudygroup.com/1-introduction/> <br> <https://000002.awsstudygroup.com/1-introduction/1.1-group-user/> <br> <https://000002.awsstudygroup.com/1-introduction/1.2-iam-policy/> |
| 3 | - Practice: create **IAM Admin Group** and attach **AdministratorAccess** <br>- Create **AdminUser** and add to Admin Group | 09/13/2025 | 09/13/2025 | <https://000002.awsstudygroup.com/2-create-admin-user-and-group/2.1-create-admin-group/> |
| 4 | - Sign in to AWS using **AdminUser** via the console sign-in URL <br>- Verify permissions and navigate IAM services | 09/14/2025 | 09/14/2025 | <https://000002.awsstudygroup.com/2-create-admin-user-and-group/2.1-create-admin-group/> |
| 5 | - Practice: create **AdminRole** (attach AdministratorAccess) <br>- Create **OperatorUser** (no direct permissions attached) | 09/15/2025 | 09/15/2025 | <https://000002.awsstudygroup.com/3-aws-role/> |
| 6 | - Allow OperatorUser to **sts:AssumeRole** into AdminRole (inline policy) <br>- Sign in as OperatorUser and **Switch Role** to AdminRole <br>- **Cleanup**: delete lab users/groups/roles/policies | 09/16/2025 | 09/16/2025 | <https://000002.awsstudygroup.com/4-switch-roles/> <br> <https://000002.awsstudygroup.com/4-switch-roles/4.2-login-operatoruser/> <br> <https://000002.awsstudygroup.com/4-switch-roles/4.3-switchrole/> <br> <https://000002.awsstudygroup.com/5-cleanup/> |

### Week 2 Achievements:

* Understood foundational IAM concepts and security best practices:
  * IAM Users, Groups, Policies, Roles
  * Difference between **Permission policy** and **Trust policy**
  * Applied the **Least Privilege** principle and avoided using the root user for daily tasks

* Successfully set up a basic administrative structure:
  * Created an **Admin Group** and attached **AdministratorAccess**
  * Created an **AdminUser** and managed access via group-based permissions

* Practiced role-based access control (RBAC) using IAM Roles:
  * Created **AdminRole** with **AdministratorAccess**
  * Created **OperatorUser** without direct permissions

* Configured and validated role assumption:
  * Attached an inline policy granting `sts:AssumeRole` for OperatorUser to assume **AdminRole**
  * Logged in as OperatorUser and used **Switch Role** to obtain temporary administrative permissions

* Completed IAM lab cleanup:
  * Removed created IAM resources (users/groups/roles/policies) to reduce security risk and keep the account tidy
