# Active Directory Setup and Configuration

## Description
This project demonstrates setting up and configuring a corporate domain controller using Windows Server in a virtualized environment. It features a functional DHCP and DNS server, internet access via NAT, and a user base populated and managed through an automated PowerShell script. 

## Languages and Utilities 
- **Active Directory Domain Services:** Configured the server as a domain controller for user and group management.
- **Remote Access Service (RAS)/NAT:** Configured to enable internet access and communication with external networks. 
- **DHCP & DNS Server:** Configured to automatically lease IP Addresses to domain devices and enable domain name resolution. 
- **PowerShell:** Used to automate the processes of adding users to the domain. 

## Environments Used
- **Oracle VirtualBox:** Hypervisor used for hosting virtual machines. 
- **Windows Server 2019:** Virtualized OS used to host the domain. 
- **Windows 10 Pro:** Virtualized Client Machine joined to the domain. 

