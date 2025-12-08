---
title: "Enhanced Network Security Control: Flow Management with AWS Network Firewall"
date: "2025-04-09"
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

<!-- {{% notice warning %}}
⚠️ **Note:** The information below is for reference purposes only. Please **do not copy verbatim** for your report, including this warning.
{{% /notice %}} -->

<!-- # Enhanced Network Security Control: Flow Management with AWS Network Firewall -->

**AWS Network Firewall:** A managed, stateful firewall and IDS/IPS service that enforces security rules for fine-grained control of VPC network traffic.

**Problem context:** Once a flow is allowed, that decision can remain in effect for the lifetime of the flow. When rules are updated (e.g., broad → strict), existing long-running flows may continue under the old decision unless action is taken.

**New capabilities introduced:**
- **Flow capture:** Point-in-time visibility into active flows for monitoring and troubleshooting.
- **Flow flush:** Selective termination/removal of flow state (specific flows or all flows) to re-apply policy or isolate suspicious traffic.

**Access methods:** Available through the **AWS Management Console** and the **AWS Network Firewall API**.

---

## Keyword Terminology

**Active flow:** A tracked network connection identified by a **5-tuple** (source IP, destination IP, source port, destination port, and protocol) that is **not in CLOSED state** (e.g., TCP NEW or ESTABLISHED).

**Flow filter:** A set of parameters to match active flows using one or more criteria (source/destination IP, ports, protocol). One filter can match multiple flows.

**Flow capture:** A firewall operation that generates a **point-in-time snapshot** of active flows based on filter(s). Used for visibility, security analysis, and validation before flushing.

**Flow flush:** A firewall operation that removes selected active flows from the flow table based on filter(s). After flushing, subsequent packets are treated as **midstream** and re-evaluated against the **stream exception policy**.

---

## Workflow Overview (Capture/Flush)

**Inspection engine:** AWS Network Firewall uses **Suricata** for stateful inspection and maintains flow state in a **flow table**.

**Common flush scenarios:**
- **Full flush:** Clear all active flows (maintenance/troubleshooting).
- **Selective flush:** Clear targeted flows (policy updates, suspicious traffic) by IP/port/protocol.

**Operating modes:**
- **Capture → Flush:** Capture flows first, review results, then flush matched flows.
- **Direct flush:** Flush immediately using specified filters.

**Tracking:** Operation status and details can be monitored in **Firewall operation history**.

---

## Console Navigation

**Step 1:** Open **Amazon VPC console** → **Network Firewall** → **Firewalls**  
**Step 2:** Select a firewall  
**Step 3:** In **Firewall operations**, use:
- **Configure flow capture**
- **Configure flow flush**

  <img src="/images/3-Blogs/bl1-1.png" alt="Blog 1" />
<!-- 

 
> *Figure 1: Firewall operations.* -->

---

## Flow Capture

**Goal (example):** Identify active flows from `10.0.1.0/24` → `10.0.2.0/24` on **TCP port 80**, then flush them.

**Network setup:** Traffic between the two subnets is routed through AWS Network Firewall for inspection.

<img src="/images/3-Blogs/bl1-2.png" alt="Blog 2" />

<!-- > *Figure 2: Network setup.* -->

### Start capture via console

**Action:** Select **Configure flow capture** (from Figure 1).  
**Availability Zone:** Select the AZ (required per operation).  
**Required fields:** Provide at least one: **Source address** or **Destination address**.  
**Optional fields:**
- **Minimum age of flow**
- **Source port**
- **Destination port**
- **Protocol** (ICMP, TCP, UDP, IPv6-ICMP, SCTP)

**Filters:** Click **Add filter** (up to **20** filters; full or partial 5-tuple).  
**Execution:** Click **Start capture**.

**Performance note:** More specific filters usually result in faster operation times.

<img src="/images/3-Blogs/bl1-3.png" alt="Blog 3" />

<!-- > *Figure 3: Start capture operation.* -->

---

### Capture results

**Output:** The operation displays flows captured by the filter(s).


<img src="/images/3-Blogs/bl1-4.png" alt="Blog 4" />

<!-- > *Figure 4: Flow capture operation result.* -->

---

## Flow Flush

**Scope:** Flush flows based on full or partial 5-tuple filters.

### Option 1: Capture then flush

**Action:** From capture results (Figure 4), select **Configure flow flush** to reuse the same filters.  
**Execution:** Click **Start flush**.


<img src="/images/3-Blogs/bl1-5.png" alt="Blog 5" />

<!-- > *Figure 5: Start flush from previous flow capture filter.* -->

---

### Option 2: Direct flush

**Action:** From Firewall operations (Figure 1), select **Configure flow flush**.  
**Filter properties:** Configure as in capture (same filter fields).  
**Execution:** Click **Start flush**.

**Output:** After completion, flushed flows are shown.


<img src="/images/3-Blogs/bl1-6.png" alt="Blog 6" />

<!-- > *Figure 6: Flow flush operation result.* -->

---

## Verification & Logging

**Reconnect behavior:** After flows are flushed, clients typically attempt to **reconnect**. These retries appear as new flows in subsequent captures.

**Noise control:** Use **Minimum age** to avoid clutter from very recent retry flows.

**Flow logs (stateful engine):** If flow logs are enabled, log entries for flushed flows show the field `reason = flushed` and include the last state before flushing.

```json
{
  "reason": "flushed",
  "last_state": "ESTABLISHED"
}
```


<img src="/images/3-Blogs/bl1-7.png" alt="Blog 7" />

<!-- > *Figure 7: Flow logs when flow is flushed. -->
---

## Firewall Operation History

**Retention:** Shows capture/flush operations from the past **12 hours** per firewall per AZ.

**Purge:** Operations older than 12 hours are automatically removed.

**Detail view:** Click an **operation ID** to view capture/flush details.

<img src="/images/3-Blogs/bl1-8.png" alt="Blog 8" />

---

## Things to Know (Operational Notes)

**Concurrency rule:** One operation (either flow capture or flow flush) at a time per AZ per firewall.

**Multi-AZ:** If firewall endpoints are deployed in multiple AZs, operations can run **simultaneously** across AZs.

**Minimum age:** Helps identify/flush long-running flows (e.g., **300 seconds** includes flows active for 5+ minutes).

**Stream exception policy:** After a flush, packets are evaluated using the firewall policy’s **stream exception policy** (often recommended: **reject**).

**Distributed execution:** Capture/flush may vary slightly across firewall hosts because operations roll across distributed infrastructure.

**IPv4/IPv6 support:** These features support both IPv4 and IPv6 flows.

**Auditing:** AWS CloudTrail records flow capture and flush operations as **Management events**.

**Cost:** No additional cost; enabled by default.

---

## Conclusion

**Summary:** Flow capture provides point-in-time visibility into active network flows, while flow flush enables selective removal of flow state to re-apply updated security policy or isolate suspicious connections. Together, they improve monitoring, troubleshooting, incident response, and consistent policy enforcement across active connections.

---