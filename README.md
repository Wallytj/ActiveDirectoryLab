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

<h3> Network Adaptor 1 </h3>
<br/>
<br><img width="707" alt="Screenshot 2024-05-14 at 12 31 22 AM" src="https://github.com/Wallytj/securityaudit/assets/75745703/557b3eda-2817-4a5f-b273-d46a0b147c25">
<br/>
<h3>Network Adaptor 2 </h3>
<br><img width="704" alt="Screenshot 2024-05-14 at 12 35 35 AM" src="https://github.com/Wallytj/securityaudit/assets/75745703/f1f76406-5929-4bb2-89b1-690d183e68cd">
</br>
<br>Start your server and proceed to set an IP address for the internal network on Network Adapter 2. While Network Adapter 1 automatically acquires its IP address from your home router and does not require manual configuration, the internal network necessitates manual setup to assign the IP address.
</br>
<h3> Changing Adaptor Name </h3>
<br><img width="1438" alt="Screenshot 2024-05-14 at 12 41 33 AM" src="https://github.com/Wallytj/securityaudit/assets/75745703/67c13f7a-7836-4cb0-9852-2e52687268dc">
</br>
No default gateway assignment is necessary as the Domain Controller will act as its own default gateway. Additionally, once Active Directory is installed, it automatically configures the DNS server. 

As per the architectural design, you will assign the following:
<h3>Assigning IP address to Internal Network</h3>
<br><img width="1439" alt="Screenshot 2024-05-14 at 12 46 16 AM" src="https://github.com/Wallytj/securityaudit/assets/75745703/d8429a35-cbc9-4f64-907f-bd82240dd982">
</br>
With your network interface cards (NICs) properly configured, the next step is to install Active Directory Domain Services (AD DS) and establish a domain, which will be named as “mydomain.com”.
<h3>Instaling Active Directory Domin services</h3>
<br><img width="1434" alt="Screenshot 2024-05-14 at 12 56 18 AM" src="https://github.com/Wallytj/securityaudit/assets/75745703/74a10009-ba3e-4e11-87b6-351f4c31ef18">
</br>
<br><img width="791" alt="Screenshot 2024-05-14 at 12 56 51 AM" src="https://github.com/Wallytj/securityaudit/assets/75745703/812e78e4-3b63-4e45-a103-5e992be40de9">
</br>
<br><img width="1404" alt="Screenshot 2024-05-14 at 12 57 08 AM" src="https://github.com/Wallytj/securityaudit/assets/75745703/ad640918-fd18-4763-b688-b71add4a7a96">
</br>
<br>Once the installation process is complete, you might receive a notification for Post-deployment configuration, prompting domain creation. You're free to select any domain name you wish, but for consistency, "mydomain.com" will be used as an example in this guide. You're encouraged to use the same domain name if you wish to follow along.
</br>

<br><img width="1311" alt="Screenshot 2024-05-14 at 1 07 32 AM" src="https://github.com/Wallytj/securityaudit/assets/75745703/f2cb37aa-a7ba-42a6-9a58-8eee30eb70c6">
</br>
<br><img width="1128" alt="Screenshot 2024-05-14 at 1 07 53 AM" src="https://github.com/Wallytj/securityaudit/assets/75745703/78b2b4dd-c429-4316-92ec-1cb162dd1f02">
</br>
<br><img width="1081" alt="Screenshot 2024-05-14 at 1 08 09 AM" src="https://github.com/Wallytj/securityaudit/assets/75745703/7b964556-d9aa-45a0-9826-f78f144fba03">
</br>
<br><img width="1110" alt="Screenshot 2024-05-14 at 1 08 20 AM" src="https://github.com/Wallytj/securityaudit/assets/75745703/1c778e99-3d20-4e75-86b9-6d0348dbc64a">
</br>
<br><img width="485" alt="Screenshot 2024-05-14 at 1 08 42 AM" src="https://github.com/Wallytj/securityaudit/assets/75745703/6555a173-7d01-487e-9c41-b4f3f6f3f2a8">
</br>
<br>Next, continue by installing your Remote Access Server or Network Address Translation (NAT). This step aims to allow newly added computers to access the internet while staying connected to the private network via the domain controller. To achieve this, configuring NAT settings is essential.
</br>
<br><img width="1163" alt="Screenshot 2024-05-14 at 1 25 45 AM" src="https://github.com/Wallytj/securityaudit/assets/75745703/dc631d87-4854-4ed2-8268-bec2ea453ec8">
</br>
<br><img width="1158" alt="Screenshot 2024-05-14 at 1 26 47 AM" src="https://github.com/Wallytj/securityaudit/assets/75745703/db59775a-aa73-43af-a238-6934e5897c3f">
</br>
<br>Once the installation process is complete, proceed to configure the "Routing and Remote Access" feature. You can locate "Routing and Remote Access" within the tools menu.
</br>
<br></br>
<br></br>
<br></br>
<br></br>
<br></br>
<br></br>
<br></br>
<br></br>
<br></br>
<br></br>
<br></br>
<br></br>
<br></br>
<br></br>
<br></br>
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




