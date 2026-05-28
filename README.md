<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


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
<img width="698" height="614" alt="image" src="https://github.com/user-attachments/assets/76d5b27f-d85b-4551-a799-dbe6fb52ed56" />

</p>
<p>
Here, I set up the VM server and configured the AD services
</p>
<br />

<p>
<img width="681" height="481" alt="image" src="https://github.com/user-attachments/assets/9c9b4185-b05f-4730-9f41-230c684da32e" />

</p>
<p>
Here, I set domain modifications to deploy controller options within Active Directory
</p>
<br />

<p>
<img width="596" height="519" alt="image" src="https://github.com/user-attachments/assets/5047da16-2415-417f-8762-a5d119acaf37" />

</p>
<p>
Here, I set user and admin designations within Active Directory
</p>
<br />
<p>

<img width="630" height="336" alt="image" src="https://github.com/user-attachments/assets/07c55259-8025-44f2-bf56-8697c6e80896" />

</p>
<p>
Here, I set client 1 to the proper domain to simulate the new user login capability 
</p>
<br />
