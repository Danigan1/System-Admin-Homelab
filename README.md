# My Windows Home Lab: A Training Ground for System Administration
Within this GitHub project lies my personal journey into the world of system administration and Active Directory. Crafted with a novice's ambition and an unwavering commitment to learning, my Windows home lab serves as a training ground for practical experience in system admin responsibilities and as a gateway to mastering Active Directory.

## The Aspiring Administrator
Bridging the gap between theory and practice in system administration can be challenging, especially for a beginner. However, my project underscores a proactive approach to gaining hands-on experience and a deep understanding of system administration.

## Here's what you'll discover within this project:

**Lab Setup Expertise**: I've honed my skills in setting up a Windows-based home lab, carefully selecting hardware and software for a well-rounded learning environment.

**Real-World Application**: In this lab, I've immersed myself in system admin tasks, configuring virtual machines, managing networks, and comprehensively exploring Active Directory.

**Active Directory Proficiency**: Active Directory, often seen as a complex subject, has become a core competence in this lab. My understanding and hands-on experience with it are integral to this project.

**Transparency in Learning**: My documentation not only showcases achievements but also candidly portrays the learning curve, including challenges encountered and lessons learned.



## The Lab Topology
Within this lab, I've carefully structured a real-world-like environment to explore system administration principles. The heart of this setup is a Windows Server 2019 machine, which serves as the domain controller. This powerful server represents the core of any Windows-based network and offers me an excellent platform for diving deep into Active Directory.

Complementing the server is a Windows 10 machine, seamlessly joined to the domain. This configuration provides a holistic understanding of system admin responsibilities, network management, and user account management. It's a practical microcosm of enterprise environments, with the Windows Server 2019 acting as the backbone and the Windows 10 machine as the endpoint.

<img width="1331" alt="Screen Shot 2023-10-20 at 11 51 26 AM" src="https://github.com/Danigan1/Azure-Cloud-Detection-Lab/assets/107498392/3d07f5ad-c417-4875-9af1-a2681c801098">


## The Windows Perspective
You may wonder why I chose to focus on Windows. Windows systems play a prominent role in many organizations. For system administrators, proficiency in Windows-based environments is a valuable skill set. By concentrating my efforts on Windows, I'm positioning myself to excel in a wide range of IT roles and environments.

This project signifies my proactive approach to learning. It highlights my dedication to gaining hands-on experience, which is often the most effective way to grasp the nuances of system administration and Active Directory. As I progress through this project, I'm confident in my growing understanding of these critical aspects of the IT landscape.

I invite you to explore my journey further. It is a testament to my commitment to learning, adaptability in different Windows environments, and my pursuit of system admin proficiency within a Windows ecosystem.



