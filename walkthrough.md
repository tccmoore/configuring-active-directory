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
- This lab requires three downloads for setting up the environment: A Windows Server 2019 ISO, A Windows 10 ISO, and Oracle VirtualBox. Windows Server 2019 has an evaluation edition that can be used for 180 days with no cost. 
- Oracle VirtualBox is hypervisor that can enable you to run multiple Operating Systems that aren't directly installed on the host machine. The two ISOs will help set up Windows Server 2019 and W10 in a virtual environment.
- Windows Server 2019 ISO: https://www.microsoft.com/en-us/evalcenter/download-windows-server-2019
- Windows 10 ISO: https://www.microsoft.com/en-us/software-download/windows10
- VirtualBox: https://www.virtualbox.org/wiki/Downloads

# Part 2: Setting up the Virtual Machine
- Once you have VirtualBox installed and the ISOs downloaded, you'll need to open VirtualBox and click "New" at the top of the Window to begin creating a new VM. You'll be greeted with the following Window:

![image](https://github.com/user-attachments/assets/802afc38-7ecb-491e-896b-3d8a8fb15c37)

Under the "Name and Operating Systems" tab:
- Name -> "DC", this is short for Domain Controller, and will differentiate this VM from the client machine. 
- For "ISO Image", select the Windows Server 2019 ISO from the location that you downloaded the file to. This should automatically populate the other fields.
- Before you move on, be sure to check "Skip unattended installation". This allows you to manually handle and customize the installation process.

Under the "Hardware" Tab:
- This is where you configure the host machine's resources that can be allocated to the virtual machine. What you can allocate will heavily depend on your own machine, but I've had success with a rather minimal setup. Keep in mind that you'll need to be able to
  run **two** Virtual Machines consecutively by the end of this lab. If you have a low-performing setup, then you should use minimal resources. 
- For Base Memory, you'll want at least 2048 MB (Roughly 2 GB). I used 4 GB for a smoother experience. 
- For CPU cores, 1 core is sufficient. I used 2 out of 4 cores for better performance.

Under the "Hard Disk" Tab: 
- For the Virtual Disk Image (Storage Space), I got away with 20GB. It's enough for the purposes of this lab. For prolonged use, you'll likely need more eventually.
- VirtualBox uses dynamically-allocated storage by default, so it can be assigned more space as needed.

Once you have everything configured, click on "Finish" on the bottom right corner. A Virtual Machine named "DC" will now appear on the left side of the screen. Right-click it and select "Settings":

![image](https://github.com/user-attachments/assets/04226e1c-f94f-4ea7-9abc-4d6b2c7a6970)

For the purposes of this lab, we'll use two separate network adapters: The first will be used to connect directly to the internet using the host machine's network adapter, and the second will be used for the internal network to connect to the domain controller. The client machine
will still be able to connect to the internet, but **only** through the domain controller. It's just like any school or corporate network. That being said, click on the "Network" tab:

Under "Adapter 1":
- Select Attached To -> Bridged Adapter. This allows the Virtual Machine to directly access your host machine's physical network adapter, and additionally gives the Domain Controller a distinguished IP address on the local network. 
- Under Name, select the name of your host machine's network adapter. If you have trouble finding it, check "Control Panel\Network and Internet\Network Connections" on your host machine (Assuming that you're using Windows) and identify the device connected to your Wireless Network. 
- Select Promiscuous Mode -> Allow All. This allows the Network Interface Card to receive packets intended for multiple different devices, which is necessary for this setup due to a bridged network essentially adding a second physical machine to a single NIC.

Under "Adapter 2":
- Select Attached To -> Internal Network. The client machines will use this adapter, which restricts them to the local network. They will only be able to access external networks through the domain controller, which functions as a gatekeeper for traffic.
- For name, use "intnet" (Short for itnernal network). 
- Use the default adapter type, and keep Promiscuous Mode on "Deny". 

Once the network configuration is finished, you're ready to run the Virtual Machine and install the Operating System. Close the Settings window and double click the VM to run it. You'll find a familiar screen: 

![image](https://github.com/user-attachments/assets/47bce0ad-2e15-42ed-b940-a0a7ddc1c119)




