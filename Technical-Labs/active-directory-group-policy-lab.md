# Active Directory: Implementing Group Policy Objects (GPO)

## Overview 
In an enterprise environment, allowing standard users access to system configuration tools like the **Control Panel** or **Command Prompt** poses a significant security risk. Unauthorized changes can lead to system instability, disabled security software, or the introduction of shadow IT. 

**Objective:** Implement the **Principle of Least Privilege (PoLP)** by creating and enforcing a Group Policy Object (GPO) that restricts Control Panel access for all non-administrative users in the `corp.local` domain.

### Tools Used
* **Windows Server 2022 (Domain Controller)**
* **Windows 11**
* **Active Directory Domain Services (AD DS)**
* **Group Policy Management Console (GPMC)**

### Policy Configuration Details
| Setting Name | Path | Value | Target OU |
| :--- | :--- | :--- | :--- |
| **Prohibit access to Control Panel** | User Configuration > Administrative Templates > Control Panel | **Enabled** | Users / Helpdesk |
| **Enforcement Method** | Group Policy Management Console (GPMC) | **GPO Link** | corp.local |

---

### Step 1: group policy console opened 
![group policy console opened](./screenshots/group_policy_console.png)

Initializing the Group Policy Management Console (GPMC) on the Domain Controller to audit and manage the hierarchical policy structure for the corp.local infrastructure.

---

### Step 2: new group policy object created 
![GPO created](./screenshots/HelpDesk-ControlPanel-Restriction.png)

Generating a targeted Group Policy Object (GPO) specifically for workstation restrictions, ensuring modularity so the policy can be linked or unlinked without affecting other domain settings.

---

### Step 3: Control policy enabled 
![conrol policy enabled](./screenshots/control_panel_policy_enabled.png)

Navigating to User Configuration > Administrative Templates to enforce the 'Prohibit access to Control Panel' setting, effectively disabling control.exe and system settings access for non-admin users.

---

### Step 4: Ran gpu update command 
![gpu update](./screenshots/gpupdate_client.png)

Executing gpupdate /force on the endpoint to trigger an immediate policy refresh, bypassing the default 90-minute background interval to ensure the security control is active instantly.

---

### Step 5: Policy block tested 
![policy block test](./screenshots/policy_block_test.png)

Verifying the Principle of Least Privilege from a standard user session. The system successfully intercepts the request, confirming that the GPO is correctly filtered and enforced.

---

## Conclusion
The lab successfully demonstrated the "Least Privilege" principle. By utilizing gpupdate /force, the policy was applied instantly, confirming that centralized administration through AD is an efficient way to manage enterprise-wide security posture.
