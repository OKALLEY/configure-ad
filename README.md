<p align="center">
<img src="https://imgur.com/yevQoIO.png" height="50%" width="50%" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
<p align="center">~This tutorial provides a guide on how to implement an on-premises Active Directory on Azure Virtual Machines~</p>

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Step 1: Create a Resource Group
- Step 2: Create a Virtual Network and Subnet
- Step 3: Create the Domain Controller VM
- Step 4: Set the Domain Controller's NIC Private IP address to STATIC
- Step 5: Create the Client VM

<h2>Deployment and Configuration Steps</h2>

<p>
<li>Login at portal.azure.com and go to Virtual machines. Click Create and choose "Azure virtual machine"</li>
<img src="https://imgur.com/b5iXP9Y.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://imgur.com/KTulFdB.png" height="30%" width="30%" alt="Disk Sanitization Steps"/>
</p>
<p>
<li>Under Resource group click "Create new" and name it "AD-Test" (short for Active Directory-Test) </li>  
<img src="https://imgur.com/EqfW8nO.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
</p>
<li>Under Instance details find "Virtual machine name" and name it "DC-1" (short for Domain Controller-1)</li> 
<li>Under Region choose "(US) West US 3"</li>
<li>Under image choose Windows Server 2022</li>
<img src="https://imgur.com/q4WIyf4.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
<p>
<li>Under "Size" choose at least 2 vcpus</li>
<li>Create a Username and Password</li>
<img src="https://imgur.com/QmoMUnw.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>  

<li>Tick the box for "Would you like to use an existing Windows Server license?"</li> 
<img src="https://imgur.com/gFktYCx.png" height="30%" width="30%" alt="Disk Sanitization Steps"/>  
<li>Tick the box for "I confirm I have an eligible Windows Server license"</li>
<img src="https://imgur.com/UkgsWBU.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>  
Click "Review + create"
<img src="https://imgur.com/urhP1am.png" height="15%" width="15%" alt="Disk Sanitization Steps"/>  

<li>Once the validation is complete, at the bottom, click "Create"</li> 
<img src="https://imgur.com/jFjjxBP.png" height="14%" width="14%" alt="Disk Sanitization Steps"/>  
<img src="https://imgur.com/zvFvYOJ.png" height="10%" width="10%" alt="Disk Sanitization Steps"/>  
</P>
<br>
<p>
<li>Next either click "Go to Resource" or click "Home" then click on the Domain Controller (DC-1)</li>
<li>Click "Networking" and find the Network Interface and click on it</li>  
<img src="https://imgur.com/tW0pFas.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>  
<li>Find and click the IP Configurations tab  <img src="https://imgur.com/pj8gfhU.png" height="10%" width="10%" alt="Disk Sanitization Steps"/> 
</li>  
<li>Here you will find the Private IP address is set to Dynamic. Click on it to change this Assignment to Static</li> 
<img src="https://imgur.com/w6jyuAT.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>  
<li>Click on "Static" and then "Save"</li>  
<img src="https://imgur.com/yyZeAKR.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>  

  <br>
 <li></li> 
