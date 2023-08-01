
# Introduction
  This lab report documents the process of setting up VirtualBox 7.0.8 and creating virtual machines (VMs) with Windows 10 and Ubuntu 22.04.2 ISOs.
  Additionally, it covers the configuration of networking settings to establish communication between the VMs and the host machine.

# Procedure
## 1. Installation of VirtualBox

The latest version of VirtualBox (7.0.8) was downloaded and installed. However, during the installation process, the wizard reported missing dependencies,
specifically "Python Core" and "win32api," leading to the termination of the installation.

## 2. Python Installation

To resolve the missing dependency issue, Python 3.11.4 (the latest version at the time) was downloaded and installed. 
The "pywin32" package was then installed via pip after navigating to the Python Scripts directory.

## 3. Virtual Machine Setup

### Windows 10 VM

    VirtualBox was launched, and a new VM for Windows 10 was created. The VM's RAM was set to 2048 MB, and the CPU usage was set to 1 CPU.
    A virtual disk of 10 GB was initially created, but due to insufficient disk size, it was increased to 20 GB.
    The Windows 10 VM was powered on, and the installation of Windows 10 was carried out using an ISO file downloaded from the Microsoft website.
    The VM's network adapter settings were configured to use the "Internal Network" mode.

### Ubuntu 22.04.2 VM

    A new VM for Ubuntu 22.04.2 was created with 2048 MB of RAM and 1 CPU. A virtual disk of 20 GB was allocated for the VM.
    The Ubuntu 22.04.2 VM was powered on, and the installation process was completed using the downloaded Ubuntu ISO file.
    The VM's network adapter settings were configured to use the "Internal Network" mode.

## 4. Networking Configuration

Initially, both VMs were set to use the "Internal Network" mode, but there were difficulties in establishing communication between the VMs and the host machine.
The networking mode was changed to "Host-Only," and the IP address of the VB Host-Only Ethernet Adapter was set to 192.168.100.200/24.

## 5. Troubleshooting Networking Issues

### Windows 10 VM Configuration
    The IP address of the Windows 10 VM was set to 192.168.100.2, but communication was not successful.
    Several attempts were made to add a default route, but they resulted in "Operation not permitted" errors.

### Ubuntu 22.04.2 VM Configuration

    The Ubuntu VM experienced issues opening the terminal due to a Python-related problem, which was resolved by changing the system's region and language settings.
    Network interface "enp0s3" was identified, but attempts to configure the IP address failed with "RTNETLINK" errors.

    The user "admin1" was added to the "sudo" group, but there was still no success in adding a default route.
    The VM was restarted and accessed in recovery mode. The "admin1" user was already in the "sudo" group.
    Eventually, using "sudo," the default route was successfully added, and the network interface was brought up.

    After several attempts, it was discovered that the Ubuntu VM had DHCP enabled, causing the IP address to change automatically.
    The "Host-Only" mode was selected for the Ubuntu VM, and communication between the VMs was established.

## 6. Final Configuration
    The Windows firewall was identified as the cause of ping failures between the VMs, and it was resolved by allowing the necessary traffic.
    After fixing the networking issues and changing the VMs' networking mode to "Host-Only," communication between the VMs and the host machine was successful.

# Conclusion
The setup and configuration of VirtualBox and two VMs (Windows 10 and Ubuntu 22.04.2) were completed. After resolving initial networking issues, 
the VMs were successfully communicating with each other and the host machine through the "Host-Only" mode. 
The lab demonstrated the importance of properly configuring network settings and the potential troubleshooting steps involved in resolving network-related problems. 
With the final configurations in place, the VMs are now ready for use.