# Resourses Utilized
- [VirtualBox](https://www.virtualbox.org/wiki/Downloads) 

**Download the version of VirtualBox that matches your host operating system (e.g., Windows, macOS, or Linux).*

- Windows Server [2019](https://www.microsoft.com/en-us/evalcenter/download-windows-server-2019) ISO image
- Windows [10](https://www.microsoft.com/en-us/software-download/windows10ISO) ISO image




# Resource installation process

**Downloading Windows Server 2019 ISO:** 

I began by finding a reliable source to download the Windows Server 2019 ISO file, which might have been the official Microsoft website or another trusted location. <br><br>
**Downloading Windows 10 ISO:**

In a similar manner, I obtained the Windows 10 ISO file from a trusted source, such as the official Microsoft website.<br><br>
**Opening VirtualBox:**

I launched the VirtualBox application, which I had previously installed.<br><br>
**Creating a New Virtual Machine for Windows Server 2019:**

Inside VirtualBox, I created a new virtual machine for Windows Server 2019.
I gave the virtual machine a name and specified the operating system type (Microsoft Windows) and version (Windows Server 2019).
I allocated memory and configured any other settings required.<br><br>
**Mounting the Windows Server 2019 ISO:**

In the settings for the Windows Server 2019 virtual machine, I navigated to the "Storage" section.
Under the "Controller: IDE" section, I selected the empty optical drive.
I chose to "Choose a disk file" and located the Windows Server 2019 ISO file that I had downloaded earlier.<br><br>
**Creating a New Virtual Machine for Windows 10:**

Similarly, I created a new virtual machine for Windows 10 within VirtualBox, giving it a name and selecting the appropriate OS type and version. <br><br>
**Mounting the Windows 10 ISO:**

In the Windows 10 virtual machine's settings, under "Storage," I mounted the Windows 10 ISO in the optical drive, just like I did for Windows Server 2019. <br><br>
**Installing Windows Server 2019:**

I started the Windows Server 2019 virtual machine.
The virtual machine booted from the Windows Server 2019 ISO.
I followed the on-screen instructions to install Windows Server 2019 within the virtual machine. <br><br>
**Installing Windows 10:**

I repeated the process for Windows 10. I started the Windows 10 virtual machine, and it booted from the Windows 10 ISO.
I followed the on-screen prompts to install Windows 10 within the virtual machine. <br><br>
**Running Both Virtual Machines:**

After the installations were complete, I could run both virtual machines simultaneously or individually by starting them from the VirtualBox application.


# Network Configuration (Virtual Box)

- The Windows Server 2019 machine plays the role of **domain controller**.
- The Windows 10 machine plays the role of **client**

## On the Windows Server 2019 machine:
 
I provisioned two network interface cards (NICs) 

The first NIC was set to **"NAT,"** and provided internet access. It allowed the server to communicate with the external internet.

The second NIC was set to **"Internal Network,"** which established a private network isolated from the external internet. This network was intended for internal communication within the lab environment.

<img width="1792" alt="Screen Shot 2023-10-20 at 1 41 41 PM" src="https://github.com/Danigan1/System-Admin-Homelab/assets/107498392/57623fd3-aaa8-4379-a3bf-8050ee6acdfc">

<img width="1792" alt="Screen Shot 2023-10-20 at 1 41 52 PM" src="https://github.com/Danigan1/System-Admin-Homelab/assets/107498392/41ba9ab6-1a78-434f-8366-3396d53bee85">

## On the Windows 10 machine:

It had a single NIC configured as **"Internal Network,"** allowing it to connect to the private, internal network established by the domain controller. 


<img width="1792" alt="Screen Shot 2023-10-20 at 1 44 09 PM" src="https://github.com/Danigan1/System-Admin-Homelab/assets/107498392/de37f4fd-02f4-4392-98cd-9b41f8d44a51">


# Network Configuration (within the virtual Machine)

Within the Windows Server, I began configuration of the two network adapters that were provisioned in virtual box

For the **NAT** network adapter. I selected the option to "Obtain an IP address automatically." This meant that my server would dynamically receive an IP address. This dynamic assignment was ideal for connecting to the internet.

Now, for the second network adapter, which was set as **"internal,"** I had to statically configure the IP settings. Here's what I applied: <br>

![image](https://github.com/Danigan1/System-Admin-Homelab/assets/107498392/0ce8a179-62f8-4830-bfda-0ce6cb4a4674)

These settings allowed me to establish an isolated internal network. Since two NICs were in play, the server was able to create a tunnel from the internal network to the external network. 

The DNS section had the the same ip address because the Windows Server was also going to be the DNS server for the any internal clients. 

Active Directory Domain Services was the next step of priority, for the purposes of facilitating a central Authority. **(DNS capability apart of this)**



# Setting up Active Directory

After I configured the two Network interface cards, I then began the process of installing Active Directory Domain Services within Windows Server 2019. Here's a summary of the steps I took to achieve this: <br>


https://github.com/Danigan1/System-Admin-Homelab/assets/107498392/68a8dc61-cefe-4e3a-949d-4b61d5f39d84

<br>

**Launch Server Manager:** I started by opening Server Manager, which is the central management console for Windows Server 2019. I typically accessed this by clicking on the Windows icon and selecting "Server Manager."

**Add Roles and Features:** Within Server Manager, I navigated to the "Manage" menu and selected "Add Roles and Features." This launched the Add Roles and Features Wizard, which I used to add the necessary role.

**Role-Based or Feature-Based Installation:** In the wizard, I chose the "Role-based or feature-based installation" option since I was installing Active Directory Domain Services as a role.

**Select a Server:** I selected my Windows Server 2019 from the server pool on which I wanted to install Active Directory Domain Services. This is the server on which I had configured the NICs.

**Select Roles:** In the "Select roles" section, I chose the "Active Directory Domain Services" role. The wizard prompted me to add any additional features that were required for this role.

**Role Services:** On the Role Services page, I didn't need to make any specific selections because Active Directory Domain Services is a single role with its associated role services.

**Confirmation:** The wizard displayed a summary of the selections I made. I reviewed them to ensure they were correct.

**Install:** Finally, I clicked "Install" to start the installation process. The server then went through the process of adding the role and configuring the necessary components.

<br>

https://github.com/Danigan1/System-Admin-Homelab/assets/107498392/5ad75be1-dd30-4cfd-81e7-9623c6168fc5

<br>

**Promote Server to Domain Controller:** After the installation was complete, the wizard prompted me to promote the server to a domain controller. I selected the "Add a new forest" option since I was creating a new Active Directory forest.
<br>

 ## ROOT Domain Name: DaniganDomain.com

<br>

**Domain Controller Options:** In this section, I provided a root domain name for my Active Directory forest. I also set a Directory Services Restore Mode (DSRM) password.

**DNS Options:** As part of the installation, I chose to install the DNS server role on the same server since it's commonly required for Active Directory.

**Additional Options:** I reviewed the NetBIOS domain name and left it at the default. I also selected the paths for the database, log files, and SYSVOL files.

**Review Settings:** The wizard displayed a summary of all the settings I had configured. I double-checked these settings to ensure they were accurate.

**Prerequisites Check:** The wizard performed a prerequisite check to make sure everything was in order before promoting the server to a domain controller. If any issues were found, I addressed them.

**Install:** Once the prerequisites were met, I clicked "Install" to begin the installation process. The server was then promoted to a domain controller, and Active Directory Domain Services were installed.

**Completion:** After the installation was completed successfully, I typically had to restart the server to finalize the configuration.

At this point, I had successfully installed Active Directory Domain Services on my Windows Server 2019, and the server became a domain controller for the new domain I created. This allowed me to manage user accounts, group policies, and other directory services within my network.

<br>

# RAS and NAT


## Routing and Remote Access (RAS):

RAS is a feature that allows the server to act as a router, providing routing services for remote clients and enabling remote access to the network. However, in the context of a domain controller, RAS typically doesn't change the server's primary role as a domain controller. The domain controller continues to manage user accounts, group policies, and authentication.
## Network Address Translation (NAT):

NAT, when configured on a domain controller, allows the server to perform a form of network address translation commonly used for sharing a single public IP address with multiple private IP addresses. NAT is often used in scenarios where multiple devices within a private network need to access resources on the internet while sharing a single public IP address. NAT alters the source IP address of outbound packets to the public IP address, and it keeps track of these translations so that when responses come back, it can forward them to the appropriate private IP address.
I installed RAS and NAT to establish a private virtual network within my virtual environment, ensuring that my Windows 10 client could access the internet while maintaining a secure and isolated network environment. This approach allowed me to control and monitor network traffic while also providing internet connectivity for the client.

## Installation

- Open Server Manager and click on Tools > **Routing and Remote Access**.
- Right-click on your domain controller and select **Configure and Enable Routing and Remote Access**.
Click Next.
- On the Configuration page, select **Network Address Translation (NAT)** and click Next.
- Under **NAT Internet Connection**, select the network interface that is internet-facing. This should be the adapter that was not manually configured earlier.
- On the **Completing the Routing and Remote Access Server Setup** page, click Finish.



https://github.com/Danigan1/System-Admin-Homelab/assets/107498392/400c29db-c449-412e-abf3-ceb1b8f40c92


## DHCP Configuration

The DHCP (Dynamic Host Configuration Protocol) feature within Windows Server was an important addition. It allowed me to streamline the process of assigning IP addresses within the domain. By setting up DHCP, any computer that joined the domain could automatically receive an IP address without manual intervention.

The DHCP server was configured with a specific scope, defining the range of IP addresses that it could assign to devices on the network. This scope included details such as the starting and ending IP addresses, subnet mask, default gateway, and DNS server information. This allowed for efficient management of IP address allocation within the domain.

Details



https://github.com/Danigan1/System-Admin-Homelab/assets/107498392/cc416528-7f3f-4971-b15b-65ce344b8740


<br>


DHCP SCOPE

- **range:** 172.16.0.100-200
- **subnet mask:** 255.255.255.0
- **Default gateway:** 172.16.0.1
- **DNS server:** 172.16.0.1
- **Lease Duration:** 8 days



# Joining Windows 10 Machine to the New Domain


First I created a user account named "Mr Person" within Active Directory **Users and computers**. Then I went over to the windows 10 machine and added the computer to the **"Danigan Domain"** under the user account.


https://github.com/Danigan1/System-Admin-Homelab/assets/107498392/59ce054d-a529-430b-828c-74967228f2fe



## Ensuring Internet Connectivity

I was happy to see that the DHCP configurations made on the Windows Server were taking effect on the windows 10 machine and it was able to access the internet through the server.

https://github.com/Danigan1/System-Admin-Homelab/assets/107498392/38965f9e-02ef-4b34-a812-e72724b0eaa1



## Creating a user account in Active Directory through powershell

This showcases A small powershell command I put together to Create one user within Active Directory **Users and computers**

https://github.com/Danigan1/System-Admin-Homelab/assets/107498392/2d6741d8-335f-49e1-8d15-87e522ac3937

<br>

With some light tweaking of the command and adding variables, the powershell command becomes more versatile and can add different users by asking for new input every iteration.


https://github.com/Danigan1/System-Admin-Homelab/assets/107498392/563a12f5-a5af-437f-b743-0c5b57c70ee1



