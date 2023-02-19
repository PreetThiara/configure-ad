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

- Create a domain controller(DC-1) virtual machine running on Windows Server 2022 and Create the client virtual machine(Client-1) running on windows 10  
- Login to DC-1 and install Active Directory Domain Services 
- Create an admin and normal user account in active directory
- Join Client-1 to your domain 
- Run Powershell Script to create Users

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/ffIS6U5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
step 1 
</p>
<img src="https://i.imgur.com/SWRKEMg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/QVbTBlj.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/pxJzKGi.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
On DC-1 go to server manager -> Add roles and features -> Check Active Directory Domain services. Once installed click promote this server to a domain controller on top right -> Add a new forest -> Name the root domain name
<p>
<img src="https://i.imgur.com/OvIDyLh.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/FlY1FgC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/RHSgnOO.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
On server manager top right go to tools -> Active Directory Users and computers. Right Click on mydomain.com -> New -> Organizational Unit -> Name it _employees and another one called _admins. To create new user go to folder you want user in -> right click -> New -> User
</p>
<img src="https://i.imgur.com/QQJnbyD.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/mAhnko7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/nXvowR5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/EndTHxO.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Go to Azure Portal DC-1 -> networking to get the private ip address of DC-1. Go to Client-1 -> Networking -> CLick on Client-1's network interface -> DNS Servers -> Custom -> Paste DC-1's private ip address -> Save -> Go back to Client-1 and restart
</p>
<img src="https://i.imgur.com/wNqD5BR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/nKJR01d.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/FrFh220.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/QLDsIWU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Login to DC-1 with admin credentials -> Open Powershell_ise as an administrator -> Create a new file and paste contents of script which will create 10,000 users -> Run the script
<p>
