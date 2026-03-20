# Active Directory: Implementing Group Policy Objects (GPO)

## Project Overview
This lab demonstrates the implementation of Group Policy Objects (GPOs) within a Windows Server 2022 environment. The goal was to enforce security compliance by restricting access to sensitive system settings (Control Panel) for standard domain users.

### Tools Used
* **Windows Server 2022** (Domain Controller)
* **Windows 10/11 Pro** (Target Workstation)
* **Active Directory Domain Services (AD DS)**
* **Group Policy Management Console (GPMC)**

![group policy console opened](./screenshots/group_policy_console.png)

Group Policy Management Console was opened to manage policies for the corp.local domain.

![GPO created](./screenshots/HelpDesk-ControlPanel-Restriction.png)

A new Group Policy Object was created to manage user restrictions within the domain.

![conrol policy enabled](./screenshots/control_panel_policy_enabled.png)

A Group Policy setting was configured to prohibit access to the Control Panel for domain users.

![gpu update](./screenshots/gpupdate_client.png)

The gpupdate command was used to apply the new Group Policy settings to the client machine.

![policy block test](./screenshots/policy_block_test.png)

The Control Panel restriction was successfully applied to the client machine through Group Policy.

## Conclusion
The lab successfully demonstrated the "Least Privilege" principle. By utilizing `gpupdate /force`, the policy was applied instantly, confirming that centralized administration through AD is an efficient way to manage enterprise-wide security posture.
