# PostInstallationOSTicket
<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Post Installation and Configuration</h1>
This tutorial covers the post-installation setup of the open-source help desk ticketing system osTicket, including role creation, department organization, SLA configuration, and user/agent setup for a functional ticketing workflow.<br />

<h2>Environments and Technologies </h2>

- Microsoft Azure – Virtual Machine hosting
- Remote Desktop – VM access
- Internet Information Services (IIS) – Web hosting for osTicket

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- IIS Installed & Enabled
- Web Platform Installer Installed
- MySQL Installed (with username/password configured)
- C++ Redistributable Installed
- osTicket Installed & Permissions Configured

<h2>Post Installation and Configuration Steps</h2>

<p>

<img src="https://imgur.com/XwSqfve.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

1. Navigate to the admin login page for os ticket. http://localhost/osTicket/scp/login.php Use the admin credentials you created to login. Please note, this website can only be accessed if IIS is installed.
</p>
<p>

</p>
<br />
</p>
<br />

<p>
<img src="https://imgur.com/C1Lk9tK.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
2. So first you will be creating roles aka permissions for users. Click on the admin panel,>agents>roles.
</p>
On the top right corner of this page click add new role.
</p>
After you click roles you will be prompted to create a name for the role, name it “Admin” then on the tab next to it click on permissions.
</p>
Click all permissions (usually in real life roles should have the least amount of access necessary to do their job)  click add role after choosing permissions.
</p>
<br />
</p>
<br />
<img src="https://imgur.com/GFaPxaf.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
3. Next you will configure departments in osTicket. Click the admin Panel>agents>Departments. 
</p>
Within the admin panel click add new department in upper right.  
</p>
(And create with the default SLA for now). 
</p>
Create a new top level department called System Administrators (or whatever you wish).
</p>
Name: 
</p>
Status: Active
</p>
SLA: Default (for now)
</p>
Type:Public

</p>
<br />
4. Then you’ll configure Teams which allows you to make teams with agents from different departments to solve certain issues. 
</p>
Go to the Admin Panel>Teams.  Click add new team on the right.
</p>
Create a Level I Support "status= active", everything else on this page is default.
</p>
Create Level II Support, "status=active " as well.

</p>
<br />
</p>
<br />
<img src="https://imgur.com/LVNYJG2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
5. Next you must allow end users to be able to anonymously create tickets without login info. 
</p>
So to do that head to admin Panel>settings>user>settings
</p>
Uncheck Registration Required box. 
</p>
<br />
</p>
<br />
<img src="https://imgur.com/kY6gu50.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
6. Next you'll configure Agents next. Admin Panel>agents, and click add new on this page. 
</p>
Under the account tab, enter a name.Then add an email @osticket.com 
</p>
Create the users’ credentials, don't forget them!
</p>
Uncheck the boxes “require to change password” or “send password reset email”, hit set.
</p>
Under the access tab select the department system administrators (Or whatever name you chose), and select the role admin. 
</p>
Under extended access select support department so that the Agent can see tickets)
</p>
Go to the teams (lowest tab next to access) and add level 2 support 
Click create
</p>
<br />
7. Next you can create non-admin users for osTicket.
Stay on the admin panel> Agents> create new Agents.  On this page input their name and email "@osticket.com". Do not check the admin box. Go to the access tab and give your non-admins permisions. Give them departments and for Role it will be "limited access".
</p>
<br />
</p>
<br />
<img src="https://imgur.com/WhaOpGP.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
8. Now you will add your new SLA plans. Go to admin panel> manage> SLA> Add new
</p>
-Enter a name
</p>
-Select schedule, what days of the week
</p>
-Grace period, how soon it must be resolved.
</p>
-add plan
</p>
-Now you can go back to departments (see step 3 for how to get to departments if needed). 
</p>
Click on ea department and then from the SLA tab you can expand the list and choose from the SLAs you created. You do not need to select anything for schedule.


</p>
<br />
</p>
<br />
<img src="https://imgur.com/KGGPYvj.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
9. Next you will configure help topics. This is a list that will pop up for end users when they want to select what general issue they have when creating their tickets. 
Click on Manage> Help topics 
</p>
-Click add new
</p>
-Topic: Whatever issue you want to name ex. Computer issues or password reset
</p>
-Status=active
</p>
-Parent topic= top level 
</p>
10. You are now done configuring the Admin roles, Agents roles, End User accounts, SLAs, and Help Topics. Now osTicket can be utilized, which will be shown in the next lab!
