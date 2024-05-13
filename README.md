# ActiveDirectoryLab
<h1>Active Directory HomeLab</h1>
<img width="647" alt="Screenshot 2024-05-14 at 12 10 38 AM" src="https://github.com/Wallytj/securityaudit/assets/75745703/2746f1c9-b300-4348-a40c-2949bab91bb5">

<h2>Description</h2>
This will walk you through the steps of creating an Active Directory Home Lab using Oracle VirtualBox. Furthermore, it will showcase the process of quickly adding more than 1,000 users using PowerShell Scripts for automation.
To begin, you'll need to download Oracle VirtualBox, Windows Server 2019 ISO, and Windows 11 Disk Image ISO. These three software programs are essential tools for setting up your lab. After downloading, you'll install each program to get started.
<br />

<h2>SetUp VirtualBox</h2>
<img width="1428" alt="Screenshot 2024-05-14 at 12 21 48 AM" src="https://github.com/Wallytj/securityaudit/assets/75745703/c58b6bee-1f1f-447e-8cfd-82865b6c5b50">

<H2> Install Windows 2019 Server </H2>
<br/>
<img width="707" alt="Screenshot 2024-05-14 at 12 31 22 AM" src="https://github.com/Wallytj/securityaudit/assets/75745703/557b3eda-2817-4a5f-b273-d46a0b147c25">
<br/>
Next, allocate two network adapters to the Virtual Machine. The first Network Adapter will establish a connection with the external network (i.e., the internet), while the second Network Adapter will be reserved for the private network, facilitating secure connections for client devices.

<br/>
<br/>
<h2>Describe the permissions string</h2>
The 10-character string can be deconstructed to determine who is authorized to access the file and their specific permissions. The characters and what they represent are as follows:
<li>
	1st character: This character is either a d or hyphen (-) and indicates the file type. If it’s a d, it’s a directory. If it’s a hyphen (-), it’s a regular file.</li>
<li>	2nd-4th characters: These characters indicate the read (r), write (w), and execute (x) permissions for the user. When one of these characters is a hyphen (-) instead, it indicates that this permission is not granted to the user.</li>
<li>5th-7th characters: These characters indicate the read (r), write (w), and execute (x) permissions for the group. When one of these characters is a hyphen (-) instead, it indicates that this permission is not granted for the group.</li>
<li>8th-10th characters: These characters indicate the read (r), write (w), and execute (x) permissions for other. This owner type consists of all other users on the system apart from the user and the group. When one of these characters is a hyphen (-) instead, that indicates that this permission is not granted for other.</li>
</br>
For example, the file permissions for project_t.txt are -rw-rw-r--. Since the first character is a hyphen (-), this indicates that project_t.txt is a file, not a directory. The second, fifth, and eighth characters are all r, which indicates that user, group, and other all have read permissions. The third and sixth characters are w, which indicates that only the user and group have write permissions. No one has execute permissions for project_t.txt.
<br/>
<br/>
<h2>Change file permissions</h2>
The organization determined that other shouldn't have write access to any of their files. To comply with this, I referred to the file permissions that I previously returned. I determined project_k.txt must have the write access removed for other.
<br/>
The following code demonstrates how I used Linux commands to do this:
<br/>
<img width="468" alt="image" src="https://github.com/Wallytj/TjCyberSecShowcase/assets/75745703/602b57d7-bced-42bb-85e8-d381203485f4">
</br>
The first two lines of the screenshot display the commands I entered, and the other lines display the output of the second command. The chmod command changes the permissions on files and directories. The first argument indicates what permissions should be changed, and the second argument specifies the file or directory. In this example, I removed write permissions from other for the project_k.txt file. After this, I used ls -la to review the updates I made.
<br/>
<br/>
<h2> Change file permission on the hidden file</h2>
The research team at my organization recently archived project_x.txt. They do not want anyone to have write access to this project, but the user and group should have read access.
<br/>
The following code demonstrates how I used Linux commands to change the permissions:
<br/>
<img width="468" alt="image" src="https://github.com/Wallytj/TjCyberSecShowcase/assets/75745703/97fe9c40-b485-43d3-82f8-8d355f100790">
<br/>
The first two lines of the screenshot display the commands I entered, and the other lines display the output of the second command. I know .project_x.txt is a hidden file because it starts with a period (.). In this example, I removed write permissions from the user and group, and added read permissions to the group. I removed write permissions from the user with u-w. Then, I removed write permissions from the group with g-w, and added read permissions to the group with g+r.
<br/>
<br/>
<h2>Change directory permissions</h2>
My organization only wants the researcher2 user to have access to the drafts directory and its contents. This means that no one other than researcher2 should have execute permissions.
<br/>
The following code demonstrates how I used Linux commands to change the permissions:
<br/>
<img width="468" alt="image" src="https://github.com/Wallytj/TjCyberSecShowcase/assets/75745703/d2c6d67c-b187-4032-82bb-dd3faccf0681">
<br/>
The first two lines of the screenshot display the commands I entered, and the other lines display the output of the second command. I previously determined that the group had execute permissions, so I used the chmod command to remove them. The researcher2 user already had execute permissions, so they did not need to be added.
<br/>
<br/>
<h2> Summary</h2>
I changed multiple permissions to match the level of authorization my organization wanted for files and directories in the projects directory. The first step in this was using ls -la to check the permissions for the directory. This informed my decisions in the following steps. I then used the chmod command multiple times to change the permissions on files and directories.




