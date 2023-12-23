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
- Joint Client-1 to your domain (mydomain.com)
- Setup Remote Desktop for non-administrative users on Client-1
- Create a bunch of additional users and attempt to log into client-1 with one of the users

<h2>Deployment and Configuration Steps</h2>

- SET UP RESOURCES IN AZURE
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
- ENSURE CONNECTIVITY BETWEEN THE CLIENT AND DOMAIN CONTROLLER
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
- INSTALL ACTIVE DIRECTORY
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
<img src="https://i.imgur.com/2ZJccyp.png" height="30%" width="30%" alt="Disk Sanitization Steps"/>
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
- CREATE AN ADMIN AND NORMAL USER ACCOUNT IN ACTIVE DIRECTORY     
</p>
8. In Active Directory Users and Computers, create two folders called "_EMPLOYEES" and "_ADMINS"     
<img src="https://i.imgur.com/i1mCvqH.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/OfqCr4W.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/ucwdE44.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/4ZHQQ7p.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
9. Create a new employee named "fred meka" with the username of "fred_admin"
<img src="https://i.imgur.com/ZXCGwTr.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/ndl8yyP.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/JkBa8ku.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/8HtyXcG.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/oqqVZV4.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
10. Add fred_admin to the "Domain Admins" Security Group      
<img src="https://i.imgur.com/U4OSzQt.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/V9z3CBi.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/kZgd9KO.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/nJBJ3Qf.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/uMb8gOd.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/5daK5z7.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
11. Log off as "labuser" on DC-1 Remote Desktop connection and log back in as "mydomain.com\fred_admin"
<img src="https://i.imgur.com/61VjoBa.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/px7vTJS.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
<br />
- JOINT CLIENT-1 TO YOUR DOMAIN (MYDOMAIN.COM)     
</p>
12. From Azure Portal, set client-1 DNS setting to DC-1 private IP Address: 10.0.0.4 and restart Client-1
<img src="https://i.imgur.com/0xKZ37v.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/oO6CYyQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/EYv0EKk.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/3DsrDBi.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
13. Login to Client-1 (Remote Desktop) as labuser and join it to the domain (computer will restart)
</p>  
     a. System -> Renamed this PC (Advanced) -> Change -> Member of Domain (mydomain.com) then enter name and password
<img src="https://i.imgur.com/nujEw2x.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/c6euuEX.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/dAntXCQ.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/haOKmPk.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
     b. Login to the Domain Controller (Remote Desktop) and verify Client-1 shows up in Active Directory Users and Computer   
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br /> 
- SETUP REMOTE DESKTOP FOR NON-ADMINISTRATIVE USERS ON CLIENT-1
</p>
14. Log into Client-1 as mydomain.com\fred_admin
<img src="https://i.imgur.com/QvVOTyF.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
15. Open system properties and click "Remote Desktop"
<img src="https://i.imgur.com/Vuz1F0m.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
16. Allow "domain users" access to remote desktop
<img src="https://i.imgur.com/BqfdwHD.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/5Yxt0tL.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
You can now log into Client-1 as a non-administrative user.
</p>
<br /> 
- CREATE A BUNCH OF ADDITIONAL USERS AND ATTEMPT TO LOG INTO CLIENT-1 WITH ONE OF THE USERS
</p>
17. Login to DC-1 as fred_admin and open PowerShell ISE as an administrator  
<img src="https://i.imgur.com/fbrCVB1.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
18. Create a new file and paste the contents of the script into it (https://github.com/joshmadakor1/AD_PS/blob/master/Generate-Names-Create-Users.ps1)
<img src="https://i.imgur.com/MeAiKGd.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
19. Run the script and observe the accounts being created
<img src="https://i.imgur.com/NzyZMPp.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
20. When finished, open Active Directory Users and Computers and observe the accounts being created      
<img src="https://i.imgur.com/rKnl71r.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
21. Attempt to log into Client-1 with one of the accounts (badobo.xagi)
<img src="https://i.imgur.com/w9MNfCd.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/nTiioja.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>


