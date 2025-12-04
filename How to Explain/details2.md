Great! I’ve received **Part 2** and I’ll wait for the remaining parts before producing the final:
✅ Mind maps
✅ Flow diagrams
✅ Cheat sheets
✅ Visual diagrams & summaries

I will not generate them until you say **“DONE.”**

Below is a **simple, clear summary** of Part 2, so you stay aligned before we build the final consolidated version.

---

# **📘 SIMPLE NOTES – Part 2: Data & Entitlements Layer**

The **Data & Entitlements Layer** is the “heart” of ULM’s data model.
It defines *who a user is*, *what they can access*, and *how everything is related*.

It has **four major building blocks**:

---

# **1. ULM Core Data Entities**

These are the basic pieces that represent everything ULM manages.

### **The key entities are:**

| Entity           | Meaning                                                                   |
| ---------------- | ------------------------------------------------------------------------- |
| **User**         | A person with a digital identity                                          |
| **Group**        | A collection of users (family, business unit, team)                       |
| **Membership**   | The exact services/features a user gets inside a group                    |
| **Runtime**      | A physical device (phone, TV box, tablet)                                 |
| **Account**      | Billing or service account                                                |
| **Subscription** | A service within the account (Internet, TV, VoIP)                         |
| **Feature**      | A small function within a subscription (VOD, Voicemail, Parental Control) |

### Important notes:

* ULM stores each entity in its **own database table**.
* Core schema is **not modified**; custom attributes go into extension tables.
* ULM creates a **user-centric overlay** on top of legacy backend systems (BSS/OSS).
* Many-to-many relationships allow lots of flexibility.

---

# **2. ULM Entity Associations**

Associations define **relationships** between entities.

Example relationships:

* User ↔ Group
* User ↔ Account
* User ↔ Subscription
* User ↔ Feature
* Device (Runtime) ↔ User

Associations also contain:

* **Attributes** (extra data)
* **Flags** (status indicators — e.g., disabledByUser: true)

Associations are the backbone of:

* Identity federation
* Entitlement mapping
* Self-discovery in the Service Gateway

---

# **3. ULM Entity Attributes**

Each entity (User, Account, Group, etc.) can have additional data attached.

Types of attributes:

1. **Pre-defined (out-of-the-box)**
2. **Custom (extendable)**

These allow business customizations *without* changing the core product.

Examples:

* User attributes → parental control rating, avatar URL, language preference
* Account attributes → region, account type, billing preferences

Attributes help process flows make decisions.

---

# **4. ULM Business Parameters**

Global configuration settings that help:

* Configure ULM behavior
* Support operator-specific rules
* Override defaults when no entity attribute exists

Properties:

* Configured via **REST API**
* Returned as **JSON**
* Define visibility scope (system level, service level, provider level)

Used for:

* Business logic in processes
* Provider integrations
* Third-party SAM & legacy system alignment

---

# **Detailed Breakdown of Each Core Entity**

## **A. User & Group Management**

### **User**

* Central identity
* Stored with a unique, system-generated ID
* Supports social login identities
* Supports uploading avatar images through the secure file upload service
* Operator-defined custom attributes allowed

### **Group**

* Collection of Users, Accounts, Subscriptions, Devices
* Used for:

  * Households
  * Business units
  * Shared service environments
* Users can belong to multiple groups
* Role-based:

  * Primary User
  * Administrator
  * Sub-user

---

## **B. Membership Management**

Membership defines:

* What services, subscriptions, and features a user can access **inside a group**.

Key differences from Groups:

| Group                           | Membership                    |
| ------------------------------- | ----------------------------- |
| Organizes Users & Resources     | Defines actual entitlements   |
| Structural (household/business) | Permission-based              |
| Holds Users & ASF entities      | Grants access to ASF entities |

Important in **B2B** environment:

* Users need different access per business unit
* Membership controls their permissions

---

## **C. Runtime Management (Device Management)**

Runtime = device endpoint where services are used.

ULM manages:

* Device attributes (name, OS version, capabilities)
* Device status (connected/not connected)
* Device limits (max devices per user/account/subscription)

APIs exist for full device lifecycle:

* Register
* Update
* Remove
* Associate with user

---

## **D. ASF Management (Account, Subscription, Feature)**

ULM manages all service-related data:

* **Account** → Billing account
* **Subscription** → Service (Internet, TV, Phone)
* **Feature** → Small unit of a service (VOD, Call Forwarding)

ULM responsibilities:

* Create and maintain ASF entities
* Assign unique internal IDs
* Store extra attributes
* Enforce attribute whitelist (security)

**Provisioning Interface**
ULM exposes REST APIs for BSS/OSS systems to create/update user and service entities.

---

## **E. Association Management**

Associations:

* Represent relationships between entities
* Have flags that give context
* Are manipulated by ULM processes
* Crucial for entitlement decisions

Example flag:

* **"mintEnabledByUser": true/false**

---

# **Everything Together (Simplified)**

ULM Data & Entitlements Layer is responsible for:

* Defining all fundamental entities
* Connecting them through flexible associations
* Giving users personalized access
* Managing devices
* Managing subscriptions
* Adding custom business-driven attributes
* Applying business rules and defaults
* Supporting clean integration with BSS/OSS and third-party services

This is the foundational data layer that the rest of ULM uses.

---

Whenever you're ready, please share **Part 3**, and I’ll continue.
