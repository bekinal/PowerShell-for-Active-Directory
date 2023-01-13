<h1>PowerShell for Active Directory and Remote PowerShell Commands</h1>

<h2>Description</h2>
Project consists of utilizing PowerShell to perform Active Directory commands such as adding users, groups, and policies. Then, PowerShell is used to perform remote commands on the domain.
<br />


<h2>Utilities Used</h2>

- <b>VirtualBox</b> 
- <b>Windows Server 2016</b>
- <b>Windows PoweShell</b>

<h2>Environments Used </h2>

- <b>Windows Server 2016</b>

<h2>PowerShell with Active Directory:</h2>

Create an OU named IT using the "New-ADOrganizationalUnit IT" Command: <br/>
<img src="https://imagizer.imageshack.com/img924/4271/f7S3PY.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Create a user account named Josep in the IT OU by using the "New-ADUser -Name "Josep" -SamAccountName "Josep" -path "OU=IT, DC=Cyber, DC=local" command: <br/>
<img src="https://imagizer.imageshack.com/img922/7493/a2gFAK.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Use "Set-ADAccountPassword Josep" to set a password for the new user. When asked for the current password, leave it empty and select Enter: <br/>
<img src="https://imagizer.imageshack.com/img922/4048/sRFqMe.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Enable the Josep account by using "Enable-ADAccount Josep": <br/>
<img src="https://imagizer.imageshack.com/img923/4434/NGgl0u.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Create a global security group for users in the IT department. Name it "IT-GRP", and create it in the IT OU. Use the command "New-ADAgroup "IT-GRP" -path "OU=IT, DC=Cyber, DC=local" -GroupScope Global -GroupCategory Security": <br/>
<img src="https://imagizer.imageshack.com/img924/4715/zwmaNZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Add Josep to the IT group by using "Add-ADGroupMember "IT-GRP" -Members Josep: <br/>
<img src="https://imagizer.imageshack.com/img922/7417/xMYRGC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Add a Department It parameter to the user by running "Set-ADUser Josep -Department "IT"": <br/>
<img src="https://imagizer.imageshack.com/img924/6033/FXPF13.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Use the following command to see the user properties and verify that all changes were made "Get-ADUser Josep -Properties department": <br/>
<img src="https://imagizer.imageshack.com/img924/5566/blftfP.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Use the following command to verify group members "Get-ADGroupMember IT-GRP": <br/>
<img src="https://imagizer.imageshack.com/img922/7638/82mfxf.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Log in to the Josep user account via the Windows 10 client machine: <br/>
<img src="https://imagizer.imageshack.com/img924/5848/vBoOEr.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Download the "Create-Users.ps1" and "Userlist.csv" files to your Windows Server. Move them to our C: Drive: <br/>
<img src="https://imagizer.imageshack.com/img922/544/Y1CrHw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Edit "Create-Users.ps1" with PowerShell ISE by right-clocking it and choosing Edit: <br/>
<img src="https://imagizer.imageshack.com/img923/992/u8eOOt.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Make sure the path of Userlist.csv ios correct: <br/>
<img src="https://imagizer.imageshack.com/img922/2822/QDd1KK.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Edit the CDV file with a word editor of your choice: <br/>
<img src="https://imagizer.imageshack.com/img922/8935/Lj13P9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
: <br/>
<img src="https://imagizer.imageshack.com/img922/38/pPOcou.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
: <br/>
<img src="https://imagizer.imageshack.com/img922/9903/ytuP0M.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
: <br/>
<img src="https://imagizer.imageshack.com/img924/9901/ZGLJnG.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
: <br/>
<img src="https://imagizer.imageshack.com/img923/9869/GiW7m9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
: <br/>
<img src="https://imagizer.imageshack.com/img922/2916/CSYn6r.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
: <br/>
<img src="https://imagizer.imageshack.com/img924/3217/HTau6W.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
: <br/>
<img src="https://imagizer.imageshack.com/img924/8417/kIrHpw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
: <br/>
<img src="https://imagizer.imageshack.com/img922/808/5SUMup.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
: <br/>
<img src="https://imagizer.imageshack.com/img923/4995/TDQVq6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
: <br/>


<h2>Remote PowerShell Commands:</h2>
Type "sconfig" to enter the configuration options: <br/>
<img src="https://i.imgur.com/y4j5940.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
Select option 1 to enter into a Domain with the letter D. Enter the Domain name "cyber.local", then the authorized domain user, cyber\administrator:  <br/>
<img src="https://i.imgur.com/vAZ0ewM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
Type in the password for the administrator. When typing the password, notice that nothing will populate the screen. Hit enter, and select No when prompted to name change. Restart the machine:  <br/>
<img src="https://i.imgur.com/80KLDOr.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
