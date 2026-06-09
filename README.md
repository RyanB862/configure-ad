<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
In this lab, I deployed a Windows Server Domain Controller and a Windows 10 client in Azure, configured a shared virtual network, assigned a static IP to the Domain Controller, configured DNS on the client to point to the Domain Controller, and verified connectivity using ping and ipconfig. This established the foundation required for deploying and managing Active Directory.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

-# On-premises-Active-Directory-Deployed-in-the-Cloud-Azure-
This outlines the implementation of on-premises Active Directory within Azure Virtual Machines.

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 11 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Create VM in Azure and set client 1 DNS
- Install Active Directory and set up Remote Desktop with users
- Restart and log back in as a user/create employee and admin access file designation
- Join client 1 to the VM domain in the Active Directory

<h2>Deployment and Configuration Steps</h2>

<p>
<img width="783" height="482" alt="image" src="https://github.com/user-attachments/assets/0f57b6d8-49ed-40e0-add9-92857ce03e4f" />

Inside Azure I create a resource group then select US East 2 for region. 
A Resource Group acts as a container that organizes and manages all Azure resources related to the Active Directory lab.
Then click review and create

<img width="763" height="585" alt="image" src="https://github.com/user-attachments/assets/a3a39f38-b7e9-4bf9-b0bd-a43cb781e5ef" />

I then create the virtual network. I also connect the resource group to AD (active directory) and the vnet. A Resource Group acts as a container that organizes and manages all Azure resources related to the Active Directory lab. The VNet and subnet provide a private network where the Domain Controller and client machine can securely communicate

<img width="696" height="495" alt="Screenshot 2026-06-05 140519" src="https://github.com/user-attachments/assets/21d7e6d7-2b4d-4d7f-b689-47a841004b03" />

I create a VM for DC-1. Ensuring the region is US EAST 2. 
DC-1 serves as the central server that will host Active Directory and manage users, computers, and authentication.

<img width="774" height="549" alt="Screenshot 2026-06-05 140851" src="https://github.com/user-attachments/assets/adf7964b-893c-48c8-b616-7567eb426dc0" />

Client 1 VM is setup. It's in the same region US EAST 2 and the same active directory vnet as the DC.

<img width="917" height="521" alt="Screenshot 2026-06-05 141542" src="https://github.com/user-attachments/assets/c1bf91a0-9fb8-488e-98fd-a2b9755a8685" />

Here I click into DC 1 and then click network settings. 
Here I click ipconfig then switch the Private IP Address from Dynamic to Static.
A static IP ensures the Domain Controller's address never changes, allowing clients to consistently locate authentication and DNS services

<img width="434" height="485" alt="Screenshot 2026-06-05 142118" src="https://github.com/user-attachments/assets/e2596926-caac-4365-8090-4c64aa7f31fe" />

I then log into DC 1 with Remote Desktop Protocol (RDP) using Admin username and password
Accessing the server allows configuration of Active Directory and network settings.

<img width="380" height="199" alt="image" src="https://github.com/user-attachments/assets/96a86d41-e4ca-4110-83ee-1b4789e9465b" />

<img width="501" height="547" alt="Screenshot 2026-06-05 142954" src="https://github.com/user-attachments/assets/66f53d91-2d94-486d-9da3-92a2e64c155e" />

Once inside the DC VM I click the start menu then type run. I then type wf.msc to disable the firewall. Switch to OFF
Disabling the firewall temporarily removes network restrictions so connectivity issues can be tested and verified more easily

<img width="846" height="546" alt="Screenshot 2026-06-05 143415" src="https://github.com/user-attachments/assets/49bb0b77-44b1-49be-87c9-8e7ddf6208eb" />
<img width="876" height="558" alt="Screenshot 2026-06-05 143524" src="https://github.com/user-attachments/assets/40b78e5e-14c8-4157-9929-08684deea917" />
<img width="1426" height="329" alt="Screenshot 2026-06-05 144223" src="https://github.com/user-attachments/assets/5bda765e-2f5b-42ce-a397-af162bd3f5a8" />
Back to Client 1. Click the Network Interface. Then click DNS. Type DC 1 Private IP Address.
This ensures the client uses the Domain Controller for DNS resolution, which is required for Active Directory functionality.
Then restart Client. Restarting applies the new DNS configuration and refreshes the network settings.

