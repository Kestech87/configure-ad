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

- Step 1 - Resources in Azure
- Step 2 - Ensure Connectivity between the Client and Domain Controller
- Step 3 - Install Active Directory
- Step 4 - Create an Admin and Normal User Account in AD
- Step 5 - Join Client-1 to your domain (mydomain.com)
- Step 6 - Setup Remote Desktop for non-administrative users on Client-1
- Step 7 - Create several additional users and attempt to log into client-1 with one of the users

<h2>Deployment and Configuration Steps</h2>

<p>
  
  Step 1 - Resources in Azure
  
<img src="https://i.imgur.com/jsIifQR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>


<img src="https://i.imgur.com/Ln8rai9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>


<img src="https://i.imgur.com/wP8ZV4l.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>


<img src="https://i.imgur.com/tR5ramh.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<img src="https://i.imgur.com/azawNfy.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<img src="https://i.imgur.com/tV5TG6a.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<img src="https://i.imgur.com/Vyk7Mzc.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<img src="https://i.imgur.com/WHIxqYc.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<img src="https://i.imgur.com/Zx3YXtz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<img src="https://i.imgur.com/6yZJpfd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>

<p>
  
1) Create the Domain Controller VM (Windows Server 2022) named “DC-1”
  
   - Take note of the Resource Group and Virtual Network (Vnet) that get created at this time

   - Set Domain Controller’s NIC Private IP address to be static

   - Create the Client VM (Windows 10) named “Client-1”. Use the same Resource Group and Vnet that         was created in Step 1A
     
   - Ensure that both VMs are in the same Vnet (you can check the topology with Network Watcher

</p>
<br />

<p>

Step 2 - Ensure Connectivity between the Client and Domain Controller
  
<img src="https://i.imgur.com/qnYM0ZO.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<img src="https://i.imgur.com/bduSZeH.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<img src="https://i.imgur.com/EjJ6lWl.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<img src="https://i.imgur.com/NSHRDEO.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>


 1) Login to Client-1 with Remote Desktop and ping DC-1’s private IP address with ping -t <ipaddress>    (perpetual ping)
  
    - Login to the Domain Controller and enable ICMPv4 in on the local windows Firewall
  
    - Check back at Client-1 to see the ping succeed

</p>

<p>
  


</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
