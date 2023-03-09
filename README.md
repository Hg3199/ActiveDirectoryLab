<h1>Active Directory Home Lab</h1>

 ### []()

<h2>Description</h2>
<b>In this lab we're going to walk through how to create an Active Directory home lab Environment using Oricale Virtual Box. Configuring and setting this up to simulate a corperate private network that has access to the internet through the domain controller which is also going to house active directory. Then we're going to run a powershell script to create 1000 users in our system that will be able to sign in to any of the workstations in our simulated domain.</b>
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
<b>The initial step of this project involves downloading two ISO files- one for Windows Server 2019 and the other for Windows 10. Following the download of both files, we must open the VirtualBox in order to spin up two virtual machines. The Domain controller is going to have 2 adapdters. One that will be set up to run NAT to connect to my home's wifi network and another for the internal network for the other clients to connect to. Once the construction of the two virtual machines is complete, we can continue the remainder of the project. It is important to note that a well-planned approach is necessary to ensure that the virtual machines are created accurately.</b>
<br />
<br />
<br />

<b>Configuring the domain controller's ram and cores:</b>
<br />
<br />
<br />

![ad1 jpg](https://user-images.githubusercontent.com/125488657/223576579-3df4d811-4160-4960-9627-0757049eaa56.png)
<br />
<br />

<b>Setting up the controller's second network adapter:</b>
<br />
<br />
<br />

![ad3 jpg](https://user-images.githubusercontent.com/125488657/223578216-d20b933f-1ce1-48d7-a472-882c73293efd.png)

<b>Once the machine is created, we will launch it and download windows server 2019. After doing so we will then create an admin account for the domain controller and set up the ip addressing for the internal NIC as the one that will be running NAT will get an ip address from my home router.</b>
<br />
<br />

<b>Downloading Windows Server 2019 on the domain controller:</b>
<br />
<br />
<br />

![ad2 jpg](https://user-images.githubusercontent.com/125488657/223579913-8f3b206e-cd19-4c67-afe2-ed5e76e8fb6b.png)
<br />
<br />

<b>Setting up the NIC for the internal network:</b>
<br />
<br />
<br />

![ad4 jpg](https://user-images.githubusercontent.com/125488657/223581777-2345a01d-3ebf-4b41-af0c-b5516cfdaaca.png)

<br />
<br />
<b>Once we had identified the adapter used for the internal network, we allocated it an appropriate IP address and set the default gateway to the address of the domain controllers, which had been connected to the internet via the adapter running NAT.This enabled us to establish a secure link between the internal network and the internet so that our users could readily access the resources they required.</b> 
<br />
<br />

<b>Setting up IP addressing:</b>
<br />
<br />
<br />

![ad5 jpg](https://user-images.githubusercontent.com/125488657/223807245-bd6cd333-e58f-4526-b48e-12c9d000e278.png)
<br />
<br />
<br />
<b>Having successfully completed the IP addressing for the internal network adapter and default gateway, the next step in our process is to install Active Directory and create a domain. Once the installation has been completed, we will then proceed with our post deployment configuration, which will ultimately proceed with the creation of a new domain called "mydomain.com". This is a crucial step in establishing our infrastructure.</b>
<br />
<br />
<br />

<b>Creating new domain:<b/>
<br />
<br />
<br />

![ad7](https://user-images.githubusercontent.com/125488657/223815336-150d2d66-144e-4ab9-8a5c-6d47d3fbebad.jpg)
<br />
<br />
<br />
Once mydomain.com was created, an organizational unit was set up with a new user (domain admin) to manage the domain, secure users, maintain systems/software, and serve as a contact point/info source for users. This role is important to the domain's success.
<br />
<br />
<br />

<b>Creating new OU and user:<b/>
<br />
<br />
<br />

![ad8](https://user-images.githubusercontent.com/125488657/223817096-205dccc1-f986-4b4c-9dfd-9ef1aaa5e97a.jpg)
<br />
<br />
<br />
Having established a new domain admin user, we will log out and sign in as that user. Our next step is to install the RAS/NAT (Remote Access Server/Network Address Translation) software. This will ensure that each client which is added to the private network is granted access to the internet through the domain controller. This is a crucial step in our network security system, as it allows us to manage who is allowed to access our network and the resources available to them. Therefore, it is absolutely necessary that we take the time to properly implement this system.
<br />
<br />
<br />

<b>Installing RAS/NAT:<b/>
<br />
<br />
<br />

![ad9](https://user-images.githubusercontent.com/125488657/224130857-c4384022-e92b-4332-8377-444d0ea73f14.jpg)
<br />
<br />
<br />
The next step in our network setup is to install and configure DHCP on the domain controller. This will allow client computers on the private network to obtain IP addresses. After installation, we will then configure a new scope for the DHCP server, which will assign a set of IP addresses, as well as leases on those addresses, to each client added to the network. This will ensure us to manage the network more efficiently.
<br />
<br />
<br />

<b>Configuring DHCP scope:<b/>
<br />
<br />
<br />
![ad11](https://user-images.githubusercontent.com/125488657/224138238-9bfd93c2-7612-4831-a4ad-c9914048d69a.jpg)
<br />
<br />
<br />
Once our scope has been established, we need to further configure some DHCP options to inform clients which server to use for DNS, and which one for the default gateway. As our network is setup, internal clients will be connected through the domain controller's internal Network Interface Card (NIC). Consequently, we will use the NIC's IP address as the DNS server, allowing each client to join the domain.
<br />
<br />
<br />

<b>Configuring DHCP options:<b/>
<br />
<br />
<br />
![ad14](https://user-images.githubusercontent.com/125488657/224145266-5e14435c-fe81-4f53-908a-23082aa676cb.jpg)

31:15

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
