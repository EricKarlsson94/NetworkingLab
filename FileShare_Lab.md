# MultiPlatform Filesharing between Windows and Ubuntu

## Abstract:

The aim of this lab project was to establish cross-platform file sharing between a Windows 10 virtual machine (VM)
and a Linux VM using technologies like Samba and NFS. The primary objective was to share a folder named "Shared Folder"
from the Windows 10 VM to the Linux VM and vice versa. This report outlines the setup process and the successful establishment of the file-sharing system.

## Introduction:

Cross-platform file sharing is a critical aspect of networked environments where multiple operating systems need to
collaborate and share data seamlessly. Samba and NFS are well-established technologies that enable file sharing between
Windows and Linux systems. This lab project utilized these technologies to achieve efficient and convenient file sharing.

## Methodology:
### 1. Setup of Shared Folder in the Windows 10 VM:

    Created a folder named "Shared Folder" within the Windows 10 VM.
    

### 2. Samba Setup in Linux VM:

Temporarily changed the network mode to bridged and set up a temporary wired network profile to facilitate communication between the VMs.
Followed the official Ubuntu tutorial to install and configure Samba.
Executed the following commands in the terminal:
    sudo apt update
    sudo apt install samba

Encountered an error related to a cache lock and resolved it by using:
  
    sudo kill -9 4187

Created a new directory to serve as the Samba share:

    mkdir /home/admin1/sambashare/

Edited the Samba configuration file:

    sudo nano /etc/samba/smb.conf

Added the following lines to the configuration file:
  
    [sambashare]
        comment = Samba on Ubuntu
        path = /home/username/sambashare
        read only = no
        browsable = yes

Reverted the network mode back to NAT network bridge.
Restarted the Samba service and allowed Samba through the firewall:
    
    sudo service smbd restart
    sudo ufw allow samba

Added a Samba user:

    sudo smbpasswd -a admin1
    Password: [single space]

### 3. Setup of Ubuntu to Windows Sharing:

Started the Windows 10 VM and opened File Explorer.
Typed the following path in the address bar to access the shared file from the Linux VM:

      \\192.168.100.5\sambashare

Successfully accessed the shared folder and added a test file named "testfile" from the Windows VM, which appeared in the "sambashare" folder of the Ubuntu VM.
Created a new network location on the Windows VM by:
      Right-clicking on "This PC."
      Adding a custom network location: \\192.168.100.5.\sambashare named "Sambashare."

### 4. Setup of Windows to Ubuntu Sharing:

Accessed the Ubuntu files and used the shortcut "Ctrl+L" to enter a network location.
Entered the following location to access the shared folder from the Windows VM:

    smb://WINVM1/Share

Successfully accessed the shared folder and created a folder named "testfolder" within the "Shared" folder, which was visible in the Windows VM.
Bookmarked the shared folder in Ubuntu by right-clicking on "Shared" and selecting "Mount."

## Results:

The lab project was successful in setting up cross-platform file sharing between the Windows 10 and Ubuntu virtual 
using Samba and NFS technologies. Both VMs were able to access and modify files in each other's shared folders.

## Conclusion:

The objectives of the lab project were accomplished, and a functional cross-platform file-sharing system was
established between the Windows 10 and Ubuntu virtual machines. This demonstrated the effectiveness and usability
of Samba and NFS in enabling seamless collaboration between different operating systems in a networked environment.
File sharing is essential in various scenarios, and the implemented setup can be useful for organizations or
individuals requiring efficient data exchange between Windows and Linux platforms.
