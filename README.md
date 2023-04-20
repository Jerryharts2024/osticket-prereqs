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
<img src="https://user-images.githubusercontent.com/131130119/232697781-0bb54e23-f521-4279-a6af-2b13f4e3de5c.png" height="80%" width="80%" alt="osTicket - Prerequisites and Installation"/>
</p>

<p>
  The first you pretty much want to do is to Create a Resource Group.This is to ensure that all related resources can be contained in one group. As soon as you have created a resource group, the next thing is to create a Windows 10 Virtual Machine (VM) with 2-4 Virtual CPUs. Make sure the VM is given a name, such as "Vm-osticket".
Also this is the time you have to specify Username, (for example/whatever you chose) and password (for example/whatever you chose). 
  </p>
 <p>
<img src="https://user-images.githubusercontent.com/131130119/232706472-ff638ec1-f929-4861-b6c4-675754255d3d.png" height="80%" width="80%" alt="osTicket - Prerequisites and Installation"/>
  
  <p>When creating the VM, allow it to create a new Virtual Network (Vnet). This is done authomatically during VM creation.</p>
</p>

<br />

<h3><strong>Step 2: On new VM - Install / Enable IIS in Windows WITH CGI</strong></h3>
<p>
<img src="https://user-images.githubusercontent.com/131130119/232729509-e18baa65-40cb-4337-b971-293f240a57e1.png" height="80%" width="80%" alt="osTicket - Prerequisites and Installation"/>
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
<img src="https://user-images.githubusercontent.com/131130119/232734318-4aa5dd01-e47b-48e0-bb31-04ccc4bc6220.png" height="80%" width="80%" alt="osTicket - Prerequisites and Installation"/>
</p>
<p>
Using the this link, download and install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi) https://drive.google.com/file/d/1RHsNd4eWIOwaNpj3JW4vzzmzNUH86wY_/view?usp=share_link . As demonstrated above, it requires just a normal installatiion. 
</p>
<br />

<h3><strong>Step 4: On the VM - install the Rewrite Module (rewrite_amd64_en-US.msi)</strong></h3>
<p>
<img src="https://user-images.githubusercontent.com/131130119/232738850-09179366-1352-4785-bb00-5f56d28097a9.png" height="80%" width="80%" alt="osTicket - Prerequisites and Installation"/>
</p>
<p>
Using the this link, download and install Rewrite Module (rewrite_amd64_en-US.msi)  . 
  https://drive.google.com/file/d/1tIK9GZBKj1JyUP87eewxgdNqn9pZmVmY/view?usp=share_link. As demonstrated above, it requires just a normal installatiion.
</p>
<br />

<h3><strong>Step 5: Create the directory for PHP on our C drive - C:\PHP </strong></h3>
<p>
<img src="https://user-images.githubusercontent.com/131130119/232745560-d2eeb5db-a14a-4143-8ee0-23b2d774df5c.png" height="80%" width="80%" alt="osTicket - Prerequisites and Installation"/>
</p>
<p>
So basically this is to create a folder names PHP on the C drive. So sinply go to the C drive  Right click, go to new and and create a folder. Name it PHP
</p>
<br />

<h3><strong>Step 6: Download PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) and unzip the contents into C:\PHP </strong></h3>
<p>
<img src="https://user-images.githubusercontent.com/131130119/232750070-d2b32012-d092-4e54-83f7-92900545d1a8.png" height="80%" width="80%" alt="osTicket - Prerequisites and Installation"/>
</p>
<p>
So basically this is to download the PHP zip file and extract the content of the file into the previously created folder named PHP on the C drive. So sinply go to the download folder to locate the zip folder and  Right click, to extract in to the PHP folder on the C Drive. (Link below to download)
https://drive.google.com/file/d/1snNMtLdCOpMtkCyD4mvl9yOOmvVIp9fP/view?usp=share_link
</p>
<br />

