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
- osTicket Installed & Config File Permissions Set

<h2>Post Installation and Configuration Steps</h2>

<p>

<img src="https://imgur.com/XwSqfve.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

1. Navigate to the admin login page for osTicket. http://localhost/osTicket/scp/login.php (For secure management, it’s critical to serve the osTicket admin portal over HTTPS to encrypt credentials and data in transit.) Use the admin credentials you created to login. Please note, this website can only be accessed if IIS is installed. 
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
2. So first you will be creating roles aka permissions for users. Click on the admin panel>agents>roles.
</p>
On the top right corner of this page click add new role.
</p>
After you click roles you will be prompted to create a name for the role, name it “Admin” then on the tab next to it click on permissions.
</p>
Click all permissions (in real life roles should have the least amount of access necessary to do their job)  click add role after choosing permissions.
</p>
<br />
</p>
<br />
<img src="https://imgur.com/GFaPxaf.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
3. Next you will configure departments in osTicket. Click the admin Panel>Agents>Departments. 
</p>
Within the admin panel click add new department in upper right.  
</p>
(And create with the default SLA for now). 
</p>
Create a new top level department called System Administrators. This separation limits ticket visibility and privileges by department, reducing insider threat risk.
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
4. Then you’ll configure Teams which allows you to make teams with agents from different departments. 
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
5. Next you must allow end users to be able to create tickets without login info. 
</p>
So to do that head to admin Panel>Settings>User>Settings
</p>
Uncheck Registration Required box. 
</p>
open ticket submission reduces friction but keep monitoring for spam or abuse.
</p>
<br />
</p>
<br />
<img src="https://imgur.com/kY6gu50.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
6. Next you'll configure Agents next. Admin Panel>Agents, and click add new on this page. 
</p>
Under the account tab, enter a name.Then add an email @osticket.com 
</p>
Create the users’ credentials, don't forget them! Use strong password policies (like complexity requirements and password expiration) and consider enforcing multi-factor authentication (if supported) to lock down credentials.
</p>
Under the access tab select the department system administrators (Or whatever name you chose), and select the role admin. 
</p>
Under extended access select support department so that the Agent can see tickets
</p>
Go to the teams (lowest tab next to access) and add level 2 support 
Click create
</p>
<br />
7. Next you can create non-admin users for osTicket.
Stay on the Admin panel> Agents> create new Agents.  On this page input their name and email "@osticket.com". Do not check the admin box. Go to the access tab and give your non-admins permisions. Give them departments and for Role it will be "limited access".
</p>
<br />
</p>
<br />
<img src="https://imgur.com/WhaOpGP.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
8. Now you will add your new SLA plans. Go to Admin panel> Manage> SLA> add new
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
-Topic: Most common issues ex. Computer issues or password reset
</p>
-Status=active
</p>
-Parent topic= top level 
</p>
10. You are now done configuring the Admin roles, Agents roles, End User accounts, SLAs, and Help Topics. 
</p>
<br />
11. As mentioned previously, lock down ost-config.php and its folder after installation with least privilege (remove write for everyone except the service account). Regularly patch Windows, IIS, PHP, MySQL, and osTicket itself. Monitor IIS logs and MySQL logs for suspicious activity consider using IDS (Snort)/IPS or SIEM. 
Now osTicket can be utilized, which will be shown in the next lab!
