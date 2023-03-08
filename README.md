<h1>Active Directory Home Lab</h1>

 ### [YouTube Demonstration]()

<h2>Description</h2>
In this lab we're going to walk through how to create an Active Directory home lab Environment using Oricale Virtual Box. Configuring and setting this up to simulate a corperate private network that has access to the internet through the domain controller which is also going to house active directory. Then we're going to run a powershell script to create 1000 users in our system that will be able to sign in to any of the workstations in our simulated domain.
<br />


<h2>Languages and Utilities Used</h2>

- <b>PowerShell</b> 
- <b>VirtualBox</b>
- <b>Active Directory</b>

<h2>Environments Used </h2>

- <b>Windows server 2019</b> 
- <b>Windows 10</b>

<h2>Project Walkthrough</h2>
<br />
<br />
The initial step of this project involves downloading two ISO files- one for Windows Server 2019 and the other for Windows 10. Following the download of both files, we must open the VirtualBox in order to spin up two virtual machines. The Domain controller is going to have 2 adapdters. One that will be set up to run NAT to connect to my home's wifi network and another for the internal network for the other clients to connect to. Once the construction of the two virtual machines is complete, we can continue the remainder of the project. It is important to note that a well-planned approach is necessary to ensure that the virtual machines are created accurately.
<br />
<br />
<br />

<b>Configuring the domain controller's ram and cores:</b>
![ad1 jpg](https://user-images.githubusercontent.com/125488657/223576579-3df4d811-4160-4960-9627-0757049eaa56.png)
<br />
<br />

<b>Setting up the controller's second network adapter:</b>
![ad3 jpg](https://user-images.githubusercontent.com/125488657/223578216-d20b933f-1ce1-48d7-a472-882c73293efd.png)

Once the machine is created, we will launch it and download windows server 2019. After doing so we will then create an admin account for the domain controller and set up the ip addressing for the internal NIC as the one that will be running NAT will get an ip address from my home router.
<br />
<br />

<b>Downloading Windows Server 2019 on the domain controller:</b>
![ad2 jpg](https://user-images.githubusercontent.com/125488657/223579913-8f3b206e-cd19-4c67-afe2-ed5e76e8fb6b.png)
<br />
<br />

<b>Setting up the NIC for the internal network:</b>
![ad4 jpg](https://user-images.githubusercontent.com/125488657/223581777-2345a01d-3ebf-4b41-af0c-b5516cfdaaca.png)

<br />
<br />
Once we had identified the adapter used for the internal network, we assigned it an appropriate IP address and set the default gateway to the address of the domain controllers, which had been connected to the internet via the adapter running NAT. This enabled us to establish a secure connection between the internal network and the internet so that our users could easily access the resources they needed. 



<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
