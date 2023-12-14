<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1> An On-premises Active Directory Deployed in the Cloud (In Azure) </h1> 
       
In this tutorial we will set up Active Directory within Microsoft Azure Virtual Machines.<br />

<p>

Setting up Active Directory on a Windows 10 virtual machine involves installing the Active Directory Domain Services role, configuring domain parameters, creating a domain controller, and adding users and groups. It enables centralized management and authentication across a network, improving security and efficiency.

</p>

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Step 1 - Create resources in Azure
- Step 2 - Ensure Connectivity between the Client and Domain Controller
- Step 3 - Install Active Directory
- Step 4 - Create an Admin and Normal User Account in AD
- Step 5 - Join Client-1 to your domain (mydomain.com)
- Step 6 - Setup Remote Desktop for non-administrative users on Client-1
- Step 7 - Create several additional users and attempt to log into client-1 with one of the users

<h2>Deployment and Configuration Steps</h2>

<p>
  
  Step 1 - Create resources in Azure
  
<img src="https://i.imgur.com/yqk1k7E.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>


<img src="https://i.imgur.com/Ln8rai9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>


<img src="https://i.imgur.com/5xmqBcc.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>


<img src="https://i.imgur.com/tR5ramh.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<img src="https://i.imgur.com/UBMGLHC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<img src="https://i.imgur.com/2kju7w7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<img src="https://i.imgur.com/Vyk7Mzc.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<img src="https://i.imgur.com/Jfr6p6j.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<img src="https://i.imgur.com/Zx3YXtz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<img src="https://i.imgur.com/6yZJpfd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>

<p>
  
1) Create the Domain Controller VM (Windows Server 2022) named “DC-1”
  
   - Take note of the Resource Group and Virtual Network (Vnet) that get created at this time

   - Set the domain controller’s NIC Private IP address to be static

   - Create the Client VM (Windows 10) named “Client-1”. Use the same Resource Group and Vnet that was created in
     Step 1A
     
   - make sure both VMs are in the same Virtual network (you can check the topology with Network Watcher)

</p>
<br />

<p>

Step 2 - Make sure Client 1 and Domain Controller are connected
  
<img src="https://i.imgur.com/qnYM0ZO.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>


<img src="https://i.imgur.com/NSHRDEO.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>


 1) Login to Client 1 with Remote Desktop and ping DC-1’s private IP address with ping -t <ipaddress> (perpetual ping)
  
    - Login to the Domain Controller and enable ICMPv4 in on the local windows Firewall
  
    - Check back at Client-1 to see the ping succeed

</p>

<p>
  


</p>
<br />

<p>

Step 3 - Install Active Directory

<img src="https://i.imgur.com/567ICjV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<img src="https://i.imgur.com/oxXWaiG.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<img src="https://i.imgur.com/c76T6iT.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<img src="https://i.imgur.com/YJWW4os.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<img src="https://i.imgur.com/xYyZCdQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<img src="https://i.imgur.com/vuhA6WI.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<img src="https://i.imgur.com/8e5NJI4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<img src="https://i.imgur.com/REtTj7z.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<img src="https://i.imgur.com/WVLEMze.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>

<p>
  
1) Login to DC-1 and install Active Directory Domain Services
   
   - Promote as a DC: Setup a new forest as mydomain.com (can be anything, just           remember what it is)

   - Restart and then log back into DC-1 as user: mydomain.com\Kessielab 
</p>

<p>

Step 4 - Create both ADMIN and user Accounts in Active Directory

<img src="https://i.imgur.com/w0SwJTY.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<img src="https://i.imgur.com/DkFs07v.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<img src="https://i.imgur.com/D33HWa2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<img src="https://i.imgur.com/Wx2wp7t.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<img src="https://i.imgur.com/incj9rX.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<img src="https://i.imgur.com/2K3KF1j.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<img src="https://i.imgur.com/28Beaql.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<img src="https://i.imgur.com/1MzyW79.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>



