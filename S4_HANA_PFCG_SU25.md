## **S/4 Hana ---**



PFCG expert Mode : 3 Options



1\) Delete and recreate profile and authorizations

→ This is the Complete Regeneration option.

It wipes out the old authorization data and builds everything fresh from the role menu. Best if the role is outdated or inconsistent, but risky because it removes customizations



2\) Edit old status

→ This is the Keep Old Status option.

It leaves the existing authorizations untouched. You can manually edit them later if needed. Safe if you don’t want SAP to overwrite your tailored changes.



3\) Read old status and merge with new data

→ This is the Compare Old and New (Merge) option.

SAP reads the current authorizations and merges them with any new defaults from the role menu. This is the recommended choice when the role menu has changed, because it preserves your customizations while still updating with new objects.



Authorization objects having 4 status:

Standard - We are not changing any defaults or not maintain any open field values

Maintained - When we are maintaining the open values.

Changed - When we are changing the default values, then the object turns into Changed.



\-------------------------------------------------------------------------------------------------------------



**SU25 Steps ---**



**Step 1 – Initial Copy of SAP Defaults**

**Purpose: Copies SAP-delivered authorization proposals (from tables USOBT \& USOBX) into customer tables (USOBT\_C \& USOBX\_C).**



**Step 2 – Adjustments After Upgrade**

This is the most important phase, broken into sub-steps:



**## 2a: Automatic Comparison with SU22 Data**



**\* Purpose:** This step automatically updates your customer data tables (USOBX\_C and USOBT\_C) with new SAP standard values (USOBX and USOBT) where no conflict exists.

**\* How it works:** The system automatically accepts SAP's new default values and authorization checks only for transactions that the customer has never modified in SU24.



**## 2b: Modification Comparison with SU22 Data**



**\* Purpose:** This is a manual review step used to resolve conflicts where both SAP and the customer have modified the authorization defaults for the same transaction code.

**\* How it works:** The system displays a list of affected transactions. You must go through them and decide whether to accept the new SAP standard proposals or keep your existing custom values. 



**## 2c: Determination of Roles to Be Revised**



**\* Purpose:** This step identifies and lists every single authorization role that contains one or more transaction codes whose check indicators or values were modified in steps 2a or 2b.

**\* How it works:** It flags the affected roles with a status (typically seen as red or yellow indicators). Security administrators must edit these roles in PFCG using the "Expert Mode -> Read old status and merge with new data" option to synchronize the changes into the authorization profiles.



**## 2d: Editing of Obsolete Transactions in Role Menus**



**\* Purpose:** This step checks if the upgrade has introduced replacement transactions for any existing, obsolete transaction codes within your current role menus.

**\* How it works:** It provides a mapping layout showing old (obsolete) transaction codes alongside their new equivalents. This allows you to quickly adjust your role menus so users do not continue running deprecated codes. 



\-------------------------------------------------------------------------------------------



Step 3 – Transport Customer Tables

Purpose: Moves updated SU24 customer tables (USOBT\_CUST \& USOBX\_CUST) from Development → QA → Production.



Usage: Ensures consistency across system landscapes.



\------------------------------------------------------------------------------------------