<img width="1181" height="549" alt="Screenshot 2026-06-05 144653" src="https://github.com/user-attachments/assets/c7a72e66-b727-4cee-81db-1112d1120640" />
<img width="1182" height="554" alt="Screenshot 2026-06-05 144834" src="https://github.com/user-attachments/assets/db27572d-5216-4e72-b7ee-ac87e8fc6c6b" />
Once logged into Client 1 I then open powershell to ping DC IP Address
A successful ping confirms network communication between the client and the Domain Controller.
This validates that the VNet, subnet, DNS, and firewall configurations are functioning correctly.

<img width="1174" height="554" alt="Screenshot 2026-06-05 145231" src="https://github.com/user-attachments/assets/bc808ec9-d5ea-4aa2-ac70-b7da1c515b46" />
<img width="1261" height="600" alt="Screenshot 2026-06-05 145440" src="https://github.com/user-attachments/assets/ab6b4578-7fba-405d-9f0e-cdd4bbdb708b" />
Still inside powershell I run ipconfig /all on Client-1
This command displays detailed network settings, including the DNS server being used.

<h2>Deploying Active Directory</h2>
<h2>Part One: Installation and Domain Join</h2>

<h2>Summary</h2>
I deployed Active Directory Domain Services, created a new domain forest, configured administrative accounts and organizational units, joined a Windows 10 client to the domain, and organized domain resources using Active Directory Users and Computers. This established a centralized identity management environment similar to what is used in enterprise organizations

<img width="839" height="737" alt="Screenshot 2026-06-08 103748" src="https://github.com/user-attachments/assets/fb4f604f-6e1d-40be-ac7a-201955f89528" />

First I log into DC-1 using Remote Desktop Protocol (RDP Port 3389) and use the Public IP Address. 
Once inside I click start menu then Server Manager.

<img width="723" height="508" alt="Screenshot 2026-06-08 104156" src="https://github.com/user-attachments/assets/32d0b40d-f7c8-4d5d-b6bb-a05562213b2f" />
<img width="714" height="506" alt="Screenshot 2026-06-08 104243" src="https://github.com/user-attachments/assets/360e17f4-9067-4cee-b9a2-460454fa5e45" />

Here I click Add Roles and Features. I click Next unitl I see the Active Directory Domain Services and I check this box then select Add Features

<img width="725" height="510" alt="Screenshot 2026-06-08 104645" src="https://github.com/user-attachments/assets/f4c8d1eb-4763-494b-b5b2-41161cf606ee" />
<img width="727" height="512" alt="Screenshot 2026-06-08 104812" src="https://github.com/user-attachments/assets/c717d39c-4719-4b54-b198-186e42d14365" />

I click next until I see this page then select install

<img width="318" height="250" alt="Screenshot 2026-06-08 105028" src="https://github.com/user-attachments/assets/48e2aeb9-b3f7-457b-9025-8f8cefd7d133" />

Back in server manager I then click the "Flag" then I click the link to "promote this server to a dommain controller"
Promoting the server creates the first Domain Controller responsible for managing the Active Directory environment.

<img width="700" height="504" alt="Screenshot 2026-06-08 105334" src="https://github.com/user-attachments/assets/54378198-5868-4cd6-8fd9-08891e395852" />

Here I click add new forest and fill "mydomain.com"
The forest establishes the highest-level Active Directory structure that stores all domain objects and configurations.

<img width="696" height="504" alt="Screenshot 2026-06-08 105650" src="https://github.com/user-attachments/assets/241ae692-b454-464d-8b75-d558d0ea3b46" />

Here I create a password for DSRM. DSRM (Directory Services Restore Mode) is a specialized boot mode for Windows Server Domain Controllers (DCs).
It allows administrators to access and repair the Active Directory (AD) database when it is corrupted or offline. Then click next through the remaining prompts

<img width="700" height="509" alt="Screenshot 2026-06-08 110407" src="https://github.com/user-attachments/assets/9fbe81c0-d9eb-4abe-9a16-47de69ad75f5" />
<img width="397" height="215" alt="Screenshot 2026-06-08 111203" src="https://github.com/user-attachments/assets/beea54e1-f3e8-46df-baeb-ef96b026716c" />

