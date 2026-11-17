# KNEX Experience Overview

**Product Manager (Intern), KNEX Technology** | Jun 2025 to Aug 2025

KNEX is an Oracle Cloud Applications consultancy whose products and services sit on top of Oracle's ERP platforms. I worked directly with the CEO and the product team across AI product development, product strategy, ERP data management and product analytics. My work covered seven product lines and ran from early research all the way to two AI products that shipped.

## Impact at a Glance

* **15 AI use cases** evaluated end to end; **3 advanced** to deeper scoping and **2 greenlit** for development
* **Lease Abstraction Agent and client facing RAG chatbot shipped** from PRDs I wrote, with build time cut **45%** by choosing RAG after testing it against plain LLM extraction on 25 leases and 150 terms
* **7 product lines** brought under one prioritization framework, cutting release planning time by **25%**
* **Oracle Fusion and legacy ERP data split** diagnosed and fixed with an Airflow sync, making operations reporting **40% faster**
* **Strategic value confirmed** as the stronger predictor of on time delivery and adopted as a default planning input
* **One PRD system and one roadmap method** adopted across product teams in place of team by team formats

## Key Responsibilities

* Ran an AI feasibility study across 15 use cases and turned it into a tiered executive recommendation that leadership acted on
* Wrote the PRDs for the Lease Abstraction Agent and the client facing RAG chatbot and worked with engineering to ship both
* Mapped how KNEX products depend on Oracle NetSuite and Oracle Fusion Cloud ERP data, and used that map to judge what AI ideas were buildable
* Diagnosed a reporting conflict caused by a partial Oracle Fusion migration and built an Airflow sync that unified it with the legacy system
* Built KNEX's first cross product prioritization framework and a roadmap methodology modeled on Oracle's three tier structure
* Rebuilt PRDs into a platform agnostic, modular system tied directly to roadmap execution
* Ran a historical comparison of prioritization signals to find which one predicted on time delivery

# Projects and Contributions

## 1. Oracle ERP Landscape: NetSuite and Oracle Fusion Cloud

KNEX works across both of Oracle's ERP platforms: **NetSuite**, Oracle's cloud ERP for growing and mid sized businesses, and **Oracle Fusion Cloud ERP**, its enterprise suite. Before any AI idea or roadmap decision could be judged, I needed to understand where KNEX's data actually lived and how it moved between these systems.

### What I Did

* Studied how KNEX products connect to NetSuite and Oracle Fusion, including which modules (financials, procurement, inventory) each product reads from and writes to.
* Mapped the data each product depends on, where it originates, and where it gets stuck or duplicated across systems.
* Turned that map into the **architecture fit** and **data availability** criteria used in the AI feasibility study, so every use case was judged against the real ERP setup rather than an ideal one.
* Used the same view to flag where cross product reporting would break, which pointed directly to the Oracle Fusion migration gap covered in the next section.

### Why It Mattered

* AI and analytics ideas are only as good as the ERP data underneath them. This work kept recommendations grounded in what the systems could support today.
* It gave the product team a shared picture of the ERP layer that had previously lived in individual heads.

## 2. Oracle Fusion and Legacy ERP Data Migration Study

### The Problem

Leadership was getting different answers to the same question depending on which report they opened. One metric returned two numbers. The issue looked like a reporting bug, but the cause was in the data itself.

### What I Found

* KNEX had moved from its legacy system, **KTH**, to **Oracle Fusion**, but Oracle Fusion's migration tooling only carried over part of the historical data.
* The result was a **split history**: records from before go live stayed in KTH, records after go live lived in Oracle Fusion, and no single system held the full picture.
* Any report spanning the go live date was either incomplete or stitched together by hand, which is why the same metric disagreed across reports.
* I used SQL analysis to compare records across both systems and confirm where the split occurred and which reports it affected.

### What I Proposed and Built

