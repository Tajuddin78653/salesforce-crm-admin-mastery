# 🔐 Milestone 2: Security & Access Control Model

## 🎯 Goal
Master Salesforce's 4-layer security architecture (Object, Field, Record, and Organization level) and configure strict access controls for **CloudNest Properties**.

---

## 🏛️ The 4 Layers of Salesforce Security

\\\mermaid
flowchart TD
    subgraph Layer1 [1. Organization-Level Security]
        A[IP Ranges & Login Hours]
    end
    subgraph Layer2 [2. Object & Field-Level Security]
        B[Profiles & Permission Sets]
    end
    subgraph Layer3 [3. Record-Level Security: Baseline]
        C[Organization-Wide Defaults - OWD]
    end
    subgraph Layer4 [4. Record-Level Security: Exceptions/Open Up]
        D[Role Hierarchy] --> E[Sharing Rules] --> F[Manual Sharing]
    end
    Layer1 --> Layer2 --> Layer3 --> Layer4
\\\

---

## 📚 Core Security Concepts

### 1. Object & Field-Level (CRED & FLS)
- **Profiles**: Baseline permissions assigned to a user (1 profile per user).
- **Permission Sets**: Add-on permissions granted to specific users without altering their profile (many per user).
- **Rule of Thumb**: Grant baseline access via Profiles; extend specific privileges via Permission Sets.

### 2. Record-Level Security
- **Organization-Wide Defaults (OWD)**: The most restrictive baseline for record visibility (*Private*, *Public Read Only*, *Public Read/Write*).
- **Role Hierarchy**: Automatically opens record access upwards to managers and executives.
- **Sharing Rules**: Rule-based exceptions to open access horizontally across roles or public groups.

---

## 🛠️ Hands-On Build Specification

### Task 2.1: Configure Org-Wide Defaults (OWD)
- Set \Property__c\ to **Public Read Only** (All internal agents can view properties, but only the property owner/manager can edit).
- Notice that \Lease_Agreement__c\ is **Controlled by Parent** (Inherited automatically from \Property__c\ because of the Master-Detail relationship!).

### Task 2.2: Create a Permission Set: \Property Manager\
- **Label**: \Property Manager\
- **Object Permissions**:
  - \Property\: Read, Create, Edit, Delete (Full CRUD)
  - \Lease Agreement\: Read, Create, Edit, Delete (Full CRUD)
- **Field-Level Security (FLS)**:
  - Edit access to all financial fields (\Monthly_Rent__c\, \Rent_Amount__c\, \Security_Deposit__c\).