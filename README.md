<h1>PowerShell for Active Directory and Remote PowerShell Commands</h1>

<h2>Description</h2>
Project consists of utilizing PowerShell to perform Active Directory commands such as adding users, groups, and policies. Then, PowerShell is used to perform remote commands on the domain. This project is completed assuming there is a running version of Windows Server 2016 with a Windows 10 client added to its domain.
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
Download the "Create-Users.ps1" and "Userlist.csv" files to your Windows Server: <br/>
<img src="https://imagizer.imageshack.com/img922/544/Y1CrHw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Move the files to the C:\ drive: <br/>
<img src="https://imagizer.imageshack.com/img923/992/u8eOOt.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Edit "Create-Users.ps1" with PowerShell ISE by right-clicking it and choosing Edit: <br/>
<img src="https://imagizer.imageshack.com/img922/2822/QDd1KK.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Make sure the path of Userlist.csv is correct: <br/>
<img src="https://imagizer.imageshack.com/img922/8935/Lj13P9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Edit the CSV file with a word editor of your choice: <br/>
<img src="https://imagizer.imageshack.com/img922/38/pPOcou.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Run the script by clicking the green arrow or by pressing F5 on your keyboard: <br/>
<img src="https://imagizer.imageshack.com/img922/9903/ytuP0M.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Verify that the users were created by opening Active Directory Users and Computers: <br/>
<img src="https://imagizer.imageshack.com/img924/9901/ZGLJnG.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Create two new users, Test1 and Test2, in the IT OU via PowerShell with no additional parameters by using the following commands: <br/>
New-ADUser -Name Test1 -SamAccountName Test1 -path "OU=IT, DC=Cyber, DC=Local"<br />
<img src="https://imagizer.imageshack.com/img923/9869/GiW7m9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
New-ADUser -Name Test2 -SamAccountName Test2 -path "OU=IT, DC=Cyber, DC=Local" <br/>
<img src="https://imagizer.imageshack.com/img922/2916/CSYn6r.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Show all users of the IT OU by using "Get-ADUser -Filter * -SearchBase "OU=IT, DC=Cyber, DC=local" -SearchScope subtree: <br/>
<img src="https://imagizer.imageshack.com/img924/3217/HTau6W.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Show all users from the domain for which the Department parameter equals IT. You will not see two users: <br/>
Get-ADUser -Filter "department -eq 'IT'"<br />
<img src="https://imagizer.imageshack.com/img924/8417/kIrHpw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Or Get-ADUser -Filter {department -like "IT"}: <br/>
<img src="https://imagizer.imageshack.com/img922/808/5SUMup.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
To get all users from the IT OU run: <br/>
Get-ADUser -Filter {department -notlike "*"} -SearchBase "OU=IT, DC=Cyber, DC=Local" | Set -ADUser -Department "IT"
<img src="https://imagizer.imageshack.com/img923/4995/TDQVq6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Repeat step 3. You should now see the new users: <br/>


<h2>Remote PowerShell Commands:</h2>
Log into the Windows 10 client and open PowerShell as an administrator. Enable remote PowerShell commands by using "Enable-PSRemoting -force": <br/>
<img src="https://imagizer.imageshack.com/img924/7797/C1nSZ3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Use "ping 10.0.0.1" to verify connectivity to the server: <br/>
<img src="https://imagizer.imageshack.com/img924/4706/ajLQjn.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
You must start the Windows Remote Management service for the next step to work. In the Windows search bar, enter "services.msc", the find Windows Remote Management and click the green start button: <br/>
<img src="https://imagizer.imageshack.com/img923/1638/XRa4EL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
On the server, open PowerShell as an admin. Use the following command to show the remote computer's name: <br/>
Invoke-Command -ComputerName Client10 -Credential Cyber\administrator -ScriptBlock {hostname} Client10<br/>
<img src="https://imagizer.imageshack.com/img923/8244/jr7klB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Use Invoke-Command as follows to create a local user on the remote client: <br/>
Invoke-Command -ComputerName Client10 -Credential Cyber\administrator -ScriptBlock {net user invoke_user 'P@ssw0rd'/add}<br/>
<img src="https://imagizer.imageshack.com/img922/4836/INWC0N.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Verify the new user was created on the remote client machine by using the following: <br/>
Invoke-Command -ComputerName Client10 -Credential Cyber\administrator -ScriptBlock {net user}<br/>
<img src="https://imagizer.imageshack.com/img924/6618/cGOj09.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Start a session between the server and client machines by using the "Enter-PSSession" command. Enter the correct computer name (Client10): <br/>
<img src="https://imagizer.imageshack.com/img923/213/ATPkFH.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Verify that the server is remotely logged in to the client machine using the "hostname" command: <br/>
<img src="https://imagizer.imageshack.com/img924/7040/JjuORU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Remotely check the client machine's IP by using the "ipconfig" command: <br/>
<img src="https://imagizer.imageshack.com/img923/4452/nZ3ltl.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Use "Get-Process" to show the client process (you can also start and stop a process): <br/>
<img src="https://imagizer.imageshack.com/img924/1571/2xCHvS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Create a directory on the desktop by using: <br/>
<img src="https://imagizer.imageshack.com/img924/9991/WJ74gB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Verify the directory was created through PowerShell by using the "dir" command: <br/>
cd C:\Users\administrator\Desktop and "mkdir Test_File"<br/>
<img src="https://imagizer.imageshack.com/img924/1636/atisrD.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Restart the client computer remotely by using "Restart-Computer -force": <br/>
<img src="https://imagizer.imageshack.com/img922/2002/nuFUxM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
