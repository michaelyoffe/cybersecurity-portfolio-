# Active Directory: Implementing Group Policy Objects (GPO)

## Scenario
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

![group policy console opened](./screenshots/group_policy_console.png)

Group Policy Management Console was opened to manage policies for the corp.local domain.

![GPO created](./screenshots/HelpDesk-ControlPanel-Restriction.png)

A new Group Policy Object was created to manage user restrictions within the domain.

![conrol policy enabled](./screenshots/control_panel_policy_enabled.png)

A Group Policy setting was configured to prohibit access to the Control Panel for domain users.

![gpu update](./screenshots/gpupdate_client.png)

The gpupdate command was used to apply the new Group Policy settings to the client machine.

### Verification
To ensure the policy was applied correctly, I performed the following steps on the **Windows 11 Client**:
1.  **Command Line:** Ran `gpresult /r` to confirm the "Restrict Control Panel" GPO was listed under *Applied Group Policy Objects*.
2.  **Manual Test:** Attempted to open the Control Panel from the Start Menu.
3.  **Result:** The system triggered a restriction alert: *"This operation has been cancelled due to restrictions in effect on this computer."*

![policy block test](./screenshots/policy_block_test.png)

The Control Panel restriction was successfully applied to the client machine through Group Policy.

## Future Security Hardening
While restricting the Control Panel is a vital first step, a fully hardened Active Directory environment should also include:
- [ ] **Account Lockout Policy:** Prevent brute-force attacks by locking accounts after 5 failed attempts.
- [ ] **Disable CMD/PowerShell:** Restrict access for standard users to prevent script-based attacks.
- [ ] **Interactive Logon Banner:** Display a legal warning at the sign-in screen to deter unauthorized access.
- [ ] **AppLocker:** Implement application whitelisting to prevent unapproved software from running.

## Conclusion
The lab successfully demonstrated the "Least Privilege" principle. By utilizing `gpupdate /force`, the policy was applied instantly, confirming that centralized administration through AD is an efficient way to manage enterprise-wide security posture.
