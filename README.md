# Active-Directory-Lab
A hands‑on Active Directory lab demonstrating domain setup, OU design, user/group management, delegated permissions, and Help Desk RBAC validation.

## 📌 Overview
This project simulates a realistic enterprise Active Directory environment.  
It includes domain creation, organizational structure, user and group management, delegated permissions, Group Policy configuration, and least‑privilege RBAC testing.

## 🧰 Tools Used

### Virtualization & Environment
- **VirtualBox** – Virtualization platform for hosting the lab environment  
- **Windows Server 2022** – Domain Controller and AD DS host  
- **Windows 10** – Domain‑joined client workstation  

### Active Directory & Management
- **Active Directory Domain Services (AD DS)**  
- **Active Directory Users and Computers (ADUC)**  
- **Group Policy Management Console (GPMC)**  
- **DNS Manager**  
- **Local Users and Groups** (client-side validation)

### Networking & System Configuration
- **Static IPv4 configuration**  
- **Hostname and domain configuration**  
- **gpupdate /force** for policy refresh  
- **Event Viewer** (optional troubleshooting)

### Documentation & Workflow
- **GitHub** – Project hosting and version control  
- **Markdown** – Clean, readable documentation  
- **Screenshots** – Visual validation of each step  

## 🛠️ Skills Demonstrated
- Active Directory Domain Services (AD DS)
- Organizational Unit (OU) design
- User and group management
- Delegated permissions
- Group Policy
- RBAC (Role-Based Access Control)
- Least privilege enforcement
- Documentation and troubleshooting

## 🖥️ Lab Diagram
+---------------------------+
|     Windows Server 2022   |
|   Domain Controller (DC)  |
|---------------------------|
| - AD DS                   |
| - DNS                     |
| - GPMC                    |
| - OU Structure            |
+---------------------------+
              |
              |  Domain: jose-lab.local
              |
+---------------------------+
|     Windows 10 Client     |
|   Domain-Joined Workstation|
|---------------------------|
| - User Login              |
| - GPO Applied             |
| - Help Desk Testing       |
+---------------------------+

## 🧱 Lab Structure
The project is organized into the following sections:

1. Server Installation  
2. Static Configuration  
3. AD Installation  
4. Domain Controller Promotion  
5. Domain Join  
6. Domain Users  
7. OU Structure  
8. Object Placement  
9. Security Groups  
10. GPO Desktop Wallpaper  
11. Help Desk Testing  

Each section includes screenshots and explanations.

## 📸 Screenshots & Documentation
Screenshots for each step are stored in their corresponding folders.

---

## 01 – Server Installation

This section documents the installation of Windows Server 2022, which serves as the foundation for the entire Active Directory environment. The goal of this step is to deploy a clean, stable server instance that will later be promoted to a Domain Controller. This includes selecting the correct edition, configuring initial settings, and preparing the system for domain services.
### [01 Server Installation](01%20Server%20Installation/)
Initial installation of Windows Server 2022.

### Screenshot 01A – server rename
This screenshot shows the successful installation of Windows Server 2022. At this stage, the operating system is fully deployed and ready for post‑installation configuration, including setting the administrator password, applying updates, and preparing the server for static IP assignment and AD DS installation.

## 02 – Static Configuration

This section covers the initial post‑installation configuration of the server, focusing on assigning a static IPv4 address. A Domain Controller must always have a fixed, unchanging IP so that domain‑joined clients can reliably locate it through DNS. This step ensures the server is ready for Active Directory Domain Services installation and domain controller promotion.

### Screenshot 02A – Static IP Configuration
This screenshot shows the server’s network adapter being configured with a static IPv4 address. The IP address, subnet mask, gateway, and DNS settings are manually assigned to ensure consistent network identity. Setting the preferred DNS server to the local machine prepares the server for hosting DNS once AD DS is installed. This configuration establishes the foundation for stable domain communication.
### [02 Static Configuration](02%20Static%20Configuration/)
Static IPv4 configuration for the domain controller.

## 03 – AD DS Installation

In this step, the Active Directory Domain Services (AD DS) role is installed on the server. This role provides the core directory services required for authentication, authorization, and centralized management of users, computers, and security policies. Installing AD DS prepares the server for promotion to a Domain Controller, which will become the central authority of the environment.

