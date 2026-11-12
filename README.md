# Active Directory Group Policy Objects (GPOs) & Server Hardening Lab (`ETHA.com`)

## 📌 Project Overview
This repository documents the implementation of advanced Group Policy administration, including the creation of a Central Store for administrative templates (`PolicyDefinitions`), Starter GPOs, security baseline hardening for member servers, User Rights Assignments, User Account Control (UAC) configuration, and client restrictions via Organizational Unit (OU) linking.

## 🏗️ Environment Architecture
* **Domain Controller:** `STO-DC1` (`ETHA.com`)
* **Member Servers & Workstations:** `STO-CORE`, `STO-SVR1`, `STO-CL1`
* **Core Management Tools:** Group Policy Management Console (GPMC), PowerShell (`gpupdate /force`)
* **Domain Functional Level:** Windows Server 2025

---

## ⚙️ Key Tasks & Technical Implementation

### 1. Group Policy Central Store Deployment
* Created and configured a central **PolicyDefinitions** store in the `SYSVOL` directory (`\\ETHA.com\SYSVOL\ETHA.com\Policies\PolicyDefinitions`)[cite: 3].
* Populated the Central Store with centralized ADMX administrative template definitions and verified replication across domain controllers via GPMC[cite: 3].

### 2. Starter GPOs & Custom Policies
* Created custom **Starter GPOs** (e.g., `Starter_GPO_Internet_Explorer_Restrictions`) to standardize policy baselines[cite: 3].
* Configured administrative template filters and implemented user settings to disable and hide browser configuration tabs[cite: 3].

### 3. Member Server Hardening & Security Settings
* Established a dedicated `Member Servers` OU and migrated server objects (`STO-CORE`, `STO-SVR1`) into it[cite: 3].
* Linked a targeted **Member Server Security Settings** GPO to enforce local group restrictions (`Administrators` configured to include `Domain Admins` and custom `Server Administrators`)[cite: 3].
* Configured local security policies for **User Rights Assignment** (restricting interactive logons) and enforced **User Account Control (UAC)** Admin Approval Mode for the built-in Administrator account[cite: 3].

### 4. Client Control Panel Restrictions & Security Filtering
* Deployed user-level restrictions via GPO (`NoControlPanelAccess`) linked directly to the `Sales` OU to prohibit access to system settings and Control Panel items[cite: 3].
* Validated security filtering and exemptions to ensure appropriate administrative access for IT personnel[cite: 3].
