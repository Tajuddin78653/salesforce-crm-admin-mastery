# ☁️ Salesforce CRM Administrator Mastery - Hands-On Learning Path

Welcome to the **Salesforce CRM Administrator Project & Learning Path**! This repository is designed for beginners to build foundational knowledge, hands-on admin skills, and portfolio-ready projects aligned with the **Salesforce Certified Administrator (ADM-201)** curriculum.

---

## 🎯 Capstone Learning Project: *CloudNest Property & Tenant Management System*
Throughout this repository, we build an end-to-end real-world CRM solution for **CloudNest Properties**, a property management firm tracking properties, lease contracts, tenant applications, and maintenance cases.

---

## 🗺️ Curriculum & Milestones

| Milestone | Core Concepts Covered | Deliverables & Artifacts |
| :--- | :--- | :--- |
| **[Milestone 1: Data Architecture](./milestones/01-data-architecture.md)** | Standard vs Custom Objects, Fields, Lookups, Master-Detail, Schema Builder | Data Dictionary, Object Schema, ERD Diagrams |
| **[Milestone 2: Security & Access Control](./milestones/02-security-and-access.md)** | Org-Wide Defaults (OWD), Profiles, Permission Sets, Role Hierarchy, Sharing Rules | Security Matrix, User Access Design |
| **[Milestone 3: Declarative Automation](./milestones/03-business-automation.md)** | Record-Triggered Flows, Validation Rules, Approval Processes, Formula Fields | Automation Flowcharts, Formulas, Validation Logic |
| **[Milestone 4: Sales & Service Cloud](./milestones/04-sales-and-service-cloud.md)** | Lead Lifecycle, Opportunity Stages, Case Escalations, Web-to-Lead/Web-to-Case | End-to-End Sales & Support Process Maps |
| **[Milestone 5: Analytics & Dashboards](./milestones/05-reports-and-dashboards.md)** | Summary & Matrix Reports, Lightning Dashboards, KPI Tracking | Executive Dashboard Specifications |

---

## 🏗️ Project Architecture (CloudNest ERD)

\\\mermaid
erDiagram
    ACCOUNT ||--o{ PROPERTY : owns
    PROPERTY ||--o{ LEASE_AGREEMENT : has
    CONTACT ||--o{ LEASE_AGREEMENT : signs
    PROPERTY ||--o{ MAINTENANCE_CASE : logs
    MAINTENANCE_CASE ||--o{ CASE_COMMENT : includes

    PROPERTY {
        string Name PK
        string Property_Type__c
        currency Monthly_Rent__c
        string Address__c
        string Status__c
    }

    LEASE_AGREEMENT {
        string Name PK
        date Start_Date__c
        date End_Date__c
        currency Rent_Amount__c
        string Status__c
    }

    MAINTENANCE_CASE {
        string CaseNumber PK
        string Priority
        string Status
        string Issue_Category__c
    }
\\\

---

## 🛠️ How to Follow Along
1. Open your Salesforce Developer Edition Org or Trailhead Playground.
2. Follow each milestone document under the \milestones/\ folder step-by-step.
3. Verify requirements, build fields/flows, and test live in your org.