### Screenshot 03A – AD DS Role Installation in Progress
This screenshot shows the Add Roles and Features Wizard actively installing the AD DS role and its associated management tools on the server LAB-DC01. Components such as Group Policy Management, the Active Directory Administrative Center, AD DS Snap‑Ins, and the AD PowerShell module are being deployed. This progress screen confirms that the server is receiving all required directory service components. Once the installation completes, Server Manager will display the “Promote this server to a domain controller” notification, signaling readiness for domain controller promotion.
### [03 AD Installation](03%20AD%20Installation/)
Installation of the Active Directory Domain Services role.

## 04 – Domain Controller Promotion

With the AD DS role installed, the next step is to promote the server to a Domain Controller. This process creates the first domain in the forest, establishes the directory database, configures DNS integration, and sets the foundation for authentication and authorization across the environment. The Domain Controller Promotion wizard allows you to define critical settings such as the domain name, forest functional level, and Directory Services Restore Mode (DSRM) password.

### Screenshot 04A – Domain Controller Promotion Options
This screenshot shows the Domain Controller Options page during the promotion process. Here, key configuration choices are made, including selecting the forest and domain functional levels, enabling DNS server integration, and specifying the Directory Services Restore Mode (DSRM) password. These settings determine the capabilities and security posture of the domain. Completing this step prepares the server to finalize promotion and reboot as the first Domain Controller in the environment.
### [04 Domain Controller Promotion](04%20Domain%20Controller%20Promotion/)
Promotion of the server to a Domain Controller.

## 05 – Domain Join

In this step, the Windows 10 client machine is joined to the newly created Active Directory domain. Joining a workstation to the domain allows centralized authentication, policy enforcement, and management through Group Policy and AD DS. This step validates that DNS, networking, and domain controller services are functioning correctly.

### Screenshot 05A – Domain Join Success
This screenshot captures the confirmation dialog indicating a successful join to the domain *solorzano.local*. This message verifies that the workstation was able to locate the Domain Controller, authenticate the provided credentials, and register itself in Active Directory. A reboot is required to complete the domain join process and apply domain policies.

### Screenshot 05B – Domain Login Screen
This screenshot shows the Windows login screen after reboot, now displaying the option to sign in to the **SOLORZANO** domain. This confirms that the workstation recognizes the domain and is ready for domain-based authentication. At this stage, domain users can log in, and the machine is fully integrated into the Active Directory environment.
### [05 Domain Join](05%20Domain%20Join/)
Joining the Windows 10 client to the domain and verifying login.

## 06 – Domain Users

This section documents the creation of the first domain user account within Active Directory. User accounts are essential for authentication, authorization, and access control across the domain. Creating a standard domain user validates that the domain controller, AD DS tools, and organizational structure are functioning correctly.

### Screenshot 06A – First Domain User Created
This screenshot shows the newly created domain user within the Active Directory Users and Computers (ADUC) console. The account appears in the appropriate container, confirming that the user object was successfully created and registered in the domain. This step establishes the foundation for identity management, enabling domain logins, group membership assignments, and future RBAC testing.
### [06 Domain Users](06%20Domain%20Users/)
Creation of the first domain user account.

## 07 – OU Structure

This section documents the creation of a clean and scalable Organizational Unit (OU) structure within Active Directory. A well‑designed OU hierarchy is essential for applying Group Policies, delegating permissions, and maintaining long‑term manageability in an enterprise environment. The structure created here follows a logical, professional naming convention that supports clarity and future growth.

### Screenshot 07A – OU Structure Created
This screenshot shows the newly created OU structure within the Active Directory Users and Computers (ADUC) console. Custom OUs such as *Admins*, *Users*, *Computers*, *Groups*, and *Service Accounts* are organized under the domain root. This layout separates administrative objects from standard users and machines, enabling targeted Group Policy application and proper delegation of permissions. The structure reflects real‑world best practices for domain organization.
### [07 OU Structure](07%20OU%20Structure/)
Creation of a clean and scalable Organizational Unit structure.

## 08 – Object Placement

With the OU structure created, the next step is to place domain objects into their appropriate Organizational Units. Proper object placement is essential for applying targeted Group Policies, delegating permissions, and maintaining a clean, scalable Active Directory environment. This step ensures that users and computers are organized according to best practices rather than remaining in the default built‑in containers.

