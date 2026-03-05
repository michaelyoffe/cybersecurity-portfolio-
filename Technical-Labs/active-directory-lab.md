# Active Directory Home Lab

## Overview
Built a Windows Server Active Directory lab to simulate a real corporate environment.
Configured a domain controller, DNS, and a domain-joined client workstation to practice common help desk and IT support tasks.

## Lab Architecture
* **DC01** — Domain Controller
* Static IP
* DNS configured
* Active Directory Domain Services installed
* **CLIENT01** — Domain-joined workstation
* Internal network
* DNS pointing to DC01

## Technologies & Tools
* **Virtulization:** VirtualBox
* **Operating Systems:** Windows Server 2022 (Domain Controller), Windows 11 (Client Workstation)
* **Services:** AD DS (Active Directory Domain Services), DNS, DHCP
* **Domain:** corp.local 

## Configuration Steps
1. Installed Windows Server on DC01
2. Set static IP and DNS
3. Installed and configured Active Directory Domain Services
4. Created domain corp.local
5. Created Organizational Unit and test user
6. Installed Windows 11 on CLIENT01
7. Joined CLIENT01 to the domain
8. Verified domain authentication

## Help Desk Scenarios Tested
* Created and managed domain user accounts
* Disabled and re-enabled user accounts
* Reset user passwords
* Forced password change at next logon
* Tested login behavior from domain-joined client

## Key Milestones
* Active Directory user and OU management
* DNS configuration and troubleshooting
* Domain join troubleshooting
* Virtual networking (internal networks)
* Windows Server administration
* Tier 1 help desk workflows

## Screenshots & Evidence

### 1. User & OU Management
*Demonstrating the creation of organizational structures and account security workflows.*

| Action: Create OU & User | Action: Disable Account | Verification: Login Denied |
| :--- | :--- | :--- |
| ![ad users](./screenshots/ad-users-ou.png) | ![user disabled](./screenshots/user-disabled.png) | ![disabled login](./screenshots/disabled-login-failure.png) |
| **Setup:** Created `helpdesk-users` OU and a test account in ADUC. | **Security:** Simulating an administrative lock on a user account. | **Result:** Client-side confirmation that the disabled account cannot authenticate. |

---

### 2. Domain Connectivity
*Confirming successful integration between the Windows 11 Client and the Server 2022 Domain Controller.*

| Successful Domain Login | System Verification |
| :--- | :--- |
| ![domain login](./screenshots/domain-login-success.png) | ![client domain](./screenshots/client-domain-joined.png) |
| **Authentication:** Logging into the workstation using domain credentials. | **Identity:** System properties confirming `CLIENT01` is a member of `corp.local`. |

---

### 3. Network Configuration & Troubleshooting
*Ensuring the foundational networking (Static IP and DNS) is correctly configured for AD stability.*

| Static IP Configuration (DC) | Connectivity Test (ICMP) |
| :--- | :--- |
| ![DC01 static](./screenshots/dc01-static-ip.png) | ![ping DC01](./screenshots/ping-dc01.png) |
| **Configuration:** DC01 assigned a static IP and DNS to prevent domain drops. | **Testing:** Successful ping from Client to DC verifying DNS resolution. |