<h3><strong>Step 7: Download and install VC_redist.x86.exe.</strong></h3>
<p>
<img src="https://user-images.githubusercontent.com/131130119/232861652-4dce1627-53ee-4a07-8003-fe98f204ecd6.png" height="80%" width="80%" alt="osTicket - Prerequisites and Installation"/>
</p>
<p>
Download and install the VC_redist.x86.exe. This is just a normal installation.
https://drive.google.com/file/d/1s1OsGF3-ioO0_9LYizPRiVuIkb3lFJgH/view?usp=share_link
</p>
<br />

<h3><strong>Step 8: Download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi) </strong></h3>
<p>
<img src="https://user-images.githubusercontent.com/131130119/232865934-df77cacb-9f0d-4737-8bf0-deef389255fd.png" height="80%" width="80%" alt="osTicket - Prerequisites and Installation"/>
</p>
<p>
 Pretty simple, just using the link below Download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi)
  --> Typical Setup --> Launch Configuration Wizard (after install) --> Standard Configuration --> make sure you remember the password.

 https://drive.google.com/file/d/1_OWh9p7VQLcrB0q_V7qT8yHl0xo5gv7z/view?usp=share_link
</p>
<br />

<h3><strong>Step 9: Open IIS as an Admin and Register PHP from within IIS  </strong></h3>
<h3><strong>Install osTicket v1.15.8 </strong></h3>
<p>
<img src="https://user-images.githubusercontent.com/131130119/232871745-d00dbceb-f09c-4d3d-8c8c-3c01938fba8f.png" height="80%" width="80%" alt="osTicket - Prerequisites and Installation"/>
</p>
<p>
 Pretty much simple, just using the link below Download and install Install osTicket v1.15.8 (mysql-5.5.62-win32.msi)
  --> Extract the folder --> Copy the upload folder (after extraction) --> Extract and copy “upload” folder to c:\inetpub\wwwroot --> Within c:\inetpub\wwwroot, Rename “upload” to “osTicket”.
https://drive.google.com/file/d/1VeVXKlzHDRjeaVUL99ptq7qYbrbXdFxJ/view?usp=share_link
</p>
<br />

<h3><strong>Step 10: Reload IIS (Open IIS, Stop and Start the server)  </strong></h3>
<h3><strong>Go to sites -> Default -> osTicket (Note that some extensions are not enabled) </strong></h3>
<p>
<img src="https://user-images.githubusercontent.com/131130119/232971750-bea784e5-f807-4e54-9ed8-13f912b6b826.png" height="80%" width="80%" alt="osTicket - Prerequisites and Installation"/>
</p>

<p>
<img src="https://user-images.githubusercontent.com/131130119/232974937-32254e95-0ac2-42fa-8833-efa4739007d0.png" height="80%" width="80%" alt="osTicket - Prerequisites and Installation"/>
</p>

<p>
<img src="https://user-images.githubusercontent.com/131130119/232973047-d14fc0cf-d18f-4e41-b2f1-3d1780b659e8.png" height="80%" width="80%" alt="osTicket - Prerequisites and Installation"/>
</p>
<p>
<img src="https://user-images.githubusercontent.com/131130119/232973364-a3a930dc-88e2-4ab9-8772-2d0b0bd0d23f.png" height="80%" width="80%" alt="osTicket - Prerequisites and Installation"/>
</p>
<p>
<img src="https://user-images.githubusercontent.com/131130119/232975402-0117f99e-77a5-4131-aebd-03a83a992bfe.png" height="80%" width="80%" alt="osTicket - Prerequisites and Installation"/>
</p>
<p>
Go to sites -> Default -> osTicket On the right, click “Browse *:80”. this should display osTicket installer on the web browser. Once that is done you should Note that some extensions are not enabled on the installer as demonstrated above. Go back to IIS, sites --> Default --> osTicket Double-click PHP Manager Click --> “Enable or disable an extension”. Enable these extensions.<br />
Enable: php_imap.dll<br />
Enable: php_intl.dll<br />
Enable: php_opcache.dll<br />
Refresh the osTicket site in your browse, observe the installer if some of the extensions are enabled
</p>
<br />

