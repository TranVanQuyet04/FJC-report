---
title: "Week 7 Worklog"
# date: "`r Sys.Date()`"
weight: 1
chapter: false
pre: " <b> 1.7. </b> "
---
<!-- {{% notice warning %}} 
⚠️ **Note:** The following information is for reference purposes only. Please **do not copy verbatim** for your own report, including this warning.
{{% /notice %}} -->

### Week 7 Objectives:

* Understand AWS cost governance concepts and how AWS Budgets supports cost/usage monitoring.
* Practice creating multiple budget types (template, cost, usage, RI, Savings Plans) and configuring notifications.
* Learn how to clean up budgets to avoid unnecessary alerts and keep the account tidy.

### Tasks to be carried out this week:

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - Read workshop overview: AWS Budgets concepts, budget types, alerting behavior <br>- Note best practices (multi-threshold alerts, least privilege access, delays in billing updates) | 10/13/2025 | 10/13/2025 | <https://000007.awsstudygroup.com/> |
| 3 | - Create a budget quickly using AWS template (Monthly cost budget) <br>- Review configured thresholds (actual + forecast) | 10/14/2025 | 10/14/2025 | <https://000007.awsstudygroup.com/0-createtemplate/> |
| 4 | - Create a customized **Cost Budget** <br>- Configure alert recipients and thresholds (e.g., 50/80/90/100%) <br>- Observe budget overview & history screens | 10/15/2025 | 10/15/2025 | <https://000007.awsstudygroup.com/1-cost-budgets/> |
| 5 | - Create a **Usage Budget** (example: EC2 Running Hours) <br>- Configure actual / forecasted alerts <br>- Understand update latency (billing data refresh cadence) | 10/16/2025 | 10/16/2025 | <https://000007.awsstudygroup.com/2-usage-budget/> |
| 6 | - Create a **Reserved Instance (RI) Budget** (coverage/utilization monitoring) <br>- Create a **Savings Plans Budget** (coverage/utilization monitoring) <br>- Note that lab does not require purchasing RIs/Savings Plans | 10/17/2025 | 10/17/2025 | <https://000007.awsstudygroup.com/3-reservation-budget/> <br><https://000007.awsstudygroup.com/4-saving-plans-budget/> |
| 7 | - Review created budgets, alerts, and notification channels <br>- Clean up all lab budgets to prevent ongoing notifications <br>- Verify Budgets list is clean | 10/18/2025 | 10/18/2025 | <https://000007.awsstudygroup.com/5-clean-up/> |

### Week 7 Achievements:

* Understood AWS Budgets and how it helps monitor both **current** and **forecasted** spend/usage to avoid unexpected costs.
* Identified and differentiated common AWS budget types:
  * **Cost Budget**: track spend ($)
  * **Usage Budget**: track service usage (e.g., EC2 hours)
  * **RI Budget**: track reserved instance coverage/utilization
  * **Savings Plans Budget**: track Savings Plans coverage/utilization
* Successfully created budgets using:
  * **Template-based setup** (fast setup with default recommended alerts)
  * **Customized (advanced) setup** for granular control (scope, thresholds, recipients)
* Configured alerts using multiple thresholds and understood limitations:
  * Billing/usage data updates are not instant, so alerts may lag behind real-time usage.
  * Forecast alerts can trigger multiple times as predictions change.
* Practiced good governance hygiene:
  * Cleaned up lab budgets after completing exercises to avoid alert fatigue and account clutter.
