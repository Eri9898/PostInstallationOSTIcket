# PostInstallationOSTIcket
<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Post Installation and Configuration</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Computer)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Enable IIS
- Install Web Platform Installer
- Install My SQL (Set up Username and Passwoord)
- Install C++ Redistributable
- Configure Permissions and Install OSTicket

<h2>Post Installation Steps</h2>

<p>

<img src="https://imgur.com/XwSqfve.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

1. In the browser search for the admin login page for os ticket. http://localhost/osTicket/scp/login.php Use the admin credentials you created to login. 
</p>
<p>

</p>
<br />

<p>
<img src="https://imgur.com/C1Lk9tK.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
2. So first you will be creating roles aka permissions for users. Click on the admin panel (when you click on admin panel it will then display as agent on the top right, you’re still on the admin page unless you click on agent panel then it will switch), on the top right corner of the page, then click agents,  then below that click roles. On the top right corner of this page click add new role.

After you click roles you will be prompted to create a name for the role, name it “Admin” then on the tab next to it click on permissions. Click all permissions for this lab (usually in real life roles should have the least amount of access necessary to do their job, but for the lab’s sake just check everything)  click add role after choosing permissions.

</p>
<br />
3. Next you will configure departments in osTicket. Click the admin Panel, then agents and then go to  Departments. Within the admin panel click add new department in upper right.  (And create with the default SLA for now). Create a new top level department called System Administrators (or whatever you wish for your lab).
Name: 
Status: Active
SLA: Default for now
Type:Public

</p>
<br />
4. Then you’ll configure Teams which allows you to make teams with agents from different departments to solve certain issues. 
Go to the Admin Panel, then Agents, then Teams.  Click add new team on the right.
Create a Level I Support status= active everything else is default
Create Level II Support, status=active 

</p>
<br />
</p>
<br />
<img src="https://imgur.com/GwE2WGF.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
5. Next you must allow end users to be able to anonymously create tickets without login info. So to do that head to admin Panel then settings, then user and then settings again. Uncheck Registration Required box. 
</p>
<br />
<h2>Configuration Steps</h2>
</p>
<br />
1. Configure Agents next. Head to admin Panel, agents, then add new. Under the account tab, enter a name.Then add an email @osticket.com Create the users’ credentials, dont forget them! Uncheck the boxes “require to change password” or “send password reset email”, hit set.
Under the access tab select the department system administrators (Or whatever name you chose), and select the role admin. Under extended access select support department so that the AGent can see tickets)** redo
Go to the teams (lowest tab next to access) and add level 2 support 
Click create
 
</p>
<br />
2. Now you will add your new SLA plans. Go to admin panel, then manage, then SLA.
	-Enter a name
-Select schedule, what days of the week
-Grace period, how soon it must be resolved.
-add plan
-Now you can go back to departments (see step 3 for how to get to departments if needed). Click on ea department and then from the SLA tab you can expand the list and choose from the SLAs you created. You do not need to select anything for schedule.


</p>
<br />
</p>
<br />
<img src="https://imgur.com/yA0dnbM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
3. Next you will configure help topics. This is a list that will pop up for end users when they want to select what general issue they have when creating their tickets. 
Click on Admin Panel, then manage then help topics.Click add new.
-Topic: Whatever issue you want to name ex. Computer issues or password reset
                       Status=active
                       Parent topic= top level 

</p>
<br />
4. Next download Microsoft Visual C + + (VC_redist.x86.exe.) 
https://www.microsoft.com/en-us/download/details.aspx?id=52685
</p>
<br />
5.  Next Install a database ((mysql-5.5.62-win32.msi)
Select the typical install, click finish to launch the configuariation wizard. Within that check standard configuaration and install.
Create your credentials for the database, your username will automatically be “root”. So create your password.  Do not forget it! Then execute.
</p>
<br />
6. Next search IIS on the windows start menu, right click and open as admin.
</p>
<br />
</p>
<br />
<img src="https://imgur.com/s5jUSDP.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
13. Open the PHP manager that was installed earlier. Click register and it will ask for a location, click the three dots. Locate file C:\PHP\CGI and select it.
</p>
<br />
</p>
<br />
<img src="https://imgur.com/5AHq3tk.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
14. Refresh IIS AFTER selecting the file.
 Then download OSTicket (osTicket v 1.12.8) onto the machine. 
Open the OSTicket file, extract and copy the zipped file "Upload" within it. Copy it into c:\inetpub\wwwroot
</p>
<br />
15. Within c:\inetpub\wwwroot rename the upload file to "OSTicket"
</p>
<br />
</p>
<br />
<img src="https://imgur.com/fMTpCKA.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
16. Reload IIS again and in the upper left corner go click on Ticket\YourName> Sites> Default> osTicket. On the right side of the screen click “Browse *:80” and the welcome webpage to IIS should load. It says “Thanks for choosing osTicket!”
</p>
<br />
17. On that same page, Ticket\YourName> Sites> Default> osTicket.  Double-click PHP Manager within OSticket. Click “Enable or disable an extension”
Enable: php_imap.dll
Enable: php_intl.dll
Enable: php_opcache.dll
Then Refresh osTicket Browser
</p>
<br />
18. Rename ost-sampleconfig.php to ost-config.php
It is located in
C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
</p>
<br />
</p>
<br />
<img src="https://imgur.com/t2GHOsE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
19. Next you will assign permissions to ost-config.php.  Right click to properties and go to security. Click advanced then disable inheritance, click remove all permissions. Next click add, click select principle and type everyone and click ok. Check box “full control” and apply.
</p>
<br />
20. Instal HeidiSQL ((((NAME)))  so that you can connect to MySQL. Open the file and install it. The app shoud open after install. On the bottom left click new, then enter username:Root then password:
Create a new session, enter username and passowrd.
</p>
<br />
21. Create a new session and connect to it by clicking open.  
</p>
<br />
</p>
<br />
<img src="https://imgur.com/Tcf1nhi.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
22. In Heidi right click unnamed in upper left corner, then click create new then database.then name it osTIcket then say ok
</p>
<br />
</p>
<br />
<img src="https://imgur.com/GPlKJnb.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
23. Continue Setting up osTicket in the ISS webpage, click next. Next fill out the system settings and in database settings enter your MY SQL 
MySQL Table Prefix: ost-config.php
MySQL Database: osTicket
MySQL Username: root
MySQL Password: ***** whatever you created
Click “Install Now!”
</p>
<br />
24. OS TIcket should then load up with a welcome screen. Congratulations you just installed os Ticket! c: 