### Screenshot 08A – Computer in Computers OU
This screenshot shows the domain‑joined workstation moved from the default **Computers** container into the custom **03 – Computers** OU. Relocating the computer object allows for proper Group Policy application and ensures the machine is managed according to organizational standards.

### Screenshot 08B – User in Users OU
This screenshot displays the first domain user placed inside the **02 – Users** OU. Moving the account out of the built‑in **Users** container enables cleaner administration, targeted policy assignment, and future delegation of permissions. This placement reflects real‑world identity management practices.

### [08 Object Placement](08%20Object%20Placement/)
Placing users and computers into their appropriate OUs.

## 09 – Security Groups

Security groups are essential for managing permissions, access control, and role‑based administration within Active Directory. Instead of assigning permissions directly to individual users, groups allow scalable, maintainable, and secure access management. Creating a dedicated group also prepares the environment for future RBAC testing and delegated administration.

### Screenshot 09A – First Security Group Created
This screenshot shows the creation of the first security group within the **04 – Groups** OU. The group is configured as a **Global Security Group**, which is the standard scope for assigning permissions to users within the same domain. This group will later be used to manage access, apply role‑based permissions, and support Help Desk RBAC testing. Its creation marks the beginning of structured, principle‑driven access control in the domain.
### [09 Security Groups](09%20Security%20Groups/)
Creation of the first security group for RBAC.

## 10 – GPO: Desktop Wallpaper

This section documents the creation and application of a Group Policy Object (GPO) used to deploy a custom desktop wallpaper across domain users. This demonstrates the ability to configure User Configuration policies, link GPOs to the correct Organizational Unit, and validate successful policy application on a domain‑joined workstation.

### Screenshot 10A – GPO Settings (Desktop Wallpaper Policy)
This screenshot shows the configuration of the Desktop Wallpaper policy within the Group Policy Management Editor. The setting is enabled under **User Configuration → Policies → Administrative Templates → Desktop → Desktop**, with the wallpaper path pointing to a shared network location. The wallpaper style is set to *Fill*, ensuring consistent display across different screen resolutions. This configuration prepares the policy for deployment to all users within the **02 – Users** OU.

### Screenshot 10B – Wallpaper Applied on Domain Workstation
This screenshot confirms that the GPO successfully applied to the domain‑joined workstation. The custom wallpaper is visible on the user’s desktop after running `gpupdate /force` and logging back in. This validates that the GPO is correctly linked, the user is in the proper OU, and the policy is being processed through User Configuration as intended.
### [10 GPO Desktop Wallpaper](10%20GPO%20Desktop%20Wallpaper/)
Configuration and validation of a desktop wallpaper GPO.

## 11 – Help Desk Denied Action

This section demonstrates the enforcement of least‑privilege access for the Help Desk role. After delegating limited permissions to the Help Desk security group, the next step is to verify that restricted actions are properly blocked. Testing denied actions ensures that the RBAC configuration is secure, realistic, and aligned with enterprise best practices.

### Screenshot 11A – Help Desk Denied Action
This screenshot shows the Help Desk user attempting an action outside their delegated permissions—such as creating, deleting, or modifying protected objects—and receiving an “Access Denied” message. This confirms that the Help Desk role is correctly restricted and cannot perform administrative tasks reserved for higher‑privilege roles. The denied action validates that least‑privilege enforcement is functioning exactly as intended.
### [11 Help Desk Testing](11%20Help%20Desk%20Testing/)
Validation of least‑privilege enforcement for the Help Desk role.

---

## 🔐 RBAC Validation Summary  
A Help Desk role was created and tested to ensure proper least-privilege access.  
The Help Desk user can:

✔ View user properties  
✔ Modify group membership  
✔ Reset passwords (if delegated)  
✔ Unlock accounts (if delegated)  

The Help Desk user cannot:

❌ Create users  
❌ Delete users  
❌ Modify OUs  
❌ Modify GPOs  
❌ Perform domain-level administrative tasks  

This demonstrates a secure and realistic RBAC implementation.

---

## 🧠 What I Learned  
- How to design a clean and scalable OU structure  
- How to create and manage users and groups  
- How to delegate permissions safely  
- How to enforce least privilege  
- How to validate RBAC using allowed/denied actions  
- How to document technical work professionally  

---

## 📂 Project Files  
All screenshots and documentation are organized in the project folders.

---

## 📞 Contact  
**Jose Solórzano**  
Aspiring IT & Cybersecurity Professional  

