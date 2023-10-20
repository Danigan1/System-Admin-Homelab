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

- The Windows Server 2019 machine plays the postion of a **domain controller**.
- The Windows 10 Machine plays the position of a **client**

## On the Windows Server 2019 machine:
 
I implemented two network interface cards (NICs) 

The first NIC, connected to **"NAT,"** provided internet access. It allowed the server to communicate with the external internet.

The second NIC, set to **"Internal Network,"** established a private network isolated from the external internet. This network was intended for internal communication within the lab environment.

After setting up the network adapters, I powered on the Windows Server 2019 virtual machine and configured the NICs as follows:

The NIC connected to **"NAT"** was set to obtain its IP address automatically, typically through DHCP, allowing the server to access the internet and external resources.

The second NIC, which was on the internal network, was configured with a static IP address. This NIC was essential for internal network communication.

Subsequently, I installed and configured the Active Directory Domain Services role on the Windows Server 2019 machine, effectively transforming it into a domain controller for the lab network.

<img width="1792" alt="Screen Shot 2023-10-20 at 1 41 41 PM" src="https://github.com/Danigan1/System-Admin-Homelab/assets/107498392/57623fd3-aaa8-4379-a3bf-8050ee6acdfc">

<img width="1792" alt="Screen Shot 2023-10-20 at 1 41 52 PM" src="https://github.com/Danigan1/System-Admin-Homelab/assets/107498392/41ba9ab6-1a78-434f-8366-3396d53bee85">

## On the Windows 10 machine in the lab:

It had a single NIC configured as **"Internal Network,"** allowing it to connect to the private, internal network established by the domain controller.

The NIC on the Windows 10 machine was configured to obtain its IP address automatically through DHCP, with the Windows Server 2019 domain controller serving as the DHCP server.

The Windows 10 machine was also configured to use the Windows Server 2019 machine as its gateway for network communication within the lab environment.

This setup allowed the Windows 10 machine to be a part of the domain controlled by the Windows Server 2019 domain controller while using it as both the DHCP server and gateway for internal network communication.

<img width="1792" alt="Screen Shot 2023-10-20 at 1 44 09 PM" src="https://github.com/Danigan1/System-Admin-Homelab/assets/107498392/de37f4fd-02f4-4392-98cd-9b41f8d44a51">


# Steps for Network Configuration (within the virtual Machine)


- 1. **Boot Your Virtual Machine:**

Start your Windows Server 2019 virtual machine.
- 2.  **Log In:**

Log in to your Windows Server 2019 virtual machine with administrative privileges.
- 3.  **Configure IP Addresses:**

Open the "Network Connections" window.
You should see two network adapters listed: one for NAT and one for the internal network.
- 4.  **Configure IP Addresses for NAT Adapter:**

Right-click on the NAT network adapter and select "Properties."
Select "Internet Protocol Version 4 (TCP/IPv4)" and click "Properties."
Choose "Obtain an IP address automatically" or manually set the IP settings based on your requirements.
Click "OK" to save the settings.
- 5.  **Configure IP Addresses for Internal Adapter:**

Right-click on the internal network adapter and select "Properties."
Select "Internet Protocol Version 4 (TCP/IPv4)" and click "Properties."
Choose "Use the following IP address" and specify the IP address and subnet mask for the internal network adapter. There's no need to set a gateway because it's an internal network.
Click "OK" to save the settings.

![image](https://github.com/Danigan1/System-Admin-Homelab/assets/107498392/7c101ed4-76be-4272-b9df-e917fba3f79f)


## in my case


 **IP address:** 172.16.0.1 (you can set your own address as long as it doesn't overlap with other addresses) <br>
 **Subnet mask:** 255.255.255.0 (which is a /24 subnet holding up to 254 addresses available to be assigned to hosts) <br>
 **Default Gateway:** empty <br>
 **Preferred DNS:** 172.16.0.1 <br>
 **Alternate DNS:** 127.0.0.1 <br>
<br>
- 6.  **Verify Connectivity:**

Open a Command Prompt and use commands like ipconfig, ping, and tracert to verify the configuration and connectivity of both network adapters.
- 7.  **Test Network Functionality:**

Test the functionality of both network adapters by accessing resources on the NAT network (external) and the internal network as needed.



