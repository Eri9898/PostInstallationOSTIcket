# PostInstallationOSTicket
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

<h2>Post Installation and Configuration Steps</h2>

<p>

<img src="https://imgur.com/XwSqfve.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

1. In the navigation bar of your browser go to the admin login page for os ticket. http://localhost/osTicket/scp/login.php Use the admin credentials you created to login. Please note, this website can only be accessed if IIS is installed.
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
2. So first you will be creating roles aka permissions for users. Click on the admin panel (when you click on admin panel it will then display as agent on the top right, you’re still on the admin page unless you click on agent panel then it will switch), on the top right corner of the page, then click agents,  then below that click roles. On the top right corner of this page click add new role.

After you click roles you will be prompted to create a name for the role, name it “Admin” then on the tab next to it click on permissions. Click all permissions for this lab (usually in real life roles should have the least amount of access necessary to do their job, but for the lab’s sake just check everything)  click add role after choosing permissions.
</p>
<br />
</p>
<br />
<img src="https://imgur.com/GFaPxaf.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
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
Create a Level I Support "status= active", everything else on this page is default.
Create Level II Support, "status=active " as well.

</p>
<br />
</p>
<br />
<img src="https://imgur.com/LVNYJG2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
5. Next you must allow end users to be able to anonymously create tickets without login info. So to do that head to admin Panel then settings, then user and then settings again. Uncheck Registration Required box. 
</p>
<br />
</p>
<br />
<img src="https://imgur.com/kY6gu50.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
6. Configure Agents next. Head to admin Panel, agents, then add new. Under the account tab, enter a name.Then add an email @osticket.com Create the users’ credentials, don't forget them! Uncheck the boxes “require to change password” or “send password reset email”, hit set.
Under the access tab select the department system administrators (Or whatever name you chose), and select the role admin. Under extended access select support department so that the Agent can see tickets)
Go to the teams (lowest tab next to access) and add level 2 support 
Click create
</p>
<br />
7. Next you can create users (customers) for osTicket.
Click on the Agent Panel on the top right, then Users. Input their name and email "@osticket.com", then click Add New. 
</p>
<br />
</p>
<br />
<img src="https://imgur.com/WhaOpGP.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
8. Now you will add your new SLA plans. Go to admin panel, then manage, then SLA.
	-Enter a name
-Select schedule, what days of the week
-Grace period, how soon it must be resolved.
-add plan
-Now you can go back to departments (see step 3 for how to get to departments if needed). Click on ea department and then from the SLA tab you can expand the list and choose from the SLAs you created. You do not need to select anything for schedule.


</p>
<br />
</p>
<br />
<img src="https://imgur.com/KGGPYvj.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
9. Next you will configure help topics. This is a list that will pop up for end users when they want to select what general issue they have when creating their tickets. 
Click on Admin Panel, then manage then help topics.Click add new.
-Topic: Whatever issue you want to name ex. Computer issues or password reset
                       Status=active
                       Parent topic= top level 

