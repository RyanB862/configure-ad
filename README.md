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

Here I click into DC 1 and then click network settings. Here I click ipconfig then switch the Private IP Address from Dynamic to Static.
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