Then click install. After the install it will restart. I then log in using the Domain Credentials.
Logging in with domain credentials verifies that Active Directory was successfully installed and configured

<img width="597" height="547" alt="Screenshot 2026-06-08 111830" src="https://github.com/user-attachments/assets/236c17e1-5a4e-4446-bf58-c3549481ba61" />

Inside DC-1. I click start menu then click "Windows Adminstrative Tools" then scroll down to "Active Directory Users and Computers"

<img width="1105" height="662" alt="Screenshot 2026-06-08 112229" src="https://github.com/user-attachments/assets/61ef53ad-ea1a-4ab8-8a93-38f53bbd65e4" />

I then click "mydomain.com" then scroll to "new" then click "Organizational Unit"

<img width="794" height="683" alt="Screenshot 2026-06-08 112629" src="https://github.com/user-attachments/assets/ec60ee10-7d6d-4b8f-9901-bc4ec0e81270" />
<img width="788" height="680" alt="Screenshot 2026-06-08 112932" src="https://github.com/user-attachments/assets/a49c83aa-f68a-4731-950c-19b98199148d" />

Here I make two new OU: _EMPLOYEES and _ADMINS
This OU provides a dedicated container for organizing standard user accounts.
The _ADMINS OU separates privileged administrative accounts from regular user accounts for better security and management.

<img width="1762" height="800" alt="Screenshot 2026-06-08 113205" src="https://github.com/user-attachments/assets/ee04e36b-761e-4655-acc7-8ad92fbc8525" />
<img width="789" height="680" alt="Screenshot 2026-06-08 113545" src="https://github.com/user-attachments/assets/7ad7243e-c666-46a0-ac93-61e0b759d789" />

I create a new admin user "Jane". Jane Doe (jane_admin)
Creating an administrative user establishes a dedicated account for domain administration tasks.

<img width="789" height="683" alt="Screenshot 2026-06-08 113649" src="https://github.com/user-attachments/assets/c5611e0d-6d23-4b20-b83f-612a03c3f6cb" />

A new password is created. Using jane_admin going forward makes improves accountability, auditing, and security management.

<img width="430" height="454" alt="Screenshot 2026-06-08 114341" src="https://github.com/user-attachments/assets/66d9179a-e544-464d-8442-432c43c03e10" />
<img width="578" height="322" alt="Screenshot 2026-06-08 114747" src="https://github.com/user-attachments/assets/79953e9e-a6aa-4d9a-b0d0-3169951d494c" />

Here I add Jane_admin to a security group. I right click Jsne then scroll down to properties. Then click Members Of then fill in "domain admins"
I then log out of DC-1 and log into Jane Admin account using mydomain.com\jane_admin
Using a dedicated admin account follows security best practices and separates administrative activities from standard accounts.

<img width="397" height="198" alt="Screenshot 2026-06-08 115142" src="https://github.com/user-attachments/assets/7bd17f43-2b67-4b22-864b-21a5af9a7aec" />

I click Run and type Log off to Log out of DC-1.

<img width="405" height="213" alt="Screenshot 2026-06-08 115317" src="https://github.com/user-attachments/assets/0791ffa2-616e-429c-a3f9-bcd3fbcb30b6" />

I use RDP to log into mydomain.com\jane_admin.

<img width="1096" height="860" alt="Screenshot 2026-06-08 115647" src="https://github.com/user-attachments/assets/5da49dd7-90ca-49e9-9f91-0ab4bc44fd5d" />

Inside Client 1. I click the start menu then settings. 

<img width="372" height="427" alt="image" src="https://github.com/user-attachments/assets/5b20e132-02fc-48cb-b36b-8b57f27d6520" />
<img width="373" height="425" alt="Screenshot 2026-06-08 120156" src="https://github.com/user-attachments/assets/2e126bc9-d59d-4ac6-9d71-88160275c938" />

Here I click change computer name and change it from the workgroup to the domain.
Domain joining allows the workstation to use centralized authentication and domain-based policies.

