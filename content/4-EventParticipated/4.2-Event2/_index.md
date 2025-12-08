---
title: "Event 2"
# date: "`r Sys.Date()`"
weight: 1
chapter: false
pre: " <b> 4.2. </b> "
---

# Summary Report: “BUILDING AGENTIC AI – Context Optimization with Amazon Bedrock”

### Event Objectives

- Provide a structured journey through **Agentic AI**, from high-level architecture to hands-on implementation
- Introduce core concepts of building autonomous agents using **Amazon Bedrock**
- Share real-world use cases for **agentic workflows** on AWS
- Present approaches for **agentic orchestration** and **context optimization** (L300-level session)
- Enable practical learning through a **hands-on workshop** and expert networking opportunities

### Speakers

- **Nguyen Gia Hung** – Head of Solutions Architect
- **Kien Nguyen** – Solutions Architect
- **Viet Pham** – Founder & CEO
- **Thang Ton** – Co-Founder & COO
- **Henry Bui** – Head of Engineering
- **Kha Van** – Community Leader

### Key Highlights

#### Event overview & logistics
- **Date:** **Dec 5, 2025**
- **Location:** **26th Floor, Bitexco Financial Tower**, Ho Chi Minh City, Vietnam
- **Theme/Tagline:** Build autonomous AI agents with Amazon Bedrock through hands-on techniques and real-world use cases

#### AWS Bedrock Agent Core
- Introduced foundational building blocks for agentic systems on Bedrock:
  - Selecting the right foundation model
  - Tool / function integration to enable action-taking
  - Guardrails and constraints for safety and reliability
  - Tracing and evaluation concepts for production readiness

#### [Use Case] Building Agentic Workflow on AWS
- Demonstrated how agentic workflows can be applied to practical business/technical scenarios:
  - Multi-step task execution rather than single-turn Q&A
  - Retrieval + reasoning + action loops
  - Human-in-the-loop checkpoints for high-impact operations

#### CloudThinker Agentic Orchestration & Context Optimization (L300)
- Explained why **context quality** heavily impacts accuracy, latency, and cost
- Practical context optimization approaches:
  - Keep context minimal-but-sufficient to reduce noise and hallucinations
  - Separate short-term context vs long-term memory/knowledge
  - Use metadata filtering (scope, recency, relevance) to improve retrieval
  - Apply policies to context (allowlists, redaction, access control)

#### CloudThinker Hack: Hands-on Workshop
- Guided participants through building an agentic flow:
  - Define objective → design steps → integrate tools → test and iterate
- Focused on debugging and improving agent behavior:
  - Inspect prompts and tool calls
  - Validate retrieval results and reduce context bloat
  - Add constraints and safety checks

#### Networking & expert discussions
- Connected with experts and peers to discuss:
  - Deployment constraints (security, governance, cost control)
  - Observability (logging, tracing) and evaluation strategies
  - Integration into real engineering workflows

### Key Takeaways

#### Agentic AI mindset
- Agentic AI is more than a chatbot: it requires **orchestration**, **tool usage**, **memory**, and **guardrails**
- Context is a critical lever that determines output quality and operational cost

#### Technical approach
- Separate responsibilities clearly:
  - Planner/orchestrator vs tools/actions vs memory/retrieval vs guardrails
- Context optimization best practices:
  - Reduce irrelevant context to lower hallucination risk
  - Improve retrieval quality using filters and structure
  - Add traceability for debugging and auditability

#### Responsible deployment
- Prefer human-in-the-loop for risky operations (ops, security, deployments)
- Define success metrics (accuracy, latency, cost) and evaluate continuously

### Application to Work

- Prototype an internal agent to support:
  - Incident triage, runbook guidance, log summarization
  - Retrieval-based Q&A over internal documentation
- Apply context optimization:
  - Tighten retrieval scope and reduce prompt bloat
  - Use structured memory and validation checkpoints
- Improve governance:
  - Add guardrails for tool execution
  - Implement approval flows for critical actions
  - Enable logging/tracing for compliance and troubleshooting

### Event Experience

- The event provided a practical end-to-end view of building agentic systems, connecting architecture concepts with implementation details.
- The L300 session clarified how context optimization directly improves reliability and cost efficiency.
- The hands-on workshop reinforced best practices for designing, testing, and debugging agentic workflows.
- Networking sessions helped translate concepts into real-world constraints and adoption strategies.

#### Lessons learned
- Context quality is as important as model choice for real agent performance
- Agents must be treated like production systems: safe tool usage, auditing, and evaluation are essential
- Human-in-the-loop remains critical for high-impact autonomous actions
- Hands-on iteration (trace → diagnose → refine) is the fastest way to improve agent behavior

#### Some event photos
<img src="/images/4-Events/ev2-1.jpg" alt="Image office" />
<img src="/images/4-Events/ev2-2.jpg" alt="My face" />

