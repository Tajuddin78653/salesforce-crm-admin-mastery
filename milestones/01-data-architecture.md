# 🏛️ Milestone 1: Data Architecture & Schema Design

## 🎯 Goal
Understand Salesforce foundational data structure and build the custom data model for the **CloudNest Property Management System**.

---

## 📚 Core Administrator Concepts

### 1. Standard Objects vs. Custom Objects
- **Standard Objects**: Built into Salesforce by default (\Account\, \Contact\, \Opportunity\, \Lead\, \Case\).
- **Custom Objects**: Custom database tables you create for your unique business needs (end with \__c\, e.g., \Property__c\).

### 2. Relationship Types
| Relationship | Characteristics | Example in CloudNest |
| :--- | :--- | :--- |
| **Lookup Relationship** | Loosely coupled. Child record can exist without parent. No cascade delete. Up to 40 lookups per object. | \Property__c\ to \Account\ (Property Owner) |
| **Master-Detail Relationship** | Tightly coupled. Child record cannot exist without parent. Parent deletion deletes child (cascade delete). Enables **Roll-up Summary fields**. Max 2 per object. | \Lease_Agreement__c\ (Detail) to \Property__c\ (Master) |

---

## 🛠️ Hands-On Build Specification

### Object 1: \Property__c\ (Custom Object)
- **Label**: Property
- **Plural Label**: Properties
- **Record Name**: Auto-Number \PROP-{0000}\
- **Fields to Create**:
  1. \Property_Name__c\ (Text, 100, Required)
  2. \Property_Type__c\ (Picklist: Single Family, Multi-Family, Apartment, Commercial)
  3. \Status__c\ (Picklist: Available, Leased, Maintenance, Off Market)
  4. \Monthly_Rent__c\ (Currency 16, 2)
  5. \Square_Footage__c\ (Number 10, 0)
  6. \Owner_Account__c\ (Lookup to \Account\)
  7. \Total_Leases_Count__c\ (Roll-Up Summary: COUNT of Lease Agreements)

### Object 2: \Lease_Agreement__c\ (Custom Object)
- **Label**: Lease Agreement
- **Plural Label**: Lease Agreements
- **Record Name**: Auto-Number \LEASE-{0000}\
- **Fields to Create**:
  1. \Property__c\ (Master-Detail to \Property__c\, Required)
  2. \Tenant__c\ (Lookup to \Contact\, Required)
  3. \Start_Date__c\ (Date, Required)
  4. \End_Date__c\ (Date, Required)
  5. \Monthly_Rent__c\ (Currency 16, 2, Required)
  6. \Security_Deposit__c\ (Currency 16, 2)
  7. \Status__c\ (Picklist: Draft, Active, Terminated, Expired)

---

## 📝 Practice Exercises & Quiz
1. What happens if a Property with 3 Lease Agreements is deleted in a Master-Detail relationship?
2. If you need to calculate the total rent across all active leases on a Property, what field type should you use?