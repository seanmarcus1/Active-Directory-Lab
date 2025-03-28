# Active Directory Home Lab

## Project Overview
This Active Directory home lab simulates a real-world Windows domain environment to demonstrate foundational sysadmin and security skills. This lab includes a domain controller, client workstation, domain users, organizational units, and custom Group Policies.

This enterprise environment was built using VMware Workstation Pro and includes:
- **Windows Server 2019** VM as our Domain Controller
- **Windows 11** VM as the client workstation
- A custom domain 'lab.local'
- Three Organizational Units: **HR**, **IT**, and **Finance** equipped with a test user in each
- Group Policies to enforce security controls and simulate a real-world environment

---

## Objectives
- Configure a working Active Directory domain from scratch
- Create users and organize them into Organizational Units (OUs)
- Add a Windows client to the domain
- Apply Group Policies to enforce user restrictions

---

## Lab Setup
To begin this lab, we're going to configure our Windows Server 2019 machine by promoting it to a Domain Controller and installing the Active Directory Domain Services role.

### Domain Controller Setup (DC01)
- Installed Windows Server 2019 (Desktop Experience)
- Rename to 'DC01' (Domain Controller 01)
- Set a static IP
- Promoted to a domain controller using 'lab.local' as our domain

Renaming the host to 'DC01': ![1  Rename Device](https://github.com/user-attachments/assets/31c50761-32a0-42ff-bcfd-d978cc49d7ec)

Windows Server VM Network Settings: 

![2  Network Settings](https://github.com/user-attachments/assets/c4c32dc2-ecfa-4674-b1fa-92c043604f79)

Installing Active Direcory Domain Services: ![3  AD Install](https://github.com/user-attachments/assets/413c0ed1-99eb-4362-8dcc-0e97eb514e44)

Confirmation that AD DS was installed as well as the prompt to promote DC01 to a Domain Controller: ![4  Post-Install Flag Notification](https://github.com/user-attachments/assets/795b88bd-c30c-4c7b-9721-fd4b8e893247)

Adding a new forest with the domain name as 'lab.local': ![5  Domain Name Setup](https://github.com/user-attachments/assets/3ba69452-e78f-4e5e-995d-b29d0635135d)

After going through the rest of the AD DS configuration wizard and rebooting the system, we have confirmation that 'DC01' has been successfully promoted to a domain controller, indicatied by the login screen shown for LAB\\Administrator: ![7  DC Confirmation](https://github.com/user-attachments/assets/16f3f12f-35fc-4cc0-859f-b5087676ee58)

### Organizational Units and Users
- Created OUs: 'HR', 'IT', and 'Finance' using Active Directory Users and Computers (ADUC)
- Created one user for each OU

Organizational Units creted in ADUC: ![8  ADUC OU Creation](https://github.com/user-attachments/assets/5ecd5546-5cc3-42ee-85eb-f5aa6fd7500d)

Creating users in each OU: 

![9  User Creation](https://github.com/user-attachments/assets/b733fd36-bc25-46c5-8794-0b1d4d2b6765)

Domain tree expanded showing a user in each OU: ![10  User in each group](https://github.com/user-attachments/assets/3fc3b5e4-3483-4b0a-9120-6d4fba7c948e)


### Client Workstation Setup (CLIENT01)
- Installed Windows 11
- Set static IP and matched the DNS to the Server DNS
- Joined CLIENT01 to the 'lab.local' domain

Network settings for CLIENT01: ![12  CLIENT Network Settings](https://github.com/user-attachments/assets/6a58cf1c-3e8a-40c7-936f-7d0be09eb5b5)

Confirming DC01 is reachable through a ping test: ![13  Ping test to DC01](https://github.com/user-attachments/assets/ea133652-bc2e-48a6-b972-8274d7837051)

Joining CLIENT01 to the 'lab.local' domain: 

![14  Add Client to Domain](https://github.com/user-attachments/assets/bad7068d-202a-4bf1-8050-286ae8cdbdcf)

Successfully added: 

![15  Added](https://github.com/user-attachments/assets/60081d1b-383a-44f5-9256-956d6267083d)

### Domain User Login Test
- Logged into CLIENT01 using 'jcarter'

'jcarter' login screen with the domain set to 'LAB': ![16  User login](https://github.com/user-attachments/assets/62b715e9-2df5-4507-8f71-05291619e347)


Successfully signed in to CLIENT01 as 'Jake Carter': 

![17  Confirmed Sign in](https://github.com/user-attachments/assets/e73cd0eb-266e-46d5-9a6e-3c90014ffd81)


---

## Group Policy Configuration

Now that we have a working Active Directory environment with organizational units and domain users, it's time to introduce Group Policies to enforce security controls and simulate real-world configurations. 

### Login Banner
- Created group policy object (GPO): 'Login Banner Policy'
- Applied to the entire domain

The two options being edited for the Login Banner GPO: ![20  Banner Policy 2](https://github.com/user-attachments/assets/e29c848c-c233-439d-9d7b-e70328ced302)

Login message title:

![21  Banner Policy 3](https://github.com/user-attachments/assets/4035e8d3-e9df-4c84-a24e-257e9536bb7e)

Details under the title:

![24  Banner Policy 4](https://github.com/user-attachments/assets/326feab7-4707-4c9d-97fc-cca9e6887cbd)

Updating the group policy on CLIENT01: ![25  Banner Policy Update](https://github.com/user-attachments/assets/0766ef14-3dca-4add-a865-86aa688d94e4)

Result of the update after rebooting CLIENT01: ![26  Banner Policy Result](https://github.com/user-attachments/assets/9feaa9e8-381d-48ea-98a5-609fb2c889bb)


### Disable Control Panel and Settings Access
- Created GPO 'Restrict Settings Access'
- Linked to the User level

GPO linked to Users: ![27  Settings Policy 1](https://github.com/user-attachments/assets/e2a1dca2-6bc7-4bf4-b25c-af9bd3000097)

Changing the 'Prohibit access to Control Panel and PC settings' control to 'Enabled': ![28  Settings Policy 2](https://github.com/user-attachments/assets/f3a4d26a-2f34-495a-808d-6fe74fa28960)

Error message when attempting to open Control Panel or Settings on CLIENT01: ![29  Settings Policy 3](https://github.com/user-attachments/assets/a1d5bb9a-e13b-4690-a65b-a3d708f9e45a)

---



