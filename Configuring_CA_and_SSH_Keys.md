# Lab Report: Configuring SSH, Setting Up a Certificate Authority, and Achieving Interoperability Between Ubuntu and Windows 10

# Network Configuration:

    The network mode was set to "bridged" to enable internet access when downloading files.
    The network mode was switched to "NAT Network" to limit communications for testing purposes.

# Ubuntu Setup:

Initial server setup was performed on UbuntuVM2 following the guide linked.
SSH was installed using the commands:

  sudo apt update
  sudo apt install ssh
  sudo ufw allow 22

Root login issue was resolved by modifying the SSH configuration and allowing root login.
User "admvm2" was created using the command:

  sudo adduser admvm2

Sudo privileges were granted to "admvm2" using:

  sudo usermod -aG sudo admvm2

Firewall was configured using UFW.

# SSH Key Setup:

SSH keys were generated on UbuntuVM2 using the command:

  ssh-keygen

SSH key was copied to UbuntuVM1 using:

  ssh-copy-id admin1@192.168.100.7

Password authentication was disabled by modifying the SSH configuration.

# Setting Up the Certificate Authority (CA) on Ubuntu:

EasyRSA was installed and configured. A symbolic link was created to the installation directory.
The PKI was initialized and configured with necessary variables.
The CA was built using EasyRSA.
The CA certificate was copied to UbuntuVM2 and added to the certificate store.

# Windows 10 Setup:

OpenSSH was installed on Win10VM1 using PowerShell commands.
The OpenSSH.Server capability was added using PowerShell.
SSH keys were generated on Win10VM1 using PowerShell.
SSH agent was set up, and the generated key was added to the agent.
SSH connection was established to UbuntuVM1 after solving network mode and firewall issues.

# Interoperability: Windows 10 to Ubuntu:

CA certificate was copied from UbuntuVM2 to Win10VM2 and imported into the certificate store.
Win10VM2 was able to connect to UbuntuVM1 without fingerprint checks.

#Interoperability: Ubuntu to Windows 10:
An SSH key pair was generated on UbuntuVM1.
The public key was copied to Win10VM1 using "ssh-copy-id".
SSH agent was set up on UbuntuVM1 and the key was added.
SSH connection was established from UbuntuVM1 to Win10VM1 without fingerprint checks.

# Conclusion:
In this lab, we successfully configured SSH on Ubuntu and Windows 10 virtual machines, set up a Certificate Authority (CA) on Ubuntu, and established interoperability between the two platforms. SSH key pairs were generated, authentication methods were configured, and certificates were managed to enable secure communication between the virtual machines. This experience enhances our understanding of network configurations, security measures, and interoperability considerations in mixed-platform environments.