<img width="418" height="270" alt="Screenshot 2026-06-08 120433" src="https://github.com/user-attachments/assets/bb6f0b09-8ff0-4218-a2b8-b07e662a7ec3" />
<img width="274" height="138" alt="Screenshot 2026-06-08 120745" src="https://github.com/user-attachments/assets/aa773d97-7f46-4e25-bcb4-21190afd79fc" />


Here I use Jane Admin password to join Clinet 1 to the domain. Then I restart Client 1

<img width="717" height="364" alt="Screenshot 2026-06-08 121128" src="https://github.com/user-attachments/assets/14b838cd-e992-46f0-a8a0-0f43b47cc3ee" />
<img width="1045" height="259" alt="Screenshot 2026-06-08 121255" src="https://github.com/user-attachments/assets/92a5e5a0-82d0-4b50-a00f-6ef8a8e5af52" />

Here I verify that Client 1 has been added to Active Diretory Users and Computers (ADUC) 
Confirming the computer object exists verifies that the domain join was successful.

<h2>Creating Users with Powershell</h2>
<h2>Part 2: Remote Desktop and User Provisioning</h2>

<h2>Summary</h2>
I configured Remote Desktop access for domain users, automated user provisioning through PowerShell, organized accounts within Active Directory organizational units, and validated user authentication by logging into a domain-joined workstation. This demonstrated identity management, access control, automation, and user lifecycle administration.

<img width="405" height="211" alt="Screenshot 2026-06-08 122544" src="https://github.com/user-attachments/assets/64287034-973b-4776-b95f-eb93512a5e4f" />

I log into Client 1 using Jane Admin. 
Administrative access is required to configure Remote Desktop settings on the workstation

<img width="1107" height="855" alt="Screenshot 2026-06-08 123029" src="https://github.com/user-attachments/assets/da40c756-006c-47bd-ab17-c904bec5ec27" />
<img width="423" height="230" alt="Screenshot 2026-06-08 123410" src="https://github.com/user-attachments/assets/c291dc4c-0e17-414b-9f82-3a5f59ca9fe7" />

Here I click menu then settings then Remote Desktop. Then I click "Users Accounts"
I add domain users to log in using remote desktop

<img width="728" height="524" alt="Screenshot 2026-06-08 123823" src="https://github.com/user-attachments/assets/7d8455af-ff23-4914-86a6-e39048c23311" />

Log into DC-1 as jane_admin. I click start menu then open "PowerShell ISE" then right click to "Run as Administrator".	
PowerShell ISE provides a scripting environment for automating administrative tasks.

<img width="1232" height="674" alt="image" src="https://github.com/user-attachments/assets/a9643bbc-46a9-4824-93bb-2e655a6b191a" />

Here I run a powershell script to create users. I Paste and Run User Creation Script.
Automation allows administrators to efficiently provision multiple user accounts at once.

<img width="1027" height="933" alt="Screenshot 2026-06-08 124607" src="https://github.com/user-attachments/assets/d5ebcfa9-5604-4218-968c-70830e7e21a4" />

I then observe the Account Creation.
Monitoring the script confirms successful account provisioning and identifies any errors.

<img width="756" height="626" alt="Screenshot 2026-06-08 124908" src="https://github.com/user-attachments/assets/7ddac4b8-6d94-410b-a931-c5c64ecc643e" />

Here I find user "gig.foc". I now verify Users in the _EMPLOYEES OU.	
Confirming account placement ensures users are organized according to company standards.
I then attempt to login Client 1 using a New User Account: "gig.foc"
Testing validates that the newly created account can successfully authenticate and access domain resources.

<img width="598" height="549" alt="Screenshot 2026-06-08 125511" src="https://github.com/user-attachments/assets/89be53c4-6c0e-4efa-a08e-8817c37b18a9" />
<img width="399" height="215" alt="Screenshot 2026-06-08 125656" src="https://github.com/user-attachments/assets/753bce05-62b0-4fb2-91e1-2fed7680c244" />
<img width="379" height="368" alt="Screenshot 2026-06-08 125829" src="https://github.com/user-attachments/assets/ba231bb5-6d9c-430a-812f-3b8929ae87f7" />

I first must log out of Client 1 as Jane. Then log in as gig.foc using Remote Desktop Protocol (RDP)