1) Go to Active Directory Users and Computers, create an Organizational Unit (OU) called “_EMPLOYEES”


   - Create a new OU named “_ADMINS”


   - Create a new employee named “Nana Kessie” (same password) with the username of   “nana_admin”

   - Add nana_admin to the “Domain Admins” Security Group

   - Log out/close the Remote Desktop connection to DC-1 and log back in as “mydomain.com\nana_admin”

   - User nana_admin as your admin account from now on
    
</p>

<p>
  
  Step 5 - Join Client-1 to your domain (mydomain.com\nana_admin)

   <img src="https://i.imgur.com/28Beaql.png" height="80%" width="80%" alt="Disk     Sanitization Steps"/>

   <img src="https://i.imgur.com/1MzyW79.png" height="80%" width="80%" alt="Disk  Sanitization Steps"/>

1) From the Azure Portal, set Client-1’s DNS settings to the DC’s Private IP address
    
   - From the Azure Portal, restart Client-1
    
   - Login to Client-1 (Remote Desktop) as the original local admin (labuser) and join       it to the domain (computer will restart)
    
   - Login to the Domain Controller (Remote Desktop) and verify Client-1 shows up in         Active Directory Users and Computers (ADUC) inside the “Computers” container on         the root of the domain
    
   - Create a new OU named “_CLIENTS” and drag Client-1 into there (Step is not really       necessary, just for organizational purposes. I guess I skipped this in the lab!)
</p>



<p>

  
 Step 6 - Setup Remote Desktop for non-administrative users on Client-1

 <img src="https://i.imgur.com/nf8kbCl.png" height="80%" width="80%" alt="Disk  Sanitization Steps"/>

 <img src="https://i.imgur.com/ei2O3nW.png" height="80%" width="80%" alt="Disk  Sanitization Steps"/>

 <img src="https://i.imgur.com/4pWc0pJ.png" height="80%" width="80%" alt="Disk  Sanitization Steps"/>

 <img src="https://i.imgur.com/8SiMPNT.png" height="80%" width="80%" alt="Disk  Sanitization Steps"/>

 <img src="https://i.imgur.com/uHj1PdD.png" height="80%" width="80%" alt="Disk  Sanitization Steps"/>

 <img src="https://i.imgur.com/m7Lfky6.png" height="80%" width="80%" alt="Disk  Sanitization Steps"/>

 <img src="https://i.imgur.com/znMpzuX.png" height="80%" width="80%" alt="Disk  Sanitization Steps"/>

 <img src="https://i.imgur.com/bOnGXp2.png" height="80%" width="80%" alt="Disk  Sanitization Steps"/>

 <img src="https://i.imgur.com/fMEGntU.png" height="80%" width="80%" alt="Disk  Sanitization Steps"/>

 <img src="https://i.imgur.com/ivu5kD3.png" height="80%" width="80%" alt="Disk  Sanitization Steps"/>

 <img src="https://i.imgur.com/AVDErG5.png" height="80%" width="80%" alt="Disk  Sanitization Steps"/>

 <img src="https://i.imgur.com/AFsLcYy.png" height="80%" width="80%" alt="Disk  Sanitization Steps"/>

 <img src="https://i.imgur.com/VBei4x8.png" height="80%" width="80%" alt="Disk  Sanitization Steps"/>

 <img src="https://i.imgur.com/TZc1NuZ.png" height="80%" width="80%" alt="Disk  Sanitization Steps"/>

 <img src="https://i.imgur.com/QvK6CDJ.png" height="80%" width="80%" alt="Disk  Sanitization Steps"/>

 <img src="https://i.imgur.com/lYifPsY.png" height="80%" width="80%" alt="Disk  Sanitization Steps"/>

 <img src="https://i.imgur.com/KOSQ3AE.jpeg" height="80%" width="80%" alt="Disk  Sanitization Steps"/>

 <img src="https://i.imgur.com/YV5naQi.png" height="80%" width="80%" alt="Disk  Sanitization Steps"/>

1) Log into Client-1 as mydomain.com\nana_admin and open system properties

    - Click “Remote Desktop”

    - Allow “domain users” access to remote desktop

    - You can now log into Client-1 as a normal, non-administrative user now

    - Normally you’d want to do this with Group Policy that allows you to change MANY         systems at once (maybe a future lab)


 

</p>


  

<br />
