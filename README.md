<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Azure Virtual Machine
- Internet Information Services (IIS)
- PHP Manager
- Rewrite Module
- VC Redist
- MySQL
- Heidi SQL
- osTicket v1.15.8
- Link to downloads: https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6


<h2>Installation Steps</h2>


1.) First, you are going to want to create a virtual machine by going to https://portal.azure.com/. Setup your virtual machine with Windows 10 Pro, version 22H2. Depending on what you are trying to accomplish you may need more than 2 vcpus and 16gb or more of ram.

<img width="1238" alt="creating vm for osticket" src="https://github.com/ikcromer30/OSTICKET-PREREQS-INSTALL/assets/157658949/773565fa-931a-4c84-954c-468ef45cc016">
<img width="646" alt="creating vm for osticket 2" src="https://github.com/ikcromer30/OSTICKET-PREREQS-INSTALL/assets/157658949/e07e2fea-346b-4aa7-bb16-e0a4b1e6f3ce">


2.) After you create the virtual machine the next step is to retreive the public ip from the azure portal and log into it via the remote desktop connection app
</p>

 <img width="598" alt="REMOTE DESKTOP login" src="https://github.com/ikcromer30/OSTICKET-PREREQS-INSTALL/assets/157658949/3f80d47f-2ce1-448e-abc7-2d9701e1844c">

  
3.) Once connected open control panel. From the control panel click on programs. Select, Turn Windows features on and off.

<p>
<img width="404" alt="control panel programs" src="https://github.com/ikcromer30/OSTICKET-PREREQS-INSTALL/assets/157658949/ff9a730c-341e-4829-ab14-9fb7f622f500">

</p>
<p>
 <img width="420" alt="turn off windows features" src="https://github.com/ikcromer30/OSTICKET-PREREQS-INSTALL/assets/157658949/87863ee8-fb04-47d4-8f7e-5a18ab41e1a4">

<p>

</p>
<p>
  
4.) Next install / enable IIS in Windows with CGI and Common HTTP Features
Make Sure CGI and Common HTTP Features have an x in the box.

<img width="344" alt="common hhtp" src="https://github.com/ikcromer30/OSTICKET-PREREQS-INSTALL/assets/157658949/2f2c2869-562e-4104-b7be-fc57852b20cc">

</p>
<p>
  
***Make sure all Common HTTP Features are checked.*** 
 
 To make sure the IIS is installed go to a browser of your choice and search for 127.0.0.1  
  
<p>
<img width="634" alt="test for iis install" src="https://github.com/ikcromer30/OSTICKET-PREREQS-INSTALL/assets/157658949/92bf9de5-4810-4682-b33c-34a7ca5a0153">
</p>
<p>
  
  
  
  
5.) With IIS now enabled, From the Installation Files, download and install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi)
  Go through the install wizard and complete the install. Use default settings. 

  
  
6.) Next from the Installation Files, download and install the Rewrite Module (rewrite_amd64_en-US.msi)
  
7.) Create a PHP folder in C: drive.
  
8.) From the Installation Files, download PHP 7.3.8 (php-7.3.88-nts-Win32-VC15-x866.zip) and unzip the contents into C:\PHP

<img width="389" alt="ISS MANAGER SETUP " src="https://github.com/ikcromer30/OSTICKET-PREREQS-INSTALL/assets/157658949/f3f40e27-fca3-4762-a36d-cf0b473a9f02">

  
 If an alert appears saying its already downloaded, press keep anyways.
<p>
<img src="https://imgur.com/YwBhqo0.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>

9.) Once you have downloaded and extracted the zip file into the PHP folder on the C drive, download and install the VC_redist.x86.exe from the installation files. Go through the setup wizard to finish setting up and installing the VC_redist.x86.exe. 

<img width="448" alt="extract to php" src="https://github.com/ikcromer30/OSTICKET-PREREQS-INSTALL/assets/157658949/bad44e08-f3a2-46c6-94dc-7c0015522e1a">

  
10.) Download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi)
  Run the setup wizard:
Typical Setup ->
Launch Configuration Wizard (after install) ->
Standard Configuration ->

  Make the new root password: Password1
  
<p>
<img src="https://imgur.com/KxcUy7C.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  Execute the process on the next page.
  
<p>
<img src="https://imgur.com/i7sn6hT.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
11.) Now that the files are installed we will want to search for IIS in the windows search bar. Run IIS as an administrator.
  
  
<p>
<img width="256" alt="Screenshot 2024-01-24 235043" src="https://github.com/ikcromer30/OSTICKET-PREREQS-INSTALL/assets/157658949/b2111c5b-79cf-4e40-bc79-dd5301c379b0">

</p>
<p>
  
12.) Next register PHP from within IIS.
  Click on PHP Manager
  
<p>
<img width="611" alt="php manager " src="https://github.com/ikcromer30/OSTICKET-PREREQS-INSTALL/assets/157658949/f12ca3ca-00ac-48f6-b706-da8c4003eeaf">

</p>
<p>
  
Register new PHP version.
  
<p>
<img src="https://imgur.com/qdbn5zQ.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
You will want to provide a path to the php executable file (php-cgi.exe)). 
  Go to C Drive -> PHP -> click on php-cgi file.
  
