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

- Download [osTicket-Installation-Files.zip](https://drive.usercontent.google.com/download?id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD&export=download&authuser=1)  and unzip it onto your desktop. The folder should be called “osTicket-Installation-Files”
- Enable IIS with CGI in windows settings (World Wide Web Services -> Application Development Features -> [X] CGI)
- Install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi)
- Install rewrite_amd64_en-US.msi

<h2>Installation Steps</h2>


Begin by creating a directory called "PHP" on the root of the C Drive. (C:\PHP)


<img src="https://i.imgur.com/QJn8OEM.png" alt="Create C Directory"/>

Next install [VC redist.x86.exe](https://drive.google.com/file/d/1s1OsGF3-ioO0_9LYizPRiVuIkb3lFJgH/view) as well as [MySQL 5.5.62-win32.msi](https://drive.google.com/file/d/1_OWh9p7VQLcrB0q_V7qT8yHl0xo5gv7z/view) which are both found in the "osTicket-Installation-Files” folder.

Now lets configure MySQL
  - Pick Typical setup
  - Launch Configuration Wizard (after install)
  - Standard Configuration
  - for the sake of the tutorial we are going to make the username AND password "root" (make this something secure that nobody else knows.)

<h1>Setting up IIS and installing osTicket</h1>
  
- Run IIS as admin
- Register PHP from within IIS (PHP Manager -> C:\PHP\php-cgi.exe)
- Reload IIS (Open IIS, Stop and Start the server)
<img src="https://i.imgur.com/mWoAQP2.png" alt="Register PHP"/>
<img src="https://i.imgur.com/kK6LM2Q.png" alt="Register PHP 1"/>
<img src="https://i.imgur.com/UCLhb1w.png" alt="Register PHP 2"/>

<h2>Setting up osTicket</h2>

Now lets install osTicket
  
- From the “osTicket-Installation-Files” folder, unzip “osTicket-v1.15.8.zip” and copy the “upload” folder into “c:\inetpub\wwwroot”
- Within “c:\inetpub\wwwroot” Rename “upload” to “osTicket” <-- Ensure its spelled EXACTLY like this.
<img src="https://i.imgur.com/6mryAvC.png" alt="osTicket"/>
 

- Reload IIS (Open IIS, Stop and Start the server)
- Go to sites -> Default -> osTicket
    - On the right, click “Browse *:80”
<img src="https://i.imgur.com/QoisAKS.png" alt="osTicket 1"/>
<img src="https://i.imgur.com/5eN2y4d.png" alt="osTicket 2"/>

- Go back to IIS, sites -> Default -> osTicket
- Double-click PHP Manager
- Click “Enable or disable an extension”
    - Enable: php_imap.dll
    - Enable: php_intl.dll
    - Enable: php_opcache.dll
- Refresh the osTicket site in your browser, observe the changes
<img src="https://i.imgur.com/dJjBKvk.png" alt="osTicket 3"/>
<img src="https://i.imgur.com/RuPkGVg.png" alt="osTicket 3"/>
<img src="https://i.imgur.com/FiugLV6.png" alt="osTicket 4"/>
<img src="https://i.imgur.com/Fs0vbdA.png" alt="osTicket 5"/>

- Rename: ost-config.php
    - From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
    - To: C:\inetpub\wwwroot\osTicket\include\ost-config.php
<img src="https://i.imgur.com/V7g9m9e.png" alt="osTicket 6"/>

- Assign Permissions: ost-config.php
    - Disable inheritance -> Remove All
    - New Permissions -> Everyone -> All
<img src="https://i.imgur.com/1L1n0d9.png" alt="osTicket 7"/>
<img src="https://i.imgur.com/XSB8ofc.png" alt="osTicket 8"/>

- Continue Setting up osTicket in the browser (click Continue)
    - Name Helpdesk
    - Default email (receives email from customers)

- From the “osTicket-Installation-Files” folder, install [HeidiSQL](https://docs.google.com/document/u/1/d/1WovrX2DaS9xkfaSr4LXyB4YnnWpXIgPCMMbbfgHmGVw/edit).
    - Open Heidi SQL
    - Create a new session, root/root
    - Connect to the session
    - Create a database called “osTicket”
<img src="https://i.imgur.com/TJsiPlW.png" alt="osTicket 9"/>
<img src="https://i.imgur.com/3wlehYn.png" alt="osTicket 10"/>
<img src="https://i.imgur.com/QSqzPxi.png" alt="osTicket 11"/>

- Continue Setting up osTicket in the browser
    - MySQL Database: osTicket
    - MySQL Username: root
    - MySQL Password: root
    - Click “Install Now!”
<img src="https://i.imgur.com/1IQ23cc.png" alt="osTicket 12"/>

- You have now installed and can use osTicket!
    - Browse to your help desk login page: [http://localhost/osTicket/scp/login.php](http://localhost/osTicket/scp/login.php)
    - End Users osTicket URL: [http://localhost/osTicket/](http://localhost/osTicket/ )







