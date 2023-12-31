# Introduction:

The objective of this lab was to design and build a simply Small Office/Home Office (SOHO) Network infrastructure for a home office or small office environment.
The network was set up using a router, and network services such as DHCP and DNS were configured. Multiple computers running Windows and Linux were
connected to the network to experiment with various network protocols, security settings, and firewall configurations.

# Procedure:
## 1. Network Infrastructure Setup

A NAT network interface was created with the IP address range 192.168.100.0/24. DHCP (Dynamic Host Configuration Protocol) was enabled on the NAT network interface to assign IP addresses automatically to connected devices. The network adapter of each Virtual Machine (VM) was changed to use the newly created NAT network interface.

## 2. Windows 10 VM Setup

In the Windows 10 VM, the network settings were accessed by going to "ncpa.cpl". The option "Obtain an IP address automatically" was applied to allow automatic IP assignment. The preferred DNS server was set to 192.168.100.0, and the option to validate settings upon exit was selected.

![Screenshot of the Windows 10 VM network configuration](https://github.com/EricKarlsson94/NetworkingLab/blob/main/Pictures/Win10VM_NetworkConfig.png)

## 3. Ubuntu VM Setup

In the Ubuntu VM, the network settings were accessed through the settings program. A new wired connection profile was added.For IPv4 settings, the "Automatic (DHCP)" method was selected, and the DNS server was set to 192.168.100.0, but automatic DNS was turned off.

![Screenshot of the Ubuntu VM network configuration](https://github.com/EricKarlsson94/NetworkingLab/blob/main/Pictures/UbuntuVM_NetworkConfig.png)

## 4. Connectivity Verification

After completing the setup, the Windows 10 VM was assigned the IP address 192.168.100.4, and the Ubuntu VM was assigned the IP address 192.168.100.5. Mutual connectivity between the VMs was verified by successfully pinging each other.

## 5. Firewall Configuration and Security Rule Test

A connection security rule named "TestRule" was created to test firewall configurations. The Windows Defender firewall was reactivated to test traffic filtering. Attempts were made to allow traffic through the default gateway and specific IP addresses, but they were unsuccessful. Allowing all traffic also failed, leading to the conclusion that proper firewall security should be implemented either through a dedicated firewall or by the domain controller rather than on individual VMs.

# Results:

The Small Office/Home Office (SOHO) Network was successfully implemented using a router with the NAT network mode.
The Windows 10 VM had the IP address 192.168.100.4, and the Ubuntu VM had the IP address 192.168.100.5.
Both VMs demonstrated mutual connectivity, as verified through successful ping responses.
However, the attempts to configure the Windows Defender firewall on the VMs were not successful,
indicating a need for better understanding or alternative firewall solutions, such as a dedicated firewall or firewall settings managed by a domain controller.

# Conclusion:

The lab successfully achieved the implementation of a Small Office/Home Office (SOHO) Network infrastructure.
The network was designed using a router with the NAT network mode, and DHCP and DNS services were configured to enable automatic IP address assignment.
Connectivity between the Windows and Linux VMs was established, demonstrating proper networking setup.
However, the firewall configuration on the individual VMs presented challenges and limitations. It was concluded that firewall security should be
handled by a dedicated firewall or the domain controller for better security and management.
