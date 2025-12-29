<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Implementing Active Directory Deployed Within the Cloud (Azure)</h1>
This tutorial outlines the implementation of Active Directory within Azure Virtual Machines.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services

<h2>Operating Systems Used </h2>

- Windows Server 2025
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Install Active Directory from DC-1 VM
- Creating a Domain User within the Domain
- Join Client-1 VM to the Domain
- Setup Remote Desktop for Non-Admin Users on Client-1 VM

<h2>Deployment and Configuration Steps</h2>

<p>
<img width="2880" height="1708" alt="image" src="https://github.com/user-attachments/assets/7d396b8b-e0b5-4497-8c79-0c24ed2a3b4f" />
</p>
<p>
Logging into the DC-1 VM, navigate to Server Manager, Add Roles and Features, and install Active Directory Domain Services. Promote the server as a Domain Controller and set up a new forest labeled "mydomain.com". Restart the DC-1 VM and log back in as "mydomain.com\'username'".
</p>
<br />

<p>
<img width="2880" height="1696" alt="image" src="https://github.com/user-attachments/assets/83887db6-8969-4f55-a381-ae0a83a9d490" />
</p>
<p>
Open up Active Directory Users and Computers and create a new Organizational Unit (OU) labeled "_ADMINS". Create a new user within the "_ADMINS" OU and add this user to the Domain Admins security group.
</p>
<br />

<p>
<img width="2880" height="1716" alt="image" src="https://github.com/user-attachments/assets/8ca03125-0eae-4d67-8e96-8c889b54fe12" />
</p>
<p>
Please ensure that Client-1's DNS settings are configured to use DC-1's Private IP address. From the Client-1 VM, navigate to the Rename this PC (Advanced) settings, select 'Change' to change the domain, switch to 'Member of domain: mydomain.com', and log in using the domain admin's login credentials. Restart the machine to implement the change and verify that client-1 shows up in ADUC under the 'Computers' Organizational Unit. Log back into Client-1 as the Domain Admin and within the system properties, select Remote Desktop, and allow 'Domain Users' to access the remote desktop. To see more on creating a Group Policy that applies this to many systems, <a href="https://github.com/camcoleman21/group-policy-and-account-management">click the link here.</a>

</p>
<br />
