<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How to Deploy on-premises Active Directory within Azure Compute](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Set up resources in Azure
- Ensure Connectivity between the client and Domain Controller
- Install Active Directory
- Step 4

<h2>Deployment and Configuration Steps</h2>

SET UP RESOURCES IN AZURE
<p>
1. Create the Domain Controller VM (Windows Server 2022) named “DC-1”.
<img src="https://i.imgur.com/cEGxBGS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
2. Set Domain Controller’s NIC Private IP address to be static.
<img src="https://i.imgur.com/e5BUqgf.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/qgzlRt4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/8OaIpeF.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/T0tmMKo.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
3. Create the Client VM (Windows 10) named “Client-1”. 
<img src="https://i.imgur.com/kVbF486.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
ENSURE CONNECTIVITY BETWEEN THE CLIENT AND DOMAIN CONTROLLER
</p>
4. Login to Client-1 with Remote Desktop and ping DC-1’s private IP address with ping -t <10.0.0.5> (perpetual ping).  
<img src="https://i.imgur.com/rfpvju4.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
5. Login to the Domain Controller and enable ICMPv4 in on the local windows Firewal. 
<img src="https://i.imgur.com/MVLQoJq.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/6ryPaC7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
6. Check back at Client-1 to see the ping succeed.
<img src="https://i.imgur.com/50MqGdv.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
<br />
INSTALL ACTIVE DIRECTORY
</p>
7. Login to DC-1 and install Active Directory Domain Services
<img src="https://i.imgur.com/X0tBXrO.png" height="40%" width="40%" alt="Disk Sanitization Steps"/> 
</p>
     a. Add roles and features
<img src="https://i.imgur.com/lv0FZDG.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/q46NGa3.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/S0U6AUH.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/vjjtLMm.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/cX9NMml.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/2ZJccyp.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/ghAeNt3.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/jOCwitD.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/SAnmanx.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/IolZQ9Q.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
     b. Promote as a DC: Setup a new forest as mydomain.com   
<img src="https://i.imgur.com/tpAG3tU.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/5dSNftd.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/mIgNGO2.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/gGhAeMf.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/vqhAOB6.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/fLTA7yx.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/nNs22ex.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/wxxxRoG.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
     c. Restart and then log back into DC-1 as user: mydomain.com\labuser
<img src="https://i.imgur.com/A37kaNl.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
