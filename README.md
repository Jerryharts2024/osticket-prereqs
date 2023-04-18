<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How To Install osTicket with Prerequisites](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Create an Azure Virtual Machine Windows 10, 4 vCPUs
- Install / Enable IIS in Windows WITH CGI
- install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi)
- install the Rewrite Module (rewrite_amd64_en-US.msi)
- Create the directory C:\PHP
- download PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) and unzip the contents into C:\PHP
- download and install VC_redist.x86.exe.
- download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi)
- Open IIS as an Admin and Register PHP from within IIS
- Install osTicket v1.15.8
- Reload IIS (Open IIS, Stop and Start the server)
- Go to sites -> Default -> osTicket (Note that some extensions are not enabled)
- Rename: ost-config.php and Assign Permissions: ost-config.php
- Set up osTicket in the browser (click Continue)
- install HeidiSQL, and Continue Setting up osticket in the browser
- Clean up (Delete: C:\inetpub\wwwroot\osTicket\setup)


<h2>Installation Steps</h2>
<h3><strong>Step 1: Create an Azure Virtual Machine Windows 10, 4 vCPUs</strong></h3>
<p>
<img src="https://user-images.githubusercontent.com/131130119/232697781-0bb54e23-f521-4279-a6af-2b13f4e3de5c.png" height="80%" width="80%" alt=" "/>
</p>

<p>
  The first you pretty much want to do is to Create a Resource Group.This is to ensure that all related resources can be contained in one group. As soon as you have created a resource group, the next thing is to create a Windows 10 Virtual Machine (VM) with 2-4 Virtual CPUs. Make sure the VM is given a name, such as "Vm-osticket".
Also this is the time you have to specify Username, (for example/whatever you chose) and password (for example/whatever you chose). 
  </p>
 <p>
<img src="https://user-images.githubusercontent.com/131130119/232706472-ff638ec1-f929-4861-b6c4-675754255d3d.png" height="80%" width="80%" alt=" "/>
  
  <p>When creating the VM, allow it to create a new Virtual Network (Vnet). This is done authomatically during VM creation.</p>
</p>

<br />

<h3><strong>Step 2: On new VM - Install / Enable IIS in Windows WITH CGI</strong></h3>
<p>
<img src="https://user-images.githubusercontent.com/131130119/232729509-e18baa65-40cb-4337-b971-293f240a57e1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
To do this you have to Logon to the newly created VM using the username and password created during the VM creation in Azure. This is done through Remote Destop
  Connection software, available in all windows OS.  And as soon as the window opens, go to the start menu and run ---> control --> programs --> turn windows features
  on or off --> check --> Internet Information Service --> World Wide Web Service --> Application Development Features --> and finally check --> CGI. --> 
  click ok to install Internet Information Service selected features.
</p>
<br />

<h3><strong>Step 3: On the VM - install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi)</strong></h3>
<p>
<img src="https://user-images.githubusercontent.com/131130119/232734318-4aa5dd01-e47b-48e0-bb31-04ccc4bc6220.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Using the this link, download and install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi) https://drive.google.com/file/d/1RHsNd4eWIOwaNpj3JW4vzzmzNUH86wY_/view?usp=share_link . As demonstrated above, it requires just a normal installatiion. 
</p>
<br />

<h3><strong>Step 4: On the VM - install the Rewrite Module (rewrite_amd64_en-US.msi)</strong></h3>
<p>
<img src="https://user-images.githubusercontent.com/131130119/232738850-09179366-1352-4785-bb00-5f56d28097a9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Using the this link, download and install Rewrite Module (rewrite_amd64_en-US.msi)  . 
  https://drive.google.com/file/d/1tIK9GZBKj1JyUP87eewxgdNqn9pZmVmY/view?usp=share_link. As demonstrated above, it requires just a normal installatiion.
</p>
<br />

<h3><strong>Step 5: Create the directory for PHP on our C drive - C:\PHP </strong></h3>
<p>
<img src="https://user-images.githubusercontent.com/131130119/232745560-d2eeb5db-a14a-4143-8ee0-23b2d774df5c.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
So basically this is to create a folder names PHP on the C drive. So sinply go to the C drive  Right click, go to new and and create a folder. Name it PHP
</p>
<br />

<h3><strong>Step 6: Download PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) and unzip the contents into C:\PHP </strong></h3>
<p>
<img src="https://user-images.githubusercontent.com/131130119/232750070-d2b32012-d092-4e54-83f7-92900545d1a8.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
So basically this is to download the PHP zip file and extract the content of the file into the previously created folder named PHP on the C drive. So sinply go to the download folder to locate the zip folder and  Right click, to extract in to the PHP folder on the C Drive. (Link below to download)
https://drive.google.com/file/d/1snNMtLdCOpMtkCyD4mvl9yOOmvVIp9fP/view?usp=share_link
</p>
<br />

<h3><strong>Step 7: Download and install VC_redist.x86.exe.</strong></h3>
<p>
<img src="https://user-images.githubusercontent.com/131130119/232861652-4dce1627-53ee-4a07-8003-fe98f204ecd6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Download and install the VC_redist.x86.exe. This is just a normal installation.
https://drive.google.com/file/d/1s1OsGF3-ioO0_9LYizPRiVuIkb3lFJgH/view?usp=share_link
</p>
<br />

<h3><strong>Step 8: Download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi) </strong></h3>
<p>
<img src="https://user-images.githubusercontent.com/131130119/232865934-df77cacb-9f0d-4737-8bf0-deef389255fd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 Pretty simple, just using the link below Download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi)
 https://drive.google.com/file/d/1_OWh9p7VQLcrB0q_V7qT8yHl0xo5gv7z/view?usp=share_link
</p>
<br />



