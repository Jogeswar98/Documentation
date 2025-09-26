# Laptop preparation guide for the Ubuntu Machine 

This comprehensive guide covers the preparation and configuration of Ubuntu machines, domain join installation, ManageEngine Endpoint Central installation, and antivirus installation.

## Prerequisites: Before moving to the installation setup, please make sure that the following things are done on the machine.
Ubuntu 20.04 LTS or later (recommended: Ubuntu 22.04 LTS)
Administrative privileges (sudo access)
Network connectivity to domain controllers
Internet access for package downloads
Hostname change as per the laptop no like:  COMPND-LTP-****

![shared image (7)](https://github.com/user-attachments/assets/691e460b-edf7-4a5d-82c5-42703e701807)

## Table of Contents
System Preparation
Domain Join Configuration
ManageEngine Endpoint Central Setup
Antivirus Installation
Post-Installation Verification
Troubleshooting

## System Preparation: Open the terminal, run the commands mentioned below.
# Update package lists
```
sudo apt update
```
![shared image (12)](https://github.com/user-attachments/assets/4f94335c-4d0d-4a17-824a-a41bafe53776)

# Upgrade existing packages
```
sudo apt upgrade -y
```

## Domain Join Configuration: 

# Install packages needed for domain operations
```
sudo apt install -y realmd sssd sssd-tools libnss-sss libpam-sss adcli samba-common-bin oddjob oddjob-mkhomedir packagekit
```
![shared image (11)](https://github.com/user-attachments/assets/48652fc6-8e78-4bd6-ad51-7bed9c581e9e)



