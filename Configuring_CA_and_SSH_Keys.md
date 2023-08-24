# Introduction

This lab report outlines the process of setting up SSH (Secure Shell) communication and a Certificate Authority (CA) for interoperability between Ubuntu and Windows 10 virtual machines. The primary goal is to establish secure communication between these two operating systems using SSH keys and certificates.
Ubuntu Setup
## Initial Setup

Following the guide [Initial Server Setup with Ubuntu 22.04 (digitalocean.com)](https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-22-04), initial configuration of UbuntuVM2 was performed.

Attempting SSH connection using the command
    "ssh root@192.168.100.7"
was initially refused.

Installed SSH using:
    "sudo apt update", 
    "sudo apt install ssh"
and allowed SSH traffic through the firewall with 
    "sudo ufw allow 22".

Modified SSH configuration to allow root login by changing "#PermitRootLogin" to "PermitRootLogin yes" and restarting the sshd service.

Added user "admvm2" using 
    "adduser admvm2"
granting sudo privileges with 
    "usermod -aG sudo admvm2".

## Setting up SSH Keys

Generated SSH keys on UbuntuVM2 using "ssh-keygen".

Copied the public key to UbuntuVM1 using "ssh-copy-id admin1@192.168.100.7".

Disabled password authentication by modifying "/etc/ssh/sshd_config" and changing "#PasswordAuthentication yes" to "PasswordAuthentication no".

## Setting up the CA

Installed easy-rsa on UbuntuVM2 with "sudo apt install easy-rsa".

Created symbolic link between "/usr/share/easy-rsa/" and "~/easy-rsa/".

Restricted access to "~/easy-rsa/" using "chmod 700 /home/admvm2/easy-rsa".

Initialized the PKI with "./easyrsa init-pki".

Created a "vars" file in "~/easy-rsa/" with specific variables.

Built the CA with "./easyrsa build-ca", providing passphrase and leaving CN as default.

Imported the CA certificate to UbuntuVM2 using "cat ~/easy-rsa/pki/ca.crt" and copying it to "/tmp/ca.crt".

Updated certificate storage with "sudo cp /tmp/ca.crt /usr/local/share/ca-certificates/" and "sudo update-ca-certificates".

# Windows 10 Setup
## Setting up SSH Keys

Installed OpenSSH on Win10VM1 using PowerShell.

Generated SSH key with "ssh-keygen -t ed25519" and started ssh-agent with "ssh-agent" and "ssh-add".

Manually exchanged SSH keys between Win10VM1 and Win10VM2.

# Interoperability Setup
## Windows 10 to Ubuntu

Tested SSH connection from Win10VM2 to UbuntuVM1 using "ssh admvm2@192.168.100.7".

Imported CA certificate "tmp_ca.crt" into Windows certificate storage.

## Ubuntu to Windows 10

Generated SSH key on UbuntuVM1 named "target_id_ed25519".

Copied the public key to Win10VM1 using "ssh-copy-id admin@192.168.100.6".

Setup ssh-agent on UbuntuVM1 with "ssh-add ~/target_id_ed25519".

Established SSH connection from UbuntuVM1 to Win10VM1.

# Conclusion

The lab successfully achieved SSH-based interoperability between Ubuntu and Windows 10 virtual machines through the setup of SSH keys and a Certificate Authority. SSH keys were generated, exchanged, and stored securely, allowing passwordless communication between the VMs. Additionally, a Certificate Authority was established to enhance security and ensure trust between the systems. This project provides a foundation for future projects involving secure communication and interoperability between different operating systems.
