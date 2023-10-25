<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Setup Resources in Azure
- Ensure Connectivity between the client and Domain Controller
- Install Active Directory
- Create an Admin and Normal User Account in Active Directory
- Joining Client-1(user machine) to created domain
- Setting up the Remote Desktop

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/D3qbeDh.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
This portion of the project showcases the creation of two virtual machines. The virtual machines are named Client-1 and DC-1, Client-1 hosts a virtualized Windows 10 operating system and DC-1 is run on Windows Server 2022. This step includes assigning both of the different virtual machines to the same resource group and it also involved configuring network interace card of DC-1 to ensure connectivity between each respective machine.
</p>
<br />

<p>
<img src="https://i.imgur.com/uigysI6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
A critical point in ensuring this tutorial is done successfully and Active Directory is installed an fully functional I had to navigate to the local windows firewall in the domain controller machine and enable ICMPv4. This alteration forces the domain controller to allow inbound requests coming from the client machine. This photo shows the before and after of making that change. Using "ping -t" to check for connectivity, the request from the client machine timed out due to the firewall being enabled on the domain controller. After reconfiguring the settings, there were replies to the requests, meaning the domain controller is working fine.
</p>
<br />

<p>
<img src="https://i.imgur.com/hKPSTIO.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/qxhIcl0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/BEisgFO.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
This step demonstrates installing Active Directory on the domain controller and then creating an admin "Jane Doe" account. This Jane Doe account serves as the desktop administrator.
</p>
<br />

<p>
<img src="https://i.imgur.com/Qm0cYSd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/0xiDMJe.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
At this stage, I had to set Client-1's(user account) DNS settings to the Domain Controllers's Private IP address. This involved renaming the system properties of this domain to my created domain. This step is crucial in ensuring that everything runs smoothly and there are no issues when the client machine looks up elvin.com(the created domain linked to the domain controller). The second photo shows the Client-1 computer in the "Computers" folder of Active Directory Users and Computers setting which confirms everything has worked. Remote desktop for client has been set up and the admin account can begin to add users.
</p>
<br />
