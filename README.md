<h1>Installing Active Directory</h1>

<h2>Overview:</h2>

- <b>Install Active Directory Domain Services – Promote DC-1 as a new forest (e.g., mydomain.com).</b> 
- <b>Create Domain Admin User – Set up a new domain admin account (jane_admin).</b>
- <b>Join CLIENT-1 to the Domain – Connect CLIENT-1 to the domain and verify in ADUC.</b>

<h2>Install Active Directory</h2>

Login to DC-1 <br/>
Go to Server Manager -> Dashboard <br/>
Click Add Roles and Features <br/>

![](https://github.com/rbrianshutt/active_directory/blob/main/Active%20Directory%202.0/3.1%20add%20roles%20and%20features.PNG)
<br />
In Before you Begin and Installation Type click Next on the default setting  <br/>
Select Server from server pool  <br/>
Click Next <br/>

![](https://github.com/rbrianshutt/active_directory/blob/main/Active%20Directory%202.0/3.2%20server%20selection.PNG)
<br />

In Select Server Roles, click Active Directory Domain Services <br/>
Click Next <br/>

![](https://github.com/rbrianshutt/active_directory/blob/main/Active%20Directory%202.0/3.3%20active%20directory%20domain%20services.PNG)
<br />

 Click Add Features  <br/>

![](https://github.com/rbrianshutt/active_directory/blob/main/Active%20Directory%202.0/3.4%20add%20features.PNG)
<br />

Notice Acitve Directory Domain Services is checked <br/>
Click Next <br/>

![](https://github.com/rbrianshutt/active_directory/blob/main/Active%20Directory%202.0/3.5%20ad%20domain%20services%20checked.PNG)
<br />

Check Restart the destination server automatically if required. Click Yes for warning.  <br/>
Click Install <br/>

![](https://github.com/rbrianshutt/active_directory/blob/main/Active%20Directory%202.0/3.6%20restart%20destination%20server%20if%20required.PNG)
<br />

Installing...  <br/>

![](https://github.com/rbrianshutt/active_directory/blob/main/Active%20Directory%202.0/3.7%20installation%20progress.PNG)
<br />

Click on yellow warning triagle <br/>
Click Promote this server to a domain controller<br/>

![](https://github.com/rbrianshutt/active_directory/blob/main/Active%20Directory%202.0/4.1%20promote%20server%20to%20a%20dm.PNG)
<br />

Deployment Configuration<br/>
Select Add a new forest for deployment operation<br/>
For root domain name, type "mydomain.com" (it can be whatever we want)<br/>

![](https://github.com/rbrianshutt/active_directory/blob/main/Active%20Directory%202.0/4.2%20add%20new%20forest.PNG)
<br />

Ensure DNS server is checked <br/>
Create password  <br/>

![](https://github.com/rbrianshutt/active_directory/blob/main/Active%20Directory%202.0/4.3%20dc%20options.PNG)
<br />

DNS Options  <br/>

![](https://github.com/rbrianshutt/active_directory/blob/main/Active%20Directory%202.0/4.4%20dns%20options.PNG)
<br />

Click Install  <br/>

![](https://github.com/rbrianshutt/active_directory/blob/main/Active%20Directory%202.0/4.5%20install.PNG)
<br />

The DC-1 VM is starting<br/>

![](https://github.com/rbrianshutt/active_directory/blob/main/Active%20Directory%202.0/5.1%20restarting.PNG)
<br />

Connect to DC-1 via remote connection as user: mydomain.com\labuser <br/>

![](https://github.com/rbrianshutt/active_directory/blob/main/Active%20Directory%202.0/5.2%20rdp%20into%20dc.PNG)
<br />

<h2>Create a Domain Admin user within the domain</h2>

Go to Active Directory Users and Computers (ADUC)  <br/>
Right click "mydomain.com" -> New -> Organizational Unit <br/>

![](https://github.com/rbrianshutt/active_directory/blob/main/Active%20Directory%202.0/6.1%20aduc%20create%20ou.png)
<br />

Create an Organizational Unit named _EMPLOYEES <br/>
Create an Organization Unit named _ADMINS  <br/>

![](https://github.com/rbrianshutt/active_directory/blob/main/Active%20Directory%202.0/6.2%20ou%20employees.PNG)
<br />

Right click our new _ADMINS folder -> New -> User<br/>

![](https://github.com/rbrianshutt/active_directory/blob/main/Active%20Directory%202.0/6.4%20new%20user%20janeadmin.png)
<br />

Create a new employee named “Jane Doe” (same password) with the username of “jane_admin”   <br/>

![](https://github.com/rbrianshutt/active_directory/blob/main/Active%20Directory%202.0/6.5%20janeadmin.PNG)
![](https://github.com/rbrianshutt/active_directory/blob/main/Active%20Directory%202.0/6.6%20create%20password.PNG)
![](https://github.com/rbrianshutt/active_directory/blob/main/Active%20Directory%202.0/6.7%20finish.PNG)
<br />

<h3>Add jane_admin to the “Domain Admins” Security Group</h3>

Notice Jane Doe as a user in the _ADMINS folder  <br/>
Right click on Jane Doe -> Properties <br/>

![](https://github.com/rbrianshutt/active_directory/blob/main/Active%20Directory%202.0/7.1%20add%20jane%20to%20jane%20admins%20security%20group.PNG)
<br />

Go to Member of tab, see she is a member of Domain Users <br/>
Click Add  <br/>

![](https://github.com/rbrianshutt/active_directory/blob/main/Active%20Directory%202.0/7.2%20member%20of%20add.PNG)
<br />

Type Domain Admins in the object names <br/>
Click OK <br/>

![](https://github.com/rbrianshutt/active_directory/blob/main/Active%20Directory%202.0/7.3%20add%20domain%20admins.PNG)
<br />

See that Jane Doe is a member of Domain Admins and Domain Users <br/>

![](https://github.com/rbrianshutt/active_directory/blob/main/Active%20Directory%202.0/7.4%20apply%20ok.PNG)
<br />

Log out of remote connection to DC-1  <br/>
Log back in as “mydomain.com\jane_admin” <br/>
User jane_admin as your admin account from now on <br/>

![](https://github.com/rbrianshutt/active_directory/blob/main/Active%20Directory%202.0/8.1%20log%20in%20as%20janeadmin.PNG)
<br />

<h2>Join CLIENT-1 to your domain (mydomain.com)</h2>

Login to CLIENT-1 as the original local admin (labuser) <br/>
We need to go to Settings to add the domain to CLIENT-1 <br/>
Click on System <br/>

![](https://github.com/rbrianshutt/active_directory/blob/main/Active%20Directory%202.0/9.1%20client%201%20settings%20system.PNG)
<br />

Click About  <br/>

![](https://github.com/rbrianshutt/active_directory/blob/main/Active%20Directory%202.0/9.2%20about.png)
<br />

Click Rename this PC (advanced) <br/>

![](https://github.com/rbrianshutt/active_directory/blob/main/Active%20Directory%202.0/9.3%20rename%20this%20pc.PNG)
<br />

Click Change  <br/>

![](https://github.com/rbrianshutt/active_directory/blob/main/Active%20Directory%202.0/9.4%20computer%20name%20change.PNG)
<br />

Ensure Domain is selected under Member of  <br/>
Enter "mydomain.com" <br/>
Click OK <br/>

![](https://github.com/rbrianshutt/active_directory/blob/main/Active%20Directory%202.0/9.5%20mydomain.PNG)
<br />

Enter admin credentials for mydomain.com  <br/>

![](https://github.com/rbrianshutt/active_directory/blob/main/Active%20Directory%202.0/9.6%20admin%20credentials.PNG)
<br />

Success  <br/>

![](https://github.com/rbrianshutt/active_directory/blob/main/Active%20Directory%202.0/9.7%20welcome%20to%20domain.PNG)
<br />

CLIENT-1 computer will restart  <br/>

![](https://github.com/rbrianshutt/active_directory/blob/main/Active%20Directory%202.0/9.8%20restart.PNG)
![](https://github.com/rbrianshutt/active_directory/blob/main/Active%20Directory%202.0/9.9%20restart%20now.PNG)
<br />

When CLIENT-1 restarts, go into Active Directory Users and Computers (ADUC) <br/>
Open Computers folder and notice CLIENT-1 shows up in ADUC <br/>

![](https://github.com/rbrianshutt/active_directory/blob/main/Active%20Directory%202.0/10.1%20client%201%20is%20in%20aduc.PNG)
<br />

Create a new OU named “_CLIENTS” and drag CLIENT-1 into there  <br/>

![](https://github.com/rbrianshutt/active_directory/blob/main/Active%20Directory%202.0/11.1%20create%20ou%20clients.png)
![](https://github.com/rbrianshutt/active_directory/blob/main/Active%20Directory%202.0/11.2%20create%20client%20ou.PNG)
<br />

Now CLIENT-1 is in _CLIENTS <br/>

![](https://github.com/rbrianshutt/active_directory/blob/main/Active%20Directory%202.0/11.3%20move%20client%201%20to%20clients%20ou.PNG)
<br />

jane_admins in _ADMINS  <br/>

![](https://github.com/rbrianshutt/active_directory/blob/main/Active%20Directory%202.0/11.4%20janeadmins%20in%20admins.PNG)
<br />

<h2>Setup Remote Desktop for non-administrative users on CLIENT-1</h2>

Log into Client-1 as mydomain.com\jane_admin  <br/>

![](https://github.com/rbrianshutt/active_directory/blob/main/Active%20Directory%202.0/12.1%20log%20in%20to%20client1%20as%20janeadmin.PNG)
<br />

Open system properties <br/>
Click Remote Desktop <br/>

![](https://github.com/rbrianshutt/active_directory/blob/main/Active%20Directory%202.0/12.2%20settings%20system%20remote%20desktop.PNG)
<br />

Click "Select Users that can remotely access this PC" under Users Accounts <br/>

![](https://github.com/rbrianshutt/active_directory/blob/main/Active%20Directory%202.0/12.3%20user%20accounts%20select%20users.PNG)
<br />

Click Add <br/>

![](https://github.com/rbrianshutt/active_directory/blob/main/Active%20Directory%202.0/12.4%20add.PNG)
<br />

Enter "Domain Users" in object names <br/>
Click OK<br/>

![](https://github.com/rbrianshutt/active_directory/blob/main/Active%20Directory%202.0/12.5%20domain%20users.PNG)
<br />

Notice Domain Users now have remote access  <br/>
You can now log into CLIENT-1 as a normal, non-administrative user now<br/>

![](https://github.com/rbrianshutt/active_directory/blob/main/Active%20Directory%202.0/12.6%20domain%20users%20allowed%20to%20use%20remote%20desktop.PNG)
<br />

<h2>Create a bunch of additional users and attempt to log into CLIENT-1 with one of the users</h2>

Login to DC-1 as jane_admin <br/>
Open PowerShell_ise as an administrator  <br/>

![](https://github.com/rbrianshutt/active_directory/blob/main/Active%20Directory%202.0/13.1%20open%20powershell%20ise%20as%20admin.PNG)
<br />

Paste the Powershell script (created by Josh Madakor) into the file <br/>
- [Powershell script that creates users](https://github.com/joshmadakor1/AD_PS/blob/master/Generate-Names-Create-Users.ps1)  

![](https://github.com/rbrianshutt/active_directory/blob/main/Active%20Directory%202.0/13.2%20paste%20script.PNG)
<br />

Press the play icon  <br/>
The script will generate 100 users <br/>

![](https://github.com/rbrianshutt/active_directory/blob/main/Active%20Directory%202.0/13.3%20generate%20users.PNG)
<br />

Open Active Directory Users and Computers (ADUC) <br/>
Select a random user under _EMPLOYEES <br/>

![](https://github.com/rbrianshutt/active_directory/blob/main/Active%20Directory%202.0/13.4%20pick%20random%20user.PNG)
<br />

Log in to CLIENT-1 via remote connection as the random user<br/>

![](https://github.com/rbrianshutt/active_directory/blob/main/Active%20Directory%202.0/13.5%20log%20in%20to%20client1%20as%20cikoredo.PNG)
<br />

Run whoami command in the command line <br/>
Notice that Users can now log in to the domain <br/>

![](https://github.com/rbrianshutt/active_directory/blob/main/Active%20Directory%202.0/13.6%20command%20line%20whoami.PNG)
<br />
