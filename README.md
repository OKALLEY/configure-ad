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

<h2>High-Level View of Deployment and Configuration Steps</h2>

<ul>
  <li type =circle>Create a Resource Group<br>
  <li type =circle>Create a Virtual Network and Subnet<br>
  <li type =circle>Create the Domain Controller VM<br>
  <li type =circle>Set the Domain Controller's NIC Private IP address to STATIC<br>  
  <li type =circle>Create the Client VM<br>
</ul>

<h2>Set up Resources in Azure</h2>

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
<img src="https://imgur.com/yyZeAKR.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>  

  <br>
<li>To crate the Client VM go back to Virtual machines and Click "Create"</li> 
<li>Under "Resource group" use the same resource group as before (AD-Test)</li> 
<li>Give the Virtual machine a name (Client-1)</li>  
<img src="https://imgur.com/kGcUcGO.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
<li>As before enter a Username and Password</li>  
<img src="https://imgur.com/yCyvkt7.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>  
<li>Tick the box for "I confirm I have an eligible Windows 10/11 license"</li>
<img src="https://imgur.com/pNr6jNR.png" height="70%" width="70%" alt="Disk Sanitization Steps"/> 
<li>Note that when creating a virtual machine, a network interface will be created for you.</li> 
<li>Click "Review + create" and after "Validation passed" appears click "Create"</li>  
<img src="https://imgur.com/noOveGD.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>  

<h2>Ensure Connectivity (between the Client and Domain Controller)</h2>

<li>In Microsoft Azure go to Virtual machines and click on the domain controller, then copy the Public IP address (DC-1)</li>
<img src="https://imgur.com/Y9bSITT.png" height="70%" width="70%" alt="Disk Sanitization Steps"/> 
<li>In Windows click start and type: Remote Desktop Connection. (Mac users install Microsoft Remote Desktop)
</li>
<li>Paste in the Public IP address and click "Connect"</li>
<img src="https://imgur.com/kkqEELP.png" height="50%" width="50%" alt="Disk Sanitization Steps"/> 
<li>Enter your credentials (e.g. Lab User and password you created)</li>
<img src="https://imgur.com/yN57n7N.png" height="50%" width="50%" alt="Disk Sanitization Steps"/> 
<li>Click Yes and give it time to start up</li>
<img src="https://imgur.com/fp8QNnZ.png" height="50%" width="50%" alt="Disk Sanitization Steps"/> 

<p>

<li>CLick start and type "wf.msc" (or "firewall" and click <img src="https://imgur.com/GN1V1Hi.png" height="30%" width="30%" alt="Disk Sanitization Steps"/> 
 </li>
<li>Click on <img src=https://imgur.com/gIfU1lK.png" height="12%" width="12%" alt="Disk Sanitization Steps"/> </li>
<li>Scroll over and at the top click "Protocol"</li>
<li>Right click and "Enable Rule" for both ICMP Echo Request</li>
<img src="https://imgur.com/Dz6rXMs.png" height="80%" width="80%" alt="Disk Sanitization Steps"/> 

<p>
<Go back to Microsoft Azure and copy the Public IP address for Client-1 >  
<Open a seperate instance of Remote Desktop and paste in the Public IP address>
<li>Enter Username (Lab User) and password</li>
<li>Click Start and type "cmd" and click on "Command Prompt App"</li>  
<img src="https://imgur.com/R5il7kN.png" height="20%" width="20%" alt="Disk Sanitization Steps"/> 
<li>Back in MicroSoft Azure go to Virtual machines and click on DC-1 and copy the Private IP address</li>
<li>In your Remote Desktop connection for Client-1 in the command line paste the Public IP address type "ping -t" ahead of it</li>
<li>Press enter to begin the ping and "control C" to end the ping</li>
  <img src="https://imgur.com/G3QD6rZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
