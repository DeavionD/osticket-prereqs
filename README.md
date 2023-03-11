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

- Set up an Azure Windows 10 Virtual machine.
- Install / Enable IIS in Windows WITH CGI
- Install PHP Manager for IIS, Install Rewrite Module, download PHP, install C++ redistributable, and install MySQL.
- Set up MySQL
- Register PHP from within IIS
- Install osTicket
- Configure osTicket
- Clean up / Test


<h2>Installation Steps</h2>

<p>
<img src="https://i.imgur.com/umlVZC9.png" height="70%" width="70%" alt=""/>
</p>
<p>
1. The first step was to create a new resource group and VM in Azure. I created a resource group named "osTicket" and inside that group I created a Windows 10 VM and named it "VM-osTicket".
</p>
<br />

<p>
<img src="https://i.imgur.com/OpFLfOA.png" height="70%" width="70%" alt=""/>
</p>
<p>
2. Next, I opened VM-osTicket and enabled IIS with CGI using the following steps: open the Control Panel -> click Programs -> click "turn windows features on or off", next find "Internet Information Services", enable it and expand it, -> expand "World Wide Web Services" -> expand "Application Development Features",  find CGI and enable it, then click o
</p>
<br />

<p>
<img src="https://i.imgur.com/XwBxAWw.png" height="70%" width="70%" alt=""/>
</p>
<p>
<img src="https://i.imgur.com/iiCHSwJ.png" height="70%" width="70%" alt=""/>
</p>
<p>
<img src="https://i.imgur.com/GgTM5Ap.png" height="70%" width="70%" alt=""/>
</p>
<p>
3. Next, download and install prereq files. 1. "PHP Manager"(https://drive.google.com/file/d/1RHsNd4eWIOwaNpj3JW4vzzmzNUH86wY_/view). 2. "Rewrite Module"(https://drive.google.com/file/d/1tIK9GZBKj1JyUP87eewxgdNqn9pZmVmY/view?usp=share_link). 3. "PHP 7.3.8"(https://drive.google.com/file/d/1snNMtLdCOpMtkCyD4mvl9yOOmvVIp9fP/view?usp=share_link) - download this entire folder, create a new folder in the windows C drive, and name it "PHP". Once "PHP 7.3.8" is downloaded, right-click it and extract the contents into that C:\PHP folder that you created. (example above). 4. "C++ redistributable"(https://drive.google.com/file/d/1s1OsGF3-ioO0_9LYizPRiVuIkb3lFJgH/view?usp=share_link). 5. "MySQL" (https://drive.google.com/file/d/1_OWh9p7VQLcrB0q_V7qT8yHl0xo5gv7z/view?usp=share_link) - be sure to click "Typical" install(example above).
</p>
<br />

<p>
<img src="https://i.imgur.com/ePz8ouT.png" height="70%" width="70%" alt=""/>
</p>
<p>
4. Next, set up MySQL. Launch MySQL, press next -> press standard configuration -> press next again -> create a password then press next, and finally press execute. A database is now installed on the VM which is used for osTicket.
</p>
<br />

<p>
<img src="https://i.imgur.com/NkSs7Ca.png" height="70%" width="70%" alt=""/>
</p>
<p>
5. Next, register PHP from within IIS. Go to the start menu -> search IIS and run it as an admin. Double click PHP manager -> click "register new PHP version" -> browse for the PHP folder we created in the C drive earlier -> open the folder and click "php-cgi" -> next press ok. Finally, restart the server -> click on the name of the server then click restart in the right-hand corner.
</p>
<br />

<p>
<img src="https://i.imgur.com/6LIzYvH.png" height="70%" width="70%" alt=""/>
</p>
<p>
<img src="https://i.imgur.com/83kCjI8.png" height="70%" width="70%" alt=""/>
</p>
<p>
<img src="https://i.imgur.com/Gxpa19I.png" height="70%" width="70%" alt=""/>
</p>
<p>
6. Next, install osTicket(https://drive.google.com/drive/u/1/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6). Download osTicket from the link -> click the folder and drag the “upload” folder to "c:\inetpub\wwwroot" (example above). Next, rename the "upload" folder to "osTicket". Next, reload IIS -> open IIS -> click the server name and press restart. Next, while in IIS, go to sites -> Default -> osTicket. Then on the right click "Browse *:80". If done correctly, your screen should look like image 3 above.
</p>
<br />

<p>
<img src="https://i.imgur.com/YsuQJbI.png" height="70%" width="70%" alt=""/>
</p>
<p>
<img src="https://i.imgur.com/1xNJ3lG.png" height="70%" width="70%" alt=""/>
</p>
<p>
<img src="https://i.imgur.com/6EvxAI6.png" height="70%" width="70%" alt=""/>
</p>
<p>
<img src="https://i.imgur.com/3hp6zXt.png" height="70%" width="70%" alt=""/>
</p>
<p>
6. Next, go back to IIS, click sites -> Default -> osTicket, double click PHP Manager, then click "Enable or disable an extension". Next, enable "php_imap.dll", "php_intl.dll", and "php_opcache.dll". Next, in the file manager go to : "C:\inetpub\wwwroot\osTicket\include" and rename "ost-sampleconfig.php" to "ost-config.php". Next, right-click "ost-config.php", click properties -> security -> advanced, then press "Disable inheritance", then remove all. Then, press "Add" -> "select principal", and type everyone -> press check -> press ok -> then click "full control" -> press ok ->then press apply to give everyone permission.
</p>
<br />

<p>
<img src="https://i.imgur.com/UtJPJtZ.png" height="70%" width="70%" alt=""/>
</p>
<p>
<img src="https://i.imgur.com/grfkfbd.png" height="70%" width="70%" alt=""/>
</p>
<p>
<img src="https://i.imgur.com/9HkvWJZ.png" height="70%" width="70%" alt=""/>
</p>
<p>
7. Next, download and install HeidiSQL(https://www.heidisql.com/installers/HeidiSQL_12.3.0.6589_Setup.exe). This will allow us to connect to the SQL server and set up a database for osTicket. After installing, run Heidi and click "New". Enter the password you created for SQL and press "open". Right-click "Unnamed" -> click "create new database" -> name the database osTicket. Next, go back to the browser and go to the osTicket installer page -> fill out the information. In the Database Settings, type in "root" for "MySQL Username", enter the password you created, then for "MySQL Database" enter "osTicket". Next, press "install now". If done correctly, your screen should look like images 2 and 3 above.
</p>
<br />

<p>
<img src="https://i.imgur.com/75K0lVJ.png" height="70%" width="70%" alt=""/>
</p>
<p>
<img src="https://i.imgur.com/dhykFkj.png" height="70%" width="70%" alt=""/>
</p>
<p>
8. Lastly, in the file manager, go to "C:\inetpub\wwwroot\osTicket" and delete the setup folder. Next, go to "C:\inetpub\wwwroot\osTicket\include" -> scroll down to "ost-config.php" and change the permissions back to "read-only". Right-click "security" -> "advanced" -> "everyone" -> "edit", now uncheck "modify" and "write". Press ok, and apply the changes. This completes the prereqs and initial installation of osTicket. Use this link(http://localhost/osTicket/scp/login.php), if all steps were done correctly, you should be able to log in.
</p>
<br />