<p>
<img width="610" alt="Register new php" src="https://github.com/ikcromer30/OSTICKET-PREREQS-INSTALL/assets/157658949/c94991aa-b2e1-4daa-879f-9ba020e4bfaa">

</p>
<p>
  
  Restart the IIS server.
  
<p>
<img src="https://imgur.com/CJ3RUbG.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
13.) Install osTicket v1.15.8
  -Download osTicket from the Installation Files Folder
  -Extract and copy "upload" folder to c:\inetpub\wwwroot
  -Within c:\inetpub\root, Rename "upload" to "osTicket"

  <img width="808" alt="EXTRACT OSTICKET TO WWWROOT" src="https://github.com/ikcromer30/OSTICKET-PREREQS-INSTALL/assets/157658949/f2bc09d0-ff4f-460d-bb6c-cf615570380c">

  
  Reload IIS again.
  
14.) On IIS go to sites -> Default -> osTicket
  -On the right, click “Browse *:80”
  
<p>
<img width="611" alt="after restar os ticket iis" src="https://github.com/ikcromer30/OSTICKET-PREREQS-INSTALL/assets/157658949/f4bd2de4-87f6-4f55-a140-0cb19d173c2c">

</p>
<p>
  
  Some extensions are not enabled on the osTicket browser.
  
<p>
<img src="https://imgur.com/eJIsGTn.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  To enable the extensions:
  -Go back to IIS, sites -> Default -> osTicket
  -Double click PHP manager
  -Click "Enable or disable an extension"
  
<p>
<img width="611" alt="php manager " src="https://github.com/ikcromer30/OSTICKET-PREREQS-INSTALL/assets/157658949/b6089859-e605-4b2a-b9be-082a8f849934">

</p>
<p>
  
<p>
<img width="607" alt="enable extension osticket" src="https://github.com/ikcromer30/OSTICKET-PREREQS-INSTALL/assets/157658949/cf9977ac-cff9-40f0-bf5d-99b3bf1f6ae0">

</p>
<p>
  
  We will want to enable three extensions from here.
  
  1.) php_imap.dll
 
  2.) php_intl.dll
  
  3.) php_opcache.dll
  
<p>
<img width="297" alt="3 extentions" src="https://github.com/ikcromer30/OSTICKET-PREREQS-INSTALL/assets/157658949/3956620c-1d6b-4420-9162-d2a5526892eb">

</p>
<p>
  
  
15.) Once we have those extensions enabled in IIS, we are going to want to rename one of the files in our osTicket folder.
  Go into the file explorer and search for C;\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
  
  We are going to rename the ost-sampleconfig.php to ost-config.php

<img width="452" alt="change config " src="https://github.com/ikcromer30/OSTICKET-PREREQS-INSTALL/assets/157658949/6068dac0-5a0a-439d-916d-311616ba88b0">

  
 Once we have renamed the files, right click on the file and go to properties.
 Click security, click on advance, and disable the inheritance.
 We will select Remove all inherited permissions from this object.

 <img width="866" alt="disable inheritance" src="https://github.com/ikcromer30/OSTICKET-PREREQS-INSTALL/assets/157658949/18496cdd-06e1-4647-a4a4-4878d723431a">

  
  Now we will add new permissions.

  
 <img width="700" alt="add permissions" src="https://github.com/ikcromer30/OSTICKET-PREREQS-INSTALL/assets/157658949/3afb8194-17f1-4ffd-96e2-25f3864981c6">

  
  Make sure Full Control and all the other boxes are checked.
  
<p>
<img src="https://imgur.com/rbbGqwB.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  Click Apply and Ok.
  
<p>
<img src="https://imgur.com/saRO3y5.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  Once that is done we will continue to setup osTicket in the browser. Click Continue on the osTicket browser page.
  Fill out the page as required except the Database Settings at the bottom of the page. We will get to that. 
  
  We will want to download and install HeidiSQL from the Installation Files. 
  
<p>
<img src="https://imgur.com/i7a4gWC.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  When the program is open we will create a new session in it.
  
<p>
<img src="https://imgur.com/g5M1i61.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  We want to make sure the username is root and the password is Password1.
  
<p>
<img src="https://imgur.com/LEAZNOc.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  Once we are connected to the session we will go back to the browser to finish setting everything up. Under the Database Settings in the browser the username will be root and the password will be Password1.
  
  We will now create a new database within HeidiSQL. In Heidi right click on the left side where is says "Unnamed", select "create new", and then select "database". Name the new database osTicket. Once we have the new database setup go back to the osTicket browser and under MySQL Database type in osTicket.
  
<p>
<img src="https://imgur.com/0rG1AJm.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  The last step is to do some clean up. We will want to delete the setup folder in our system. 
  -Delete: C:\inetpub\wwwroot\osTicket\setup
  Only delete the setup folder and nothing else.
  
  We then will want to set the permissions back to "Read" only in the ost-config.php file.
  
<p>
<img src="https://imgur.com/wFr0pkK.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
<p>
<img src="https://imgur.com/jsJOPyn.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  The last step after that is to login to osTicket on the browser.
  
<p>
<img src="https://imgur.com/uHVdDsx.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  Congrats! You have now successfully installed and setup osTicket!
