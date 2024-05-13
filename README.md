![image](https://github.com/Wallytj/ActiveDirectoryLab/assets/75745703/5ac30f76-0d55-4416-aab6-080ef77ce297)# ActiveDirectoryLab
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
<br><img width="1131" alt="Screenshot 2024-05-14 at 1 29 47 AM" src="https://github.com/Wallytj/securityaudit/assets/75745703/87bbd564-7fee-41fb-913d-005a96a3f2c6">
</br>
<br><img width="547" alt="Screenshot 2024-05-14 at 1 30 27 AM" src="https://github.com/Wallytj/securityaudit/assets/75745703/4f7c2cfb-c469-4cc9-9c6c-d834930abac5">
</br>
<br><img width="500" alt="Screenshot 2024-05-14 at 1 31 15 AM" src="https://github.com/Wallytj/securityaudit/assets/75745703/9c8382b8-304d-4b21-9ea6-2d4e0468eb54">
</br>
<br><img width="685" alt="Screenshot 2024-05-14 at 1 32 08 AM" src="https://github.com/Wallytj/securityaudit/assets/75745703/4c8802e3-e3e1-4e19-bd90-e2888237136a">
</br>
<br>
Next, you'll need to set up your DHCP (Dynamic Host Configuration Protocol) to ensure that clients connecting to your domain receive automatic IP addresses, allowing them internet access even within the private internal network. To configure DHCP, return to your server manager and select "add roles and features."
</br>
<br><img width="1081" alt="Screenshot 2024-05-14 at 1 33 51 AM" src="https://github.com/Wallytj/securityaudit/assets/75745703/71367e49-2256-4f28-aeee-068b8772464a">
</br>
<br><img width="1064" alt="Screenshot 2024-05-14 at 1 35 15 AM" src="https://github.com/Wallytj/securityaudit/assets/75745703/6aa3bfe5-a859-4d28-bfbf-6a8cc6c6d275">
</br>
<br><img width="1062" alt="Screenshot 2024-05-14 at 1 35 53 AM" src="https://github.com/Wallytj/securityaudit/assets/75745703/bb68fae3-bc65-429c-8e3b-7020250099e5">
</br>
<br><img width="1058" alt="Screenshot 2024-05-14 at 1 37 53 AM" src="https://github.com/Wallytj/securityaudit/assets/75745703/6c566dd6-7b24-47d8-aa40-9fcf554267ca">
</br>
<br>After successfully installing DHCP, the next step is to configure it according to the architectural design, which serves as a blueprint. Assuming you have basic networking skills, follow these steps: access Tools, locate DHCP, select DC.mydomain.com, navigate to IPV4, and then initiate the creation of a new scope.![image](https://github.com/Wallytj/ActiveDirectoryLab/assets/75745703/469d9f6e-b86a-410b-9cd7-287761d37656)
</br>
<br><img width="520" alt="Screenshot 2024-05-14 at 1 40 34 AM" src="https://github.com/Wallytj/securityaudit/assets/75745703/b183f54c-cbfb-4cc1-b1c2-fd324b8add5e">
</br>
<br><img width="509" alt="Screenshot 2024-05-14 at 1 40 54 AM" src="https://github.com/Wallytj/securityaudit/assets/75745703/32ee3a5b-14b9-4cbf-91d8-e09ee82a5469">
</br>
<br><img width="509" alt="Screenshot 2024-05-14 at 1 41 02 AM" src="https://github.com/Wallytj/securityaudit/assets/75745703/2896ac51-fbb4-4188-8443-b8e58400042a">
</br>
<br><img width="513" alt="Screenshot 2024-05-14 at 1 41 08 AM" src="https://github.com/Wallytj/securityaudit/assets/75745703/c42780a0-3fd8-4ae7-8184-974008884199">
</br>
<br><img width="515" alt="Screenshot 2024-05-14 at 1 41 15 AM" src="https://github.com/Wallytj/securityaudit/assets/75745703/619d1312-b631-4155-972b-7a8c524c1e28">
</br>
<br>Following that, I'll access the PowerShell script located on my desktop, designed to automate the creation of 1,000 users. This script will generate user accounts and set their passwords to "Password1"</br>
<br><img width="1111" alt="Screenshot 2024-05-14 at 1 44 37 AM" src="https://github.com/Wallytj/securityaudit/assets/75745703/c02a3f68-1d80-4a15-b900-f0a3281ec28c">
</br>
<h3>Runing Windows Powershell ISE as administrator</h3>
<br><img width="1300" alt="Screenshot 2024-05-14 at 1 45 56 AM" src="https://github.com/Wallytj/securityaudit/assets/75745703/7e514127-c2d1-48d6-ae48-f928939527e6">
</br>
<h3>Open your script</h3>

<br><img width="1438" alt="Screenshot 2024-05-14 at 1 46 56 AM" src="https://github.com/Wallytj/securityaudit/assets/75745703/11295445-6f84-40bd-bba2-3d0547e17086">
</br>
<br><img width="1439" alt="Screenshot 2024-05-14 at 1 47 59 AM" src="https://github.com/Wallytj/securityaudit/assets/75745703/587c4b0f-ff37-4a84-8b03-3fb767e35bfe">
</br>
<br>Set execution policy to unrestricted to bypass the security feature since this is just a lab for practice</br>
<br><img width="1432" alt="Screenshot 2024-05-14 at 1 49 00 AM" src="https://github.com/Wallytj/securityaudit/assets/75745703/e3a40ff8-4246-42f1-bea6-df5485fda532">
</br>
<br>To run the script, you must locate the directory where it is saved.</br>
<br><img width="1242" alt="Screenshot 2024-05-14 at 1 51 00 AM" src="https://github.com/Wallytj/securityaudit/assets/75745703/30e42145-ff25-4eac-b2f2-97f084cd4ab8">
</br>
<h3>Runing the Script</h3>
<br><img width="1440" alt="Screenshot 2024-05-14 at 1 51 49 AM" src="https://github.com/Wallytj/securityaudit/assets/75745703/2600ac25-ca8f-44c2-81c2-2223043fbe32">
</br>
<br><img width="1437" alt="Screenshot 2024-05-14 at 1 53 40 AM" src="https://github.com/Wallytj/securityaudit/assets/75745703/65e1a4d6-db1e-4a5f-a7da-d4c55517a4c9">
</br>
<br><img width="1261" alt="Screenshot 2024-05-14 at 1 53 49 AM" src="https://github.com/Wallytj/securityaudit/assets/75745703/97c73706-b362-4213-80a5-be75cb97a5e9">
</br>
<br><img width="1267" alt="Screenshot 2024-05-14 at 1 53 58 AM" src="https://github.com/Wallytj/securityaudit/assets/75745703/882f83f5-1774-4933-b9e1-c5987fdd1a4c">
</br>
<br><img width="1263" alt="Screenshot 2024-05-14 at 1 54 08 AM" src="https://github.com/Wallytj/securityaudit/assets/75745703/6c329373-7287-479d-865d-8563e2b20493">
</br>
<br>With everything set up, the final step is to create your Windows 11 virtual machine, serving as your client for testing and verification purposes. My Windows 11 client is now operational, and I am prepared to commence network testing.
</br>
<br><img width="1080" alt="Screenshot 2024-05-14 at 1 58 23 AM" src="https://github.com/Wallytj/securityaudit/assets/75745703/0d5f46b0-e444-4e6b-8bf2-7ded6826919d">
</br>
<br>Upon confirming that the default gateway is configured to 172.16.0.1, you can conclude that all necessary steps have been completed. At this point, proceed to add your virtual machine to the domain controller (DC). To do so, access your virtual machine's settings, navigate to "About," then "Domain or Workgroup." From there, add the client1 to your domain, which should be mydomain.com. Upon successful completion of this step, you will have successfully established your home lab with Active Directory, enabling login to the client machine using any previously created accounts.
The setup and configuration of our network infrastructure have been successfully finalized. By installing and configuring essential software such as DHCP and following an architectural blueprint, we've ensured seamless network connectivity and IP address assignment for clients. Automating user creation through a PowerShell script has streamlined administrative tasks. Verifying network functionality with the Windows 11 virtual machine running as our client and integrating the client machine with our Active Directory setup through domain addition have all contributed to a successful deployment of network and domain services. This home lab implementation exemplifies efficient management and user authentication.
</br>