<h3><strong>Step 11: Rename: ost-config.php and Assign Permissions: ost-config.php </strong></h3>
<p>
<img src="https://user-images.githubusercontent.com/131130119/232978536-da5912b6-7aab-4bbb-8983-2863df05276e.png" height="80%" width="80%" alt="osTicket - Prerequisites and Installation"/>
</p>
<p>
<img src="https://user-images.githubusercontent.com/131130119/232983471-bd78efb2-132e-4278-bec2-20b41a872013.png" height="80%" width="80%" alt="osTicket - Prerequisites and Installation"/>
</p>
<p>
 As demonstrated on the screenshot the file can be located  and retrieved From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php. --> The file ost-sampleconfig.php should be remaned to ost-config.php. (To: C:\inetpub\wwwroot\osTicket\include\ost-config.php). --> Assign Permissions: ost-config.php this can be done the following ways. <br />
  Disable inheritance -> Remove All<br />
  New Permissions -> Everyone -> All<br />
</p>
<br />

<h3><strong> Step 12: Set up osTicket in the browser (click Continue) </strong></h3>
<p>
<img src="https://user-images.githubusercontent.com/131130119/233210759-ccd869bd-8e7d-4d40-bd92-b5043a81e526.png" height="80%" width="80%" alt="osTicket - Prerequisites and Installation"/>
</p>
<p>
<img src="https://user-images.githubusercontent.com/131130119/233210996-51c36462-3149-4799-8e1d-76af71302ebf.png" height="80%" width="80%" alt="osTicket - Prerequisites and Installation"/>
</p>
<p>
Continue Setting up osTicket in the browser (click Continue) --> Name Helpdesk, Default email (receives email from customers). Create the admin profile and fill all necessay information as provided before installation.
</p>
<br />


<h3><strong> Step 13: install HeidiSQL, and Continue Setting up osticket in the browser </strong></h3>
<p>
<img src="https://user-images.githubusercontent.com/131130119/233216999-dd1edf47-d7a9-4c8d-80d8-8b12ca863d91.png" height="80%" width="80%" alt="osTicket - Prerequisites and Installation"/>
</p>
<p>
<img src="https://user-images.githubusercontent.com/131130119/233217127-3321edec-cf7b-4f14-af17-329d1dc1801a.png" height="80%" width="80%" alt="osTicket - Prerequisites and Installation"/>
</p>

<p>
<img src="https://user-images.githubusercontent.com/131130119/233221643-e1b1b38c-4a70-4159-ae7f-8aa37734d497.png" height="80%" width="80%" alt="osTicket - Prerequisites and Installation"/>
</p>

<p>
To continue Setting up osTicket in the browser we have of download and install HeidiSQL. This program allows us to connect to mysql server to setup a database that OsTicket is going to use. So we are going to install HeidiSQL database client. Lunch the HeidiSQL --> create new session --> add paasword (must be remembered to login to the database) --> connect to session --> create database called osTicket.   <br />
</p>
<p>
To continue Setting up osTicket in the browser. Fill in the database information on the osTicket installer<br />
- mySQL Database: osTicket <br />
- mySQL Username: root <br />
- mySQL password: (user defined) <br />
- Click install Now <br />
</p>
<p>
<img src="https://user-images.githubusercontent.com/131130119/233222955-388acc94-496c-4ece-bc59-151083c5fe90.png" height="80%" width="80%" alt="osTicket - Prerequisites and Installation"/>
</p>
<p>
Finishing up <br />
Change permission of include/ost-config.php to remove write access (Set Permissions to “Read” only: C:\inetpub\wwwroot\osTicket\include\ost-config.php) <br />
Delete setup directory (Delete: C:\inetpub\wwwroot\osTicket\setup) <br />
Enable the system
</p>
<p>
Notes: <br />
Browse to your help desk login page: http://localhost/osTicket/scp/login.php  <br />
End Users osTicket URL: http://localhost/osTicket/ 
</p>
<p>
CONGRATULATION YOU HAVE INSTALLED OSTICKET SUCCESSFULLY.
<br />
DONE
</p>
<br />

