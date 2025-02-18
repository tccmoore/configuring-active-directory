I created this home lab to simulate a corporate environment where I can practice resolving common troubleshooting and management issues in a dynamic Active Directory (AD) domain. This lab not only helps me gain hands-on experience with AD services but also deepens my understanding of what it takes to configure and manage a computer network from the ground up.

By the end of this walkthrough, you will:

   - Set up an Active Directory domain from scratch
   - Join virtualized client machines to the domain
   - Enable internet access for clients through the domain controller
   - Log in with multiple user accounts created via PowerShell

And this is just the beginning—once the domain is up and running, the possibilities for further exploration are endless:

   - Group Policy Management to automate configurations
   - Firewall Rules & Security Policies to harden the network
   - Ticketing Systems to simulate real-world IT workflows
   - Shared Drives & Permissions for file management and collaboration

All of this is achieved in a cost-free, virtualized environment using minimal resources—proving that you can build valuable, real-world experience without enterprise hardware.

# Part 1: Obtaining Utilities
- This lab requires three essential downloads: A Windows Server 2019 ISO, A Windows 10 ISO, and Oracle VirtualBox. Windows Server 2019 has an evaluation edition that can be used for 180 days with no cost. 
- Oracle VirtualBox is hypervisor that can enable you to run multiple Operating Systems that aren't directly installed on the host machine. The two ISOs will help set up Windows Server 2019 and W10 in a virtual environment.
- Windows Server 2019 ISO: https://www.microsoft.com/en-us/evalcenter/download-windows-server-2019
- Windows 10 ISO: https://www.microsoft.com/en-us/software-download/windows10
- VirtualBox: https://www.virtualbox.org/wiki/Downloads

# Part 2: Setting up the Virtual Machine
- Once you have VirtualBox installed and the ISOs downloaded, you'll need to open VirtualBox and click "New" at the top of the Window to begin creating a new VM. You'll be greeted with the following Window:
![image](https://github.com/user-attachments/assets/802afc38-7ecb-491e-896b-3d8a8fb15c37)