* Proposed **duplicating Oracle Fusion transactions into KTH** so that one system held the complete history from both periods.
* Built the sync as an **Airflow** job that copies new Oracle Fusion transactions into KTH on a schedule.
* This kept reporting and analytics on a single source without paying for a full remigration of historical data into Oracle Fusion.
* The fix targeted the inputs rather than the report. Correcting the report alone would have left every future report open to the same conflict.

### Why It Mattered

* Restored trust in the numbers leadership used for decisions and made operations reporting **40% faster**, since nobody had to stitch two systems together by hand.
* Gave analytics one place to query instead of two systems with a gap between them.
* Taught me to treat "the report is wrong" as a question about the data before treating it as a question about the report.

## 3. AI Feasibility Study: 15 Use Case Evaluation

I led an end to end evaluation of **15 proposed AI use cases** across KNEX products. The goal was to move the team from broad AI curiosity to a short, investment ready list.

### What I Did

* Interviewed stakeholders across all 7 product lines to surface where AI could remove manual work, and consolidated scattered requests into a backlog of 15 candidates spanning automation, intelligence and integration.
* Scored every use case on a structured rubric across four dimensions:
  * **System architecture fit:** can KNEX's current stack, including its NetSuite and Oracle Fusion setup, support it, and what would have to change?
  * **Data quality and availability:** is the underlying data clean, structured and accessible enough to power the model?
  * **Integration complexity:** how many systems, APIs and workflows does it touch, and what is the risk of breakage?
  * **Cost and benefit:** what is the expected lift in time saved, accuracy or revenue against the cost to build?
* Worked with engineering leads to pressure test feasibility assumptions before anything reached leadership.
* Ranked initiatives by strategic value and readiness, then packaged them into a three tier executive recommendation: **build now, explore further, or deprioritize**, each with a one line rationale and a clear next step.

### Outcome

* **3 initiatives** advanced to deeper scoping.
* **2 were formally greenlit**: the Lease Abstraction Agent and the client facing RAG chatbot.
* Leadership left with a concrete shortlist instead of a wish list, grounded in KNEX's actual data and system limits rather than AI hype.

## 4. AI Products: From Recommendation to Build

### Lease Abstraction Agent (shipped)

* Wrote the PRD for an LLM based agent that pulls key terms out of governed lease documents, with the source clause for each, and turns them into structured, reviewable data.
* Defined the scope, extraction fields, success metrics and acceptance criteria engineering built against.
* Tested RAG against plain LLM extraction on 25 leases and 150 terms and chose RAG, which cut build time **45%**.
* Worked with engineering through the build and shipped the agent.

### Client Facing RAG Chatbot (shipped)

* Wrote the PRD for a retrieval based chatbot that lets clients ask questions in plain language and get answers fetched from governed documents, with the source cited.
* Designed it to pair with the Lease Abstraction Agent, so extracted lease data could be queried instead of read line by line.
* Shipped it with engineering, which cut inbound support questions to the team.

### Further AI Research and Scoping

* **Inventory Flow Agent:** scoped an agent for inventory tracking and forecasting across product lines, defining the data model, success metrics and specs engineers would build from.
* **AI Load Checker:** researched system load monitoring that surfaces optimization signals before performance degrades.
* **Unified Dashboard:** proposed a single leadership view of cross product utilization and performance.
* Kept every idea practical and cost aware, with a measurable outcome attached.

## 5. Cross Product Prioritization Framework

I built KNEX's **first cross product prioritization framework** in Excel, designed to be reused across all seven product lines and aligned with Oracle style decision making. The goal was prioritization that was objective, structured and easy to explain. No single model tells the whole story, so I combined three:

* **ESVF (Effort, Strategic Value, Financial Impact, Feasibility):** the quantitative backbone. Every feature got a numeric, comparable score that forced four questions: how much effort, how strongly it ties to strategy, what the financial upside is, and whether it is feasible now.
* **MoSCoW (Must, Should, Could, Won't):** a fast, intuitive lens for leadership conversations where buckets communicate better than scores.
* **RACI (Responsible, Accountable, Consulted, Informed):** closed the ownership gap that often stalls execution by making clear who drives what and tracking dependencies across teams.

### Outcome

* One shared method across 7 product lines in place of team by team judgment calls.
* **Release planning time cut by 25%.**
* Decisions became transparent for execution teams internally and for stakeholders externally.

## 6. Roadmap Methodology and Execution Sheet

### Roadmap Methodology

* Built a structured method to turn a prioritized feature list into a product roadmap.
* Adopted **Oracle's three tier roadmap structure** for external communication:
  * **Plan of Record:** committed for the immediate release
  * **Plan of Intent:** planned for the next release
  * **Plan of Direction:** long term vision
* Added an external facing version so the roadmap could be shared with clients and stakeholders without exposing internal detail.

### Roadmap Execution Sheet (Internal)

* Built a companion Excel sheet so product teams could move from roadmap to delivery step by step.
* Tracked feature status (planned, in progress, released), cross team dependencies, release timelines and milestones, and ownership.
* **Outcome:** less ambiguity between planning and delivery, and a clear line of sight from roadmap item to release.

## 7. PRD System and Product Management Enablement Plan

I created a **Product Management Enablement Plan** to give KNEX a clear, repeatable PRD system, so documentation drove execution instead of being a formality.

### What I Built

* A **modular, platform agnostic PRD template** usable across all KNEX products, modeled on Jira and Confluence best practices but built inside KNEX's own tools. It covers:
  * Problem and business context
  * User stories and acceptance criteria
  * Dependencies and risks
  * Success metrics
  * A decision log for key choices
* A step by step **enablement guide** explaining not just what to write, but why each part matters.

### How I Did It

* Audited existing documentation for gaps.
* Drafted the PRD pack and tested it in live product discussions.
* Simplified what felt heavy and clarified what was vague based on feedback from leadership and PMs.
* Linked the PRD pack to the roadmap execution sheet so specs flowed straight into delivery.

### Outcome

* **Unified:** every product team worked from the same structure.
* **Adoptable:** light enough that people used it.
* **Traceable:** strategy, roadmap and execution connected in one flow.
* **Scalable:** reusable for future KNEX products.

## 8. Prioritization Signal Study

To improve how KNEX sequenced releases, I tested which prioritization signal actually predicted on time delivery.

### What I Did

* Identified two competing philosophies in use across teams:
  * **Effort first:** tackle the heaviest builds early.
  * **Strategic value first:** ship the highest impact items first.
* Pulled historical roadmap and delivery data across product lines and tagged each release cycle by which signal dominated its planning.
* Compared on time delivery rates between the two groups, controlling for team size, scope changes and dependency blockers to isolate the effect of the planning input.

### Outcome

* **Strategic value proved the stronger predictor** of on time delivery.
* Leadership accepted the recommendation without pushback because the analysis was transparent and evidence based.
* It became a **default input for future release planning cycles.**

## Tools and Skills

* **ERP and data:** Oracle Fusion Cloud ERP, Oracle NetSuite, legacy ERP (KTH), SQL, data migration analysis, data reconciliation
* **AI product:** LLM extraction, RAG, AI feasibility and cost benefit analysis, PRD writing
* **Product management:** prioritization frameworks (ESVF, MoSCoW, RACI), roadmapping (Plan of Record, Intent, Direction), stakeholder interviews, executive communication
* **Tools:** Excel, Airflow, Jira and Confluence practices

## What I Took Away

* **Fix inputs before outputs.** The biggest reporting problem I found was not in the report at all. It was in how two ERP systems split one company's history.
* **Feasibility beats enthusiasm.** Scoring AI ideas against real architecture and real data is what turned 15 ideas into 2 that got built.
* **Frameworks only work if people use them.** The PRD system and prioritization framework stuck because I tested them in live discussions and cut what felt heavy.
* **Working with a CEO compresses learning.** Every recommendation had to hold up to a direct question about cost, risk and impact, which shaped how I build every case since.
