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



# Prerequisites (things that need to be downloaded)
- [VirtualBox](https://www.virtualbox.org/wiki/Downloads) 

**Download the version of VirtualBox that matches your host operating system (e.g., Windows, macOS, or Linux).*

- Windows Server [2019](https://www.microsoft.com/en-us/evalcenter/download-windows-server-2019) ISO image
- Windows [10](https://www.microsoft.com/en-us/software-download/windows10ISO) ISO image




# Step By Step Installation

After downloading the two ISO images and Virtual Box. You will then want to..


 **Install Windows Server 2019 in VirtualBox:**

a. Open VirtualBox after installation.

b. Click on **"New"** to create a new virtual machine.

c. Follow the New Virtual Machine Wizard:

- Give your virtual machine a name and select the appropriate type (Microsoft Windows) and version (Windows Server 2019 (64-bit)).
- Assign the desired amount of RAM to the virtual machine. Windows Server 2019 typically requires at least 2 GB of RAM.
- Create a new virtual hard disk or use an existing one. Allocate enough storage space for your needs; 50 GB or more is a good starting point.
- Configure additional settings as needed.
  
d. Click **"Create"** to finish setting up the virtual machine.

e. Select your new virtual machine in the VirtualBox Manager and click **"Start."**

f. When prompted, choose the Windows Server 2019 ISO you downloaded in step 2 as the installation media.

g. Follow the on-screen instructions to install Windows Server 2019 on your virtual machine. You'll need to enter the product key, configure settings, and create an admin password.

**Note that if you choose to install any version that doesn't have "Desktop Experience", you will not be given a GUI.*

![windwos gif](https://github.com/Danigan1/System-Admin-Homelab/assets/107498392/b723053a-2f77-427a-8df7-162d82afbed3)


**Install Windows 10 in VirtualBox:**

a. If you want to install Windows 10 as well, create a new virtual machine in VirtualBox following similar steps as for Windows Server 2019.

b. During the setup, use the Windows 10 ISO you downloaded in step 3 as the installation media.

c. Follow the on-screen instructions to install Windows 10 on the second virtual machine.

Once you've completed these steps, you should have both Windows Server 2019 and Windows 10 running as virtual machines in VirtualBox on your computer. You can start, stop, and manage these virtual machines within VirtualBox as needed.



# Network Configuration (Virtual Box)

- The Windows Server 2019 machine plays the role of **domain controller**.
- The Windows 10 machine plays the role of **client**

## On the Windows Server 2019 machine:
 
I provisioned two network interface cards (NICs) 

The first NIC, set to **"NAT,"** provided internet access. It allowed the server to communicate with the external internet.

The second NIC, set to **"Internal Network,"** established a private network isolated from the external internet. This network was intended for internal communication within the lab environment.

<img width="1792" alt="Screen Shot 2023-10-20 at 1 41 41 PM" src="https://github.com/Danigan1/System-Admin-Homelab/assets/107498392/57623fd3-aaa8-4379-a3bf-8050ee6acdfc">

<img width="1792" alt="Screen Shot 2023-10-20 at 1 41 52 PM" src="https://github.com/Danigan1/System-Admin-Homelab/assets/107498392/41ba9ab6-1a78-434f-8366-3396d53bee85">

## On the Windows 10 machine in the lab:

It had a single NIC configured as **"Internal Network,"** allowing it to connect to the private, internal network established by the domain controller. 

Ultimately, the Windows 10 machine was going to be configured to obtain its IP address automatically through DHCP, with the Windows Server 2019 domain controller serving as the DHCP server.

Additionally, the Windows server was going to be a default gateway for reaching the outer internet.


<img width="1792" alt="Screen Shot 2023-10-20 at 1 44 09 PM" src="https://github.com/Danigan1/System-Admin-Homelab/assets/107498392/de37f4fd-02f4-4392-98cd-9b41f8d44a51">


# Network Configuration (within the virtual Machine)

Within the Windows Server 2019 machine, I had to configure the two network adapters within the "Network Connections" section to create a more versatile network setup.

For the NAT network adapter. I selected the option to "Obtain an IP address automatically." This meant that my server would dynamically receive an IP address from my home router. This dynamic assignment was ideal for connecting to the internet and ensuring the server received the necessary IP configuration from my home network.

Now, for the second network adapter, which was set as "internal," I had to statically configure the IP settings. Here's what I applied: <br>

**IP Address:** 172.16.0.1 <br>
**Subnet Mask:** 255.255.255.0 <br>
**Default Gateway:** I left this field empty since it was an internal network.<br>
**Preferred DNS:** 172.16.0.1<br>
**Alternate DNS:** 127.0.0.1<br>

These settings allowed me to establish an isolated internal network. The IP address of 172.16.0.1 served as the gateway for this network, and I used the same address as the preferred DNS server. Since this network was for internal use only, there was no need for a default gateway to connect to external networks. The alternate DNS address of 127.0.0.1 pointed back to the local machine, ensuring efficient DNS resolution for the internal network.

By configuring these network adapters in the "Network Connections" section of Windows Server 2019, I created a network environment that provided both internet access and an isolated internal network to meet my specific requirements in my home lab.

Subsequently, I installed and configured the Active Directory Domain Services role on the Windows Server 2019 machine, effectively transforming it into a domain controller for the lab network.






