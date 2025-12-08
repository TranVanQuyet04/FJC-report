---
title: "Week 8 Worklog"
# date: "`r Sys.Date()`"
weight: 1
chapter: false
pre: " <b> 1.8. </b> "
---
<!-- {{% notice warning %}} 
⚠️ **Note:** The following information is for reference purposes only. Please **do not copy verbatim** for your own report, including this warning.
{{% /notice %}} -->


### Week 8 Objectives:

* Understand the fundamentals of **Amazon CloudWatch** and the role of monitoring/observability on AWS.
* Practice working with **Metrics**, **Logs**, **Logs Insights**, **Metric Filters**, **Alarms**, and **Dashboards**.
* Perform **resource cleanup** after completing the workshop to avoid unexpected charges.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | ---------- | --------------- | ------------------ |
| 2 | - Review AWS CloudWatch Workshop overview <br>- Understand the monitoring flow: Metrics ↔ Logs ↔ Alarms ↔ Dashboards | 10/20/2025 | 10/20/2025 | <https://000008.awsstudygroup.com/1-introduction/> |
| 3 | - Follow preparatory steps (resource setup) <br>- Verify created resources and access permissions | 10/21/2025 | 10/21/2025 | <https://000008.awsstudygroup.com/2-preparatory-steps/> |
| 4 | - **CloudWatch Metrics:** view & compare EC2 metrics (CPUUtilization, EBSWriteBytes, …) <br>- Improve charts (left/right Y-axis, horizontal/vertical annotations) | 10/22/2025 | 10/22/2025 | <https://000008.awsstudygroup.com/3-cloud-watch-metric/3.1-view-metrics/> |
| 5 | - **Search expressions:** use `SEARCH()` for faster metric discovery <br>- **Math expressions:** apply simple calculations and sorting (e.g., `SORT(e1, SUM, DEC, 3)`) | 10/23/2025 | 10/23/2025 | <https://000008.awsstudygroup.com/3-cloud-watch-metric/3.2-search-expression/> <br><https://000008.awsstudygroup.com/3-cloud-watch-metric/3.3-math-expression/> |
| 6 | - **Dynamic labels:** auto-generate readable labels using `PROP('Dim...')` <br>- Format labels like `${PROP('Dim.exe')} - ${PROP('Dim.InstanceId')} - ${PROP('MetricName')}` | 10/24/2025 | 10/24/2025 | <https://000008.awsstudygroup.com/3-cloud-watch-metric/3.4-dynamic-label/> |
| 7 | - **CloudWatch Logs:** explore `/ec2/linux/var/log/messages`, adjust retention <br>- **Logs Insights:** generate sample logs and query by ERROR/WARN, save queries <br>- **Metric Filter:** convert ERROR logs → metric (`ec2-logs`) <br>- **Alarms:** create alarm + SNS email notifications <br>- **Dashboards (optional):** build a dashboard combining metrics + alarms <br>- **Cleanup:** delete the CloudFormation stack and review remaining resources | 10/25/2025 | 10/26/2025 | <https://000008.awsstudygroup.com/4-cloud-watch-logs/> <br><https://000008.awsstudygroup.com/4-cloud-watch-logs/4.2-logs-insights/> <br><https://000008.awsstudygroup.com/4-cloud-watch-logs/4.3-metric-filter/> <br><https://000008.awsstudygroup.com/5-cloud-watch-alarm/> <br><https://000008.awsstudygroup.com/6-cloud-watch-dashboard/> <br><https://000008.awsstudygroup.com/7-clean-up-resources/> |

### Week 8 Achievements:

* Understood **Amazon CloudWatch** as AWS’s monitoring & observability service for collecting and visualizing **metrics/logs**, and triggering automated actions via **alarms**.
* Practiced analyzing **CloudWatch Metrics**:
  * Compared CPUUtilization across multiple EC2 instances.
  * Observed the relationship between CPU usage and storage I/O (EBSWriteBytes).
  * Improved chart readability using dual Y-axes and annotations.
* Learned advanced metric operations:
  * Used `SEARCH()` to quickly find metrics across namespaces.
  * Used metric math (e.g., `SORT(...)`) to rank and visualize top metrics.
* Implemented **Dynamic Labels** to automatically generate clear metric names when multiple dimensions exist.
* Worked with **CloudWatch Logs & Logs Insights**:
  * Explored log groups/streams and configured log retention.
  * Queried logs by keywords (ERROR/WARN), visualized results, and saved reusable queries.
* Created **Metric Filters** to convert logs into numeric metrics and configured **CloudWatch Alarms**:
  * Set threshold-based alarms (e.g., ERROR count exceeding a limit in 1 minute).
  * Integrated **SNS email notifications** to receive alerts.
* (Optional) Built a **CloudWatch Dashboard** to monitor key metrics and alarm states in a single view.
* Completed **resource cleanup** by deleting the CloudFormation stack and reviewing remaining monitoring data (logs/metrics retention).
