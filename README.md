# Active Directory Home Lab

## Overview

I built this lab to get hands-on experience with Active Directory and Windows Server. I followed along with Josh Madakor's tutorial on YouTube and set everything up using VirtualBox on my Mac. The lab has two virtual machines — a Windows Server 2019 domain controller and a Windows 10 client — connected on a private internal network.

## What I Used

- VirtualBox (free)
- Windows Server 2019 Evaluation (free 180-day trial from Microsoft)
- Windows 10 Pro Evaluation (free from Microsoft)

## What I Did

**1. Set a static IP on the server**
I gave the server's internal network adapter a fixed IP address of `172.16.0.1` so that client machines could always find it on the network.

**2. Installed Active Directory Domain Services**
I added the AD DS role through Server Manager and promoted the server to a domain controller with the domain name `mydomain.com`.

**3. Created an Organizational Unit and admin account**
I created an OU called ADMINS and made a personal domain admin account (`a-jbraich`) inside it instead of using the default Administrator account.

**4. Set up NAT routing**
I configured the server to act as a router so that the internal network could reach the internet through the server's external adapter.

**5. Set up DHCP**
I installed the DHCP role and created a scope from `172.16.0.100` to `172.16.0.200` so that client machines automatically get an IP address when they connect.

**6. Created 1000+ users with PowerShell**
I used a PowerShell script to bulk create over 1000 user accounts in Active Directory. The script reads a list of names, generates usernames using first initial + last name, and creates each account automatically.

**7. Set up the Windows 10 client**
I created a Windows 10 VM, joined it to `mydomain.com`, and verified it received an IP from the DHCP server. I was then able to log into the client using any of the accounts created by the script.

## Screenshots

### Static IP setup
![Static IP](screenshots/S1.jpeg)

### Installing AD DS role
![AD DS Role](screenshots/S2.jpg)

### Promoting server to domain controller
![DC Promotion](screenshots/S3.jpg)

### Creating the ADMINS OU
![ADMINS OU](screenshots/S4.jpg)

### Creating my admin account
![Admin Account](screenshots/S5.jpg)

### Adding account to Domain Admins group
![Domain Admins](screenshots/S6.jpg)

### Configuring NAT routing
![NAT Routing](screenshots/S7.jpg)

### Installing DHCP role
![DHCP Install](screenshots/S8.jpg)

### Configuring DHCP scope
![DHCP Scope](screenshots/S9.jpg)

### Setting default gateway in DHCP
![Default Gateway](screenshots/S10.jpg)

### Names list for bulk user creation
![Names List](screenshots/S11.jpg)

### PowerShell script open in ISE
![PowerShell Script](screenshots/S12.jpg)

### Bulk user accounts being created
![Bulk Users](screenshots/S13.jpg)

### ipconfig on Windows 10 client showing DHCP worked
![ipconfig](screenshots/S14.jpg)

### Joining Windows 10 to the domain
![Domain Join](screenshots/S15.jpg)

### DHCP lease showing client got an IP
![DHCP Lease](screenshots/S16.jpg)

## Reference

- Tutorial by Josh Madakor: https://www.youtube.com/watch?v=MHsI8hJmggI
- PowerShell script: https://github.com/joshmadakor1/AD_PS
# active-directory-home-lab
