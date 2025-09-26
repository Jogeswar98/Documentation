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

## Domain Join Configuration: We have two options –
1. Manual setup
2. Set up through commands. 

```
sudo apt install -y realmd sssd sssd-tools libnss-sss libpam-sss adcli samba-common-bin oddjob oddjob-mkhomedir packagekit

```
![shared image (11)](https://github.com/user-attachments/assets/48652fc6-8e78-4bd6-ad51-7bed9c581e9e)

## Note :
#  After running the below-mentioned command, the domain join feature will be enabled, allowing us to add the system to the domain. Once the command is executed, the domain join feature will be activated, and it will appear as an Enterprise login. I've attached the reference image.

1. Manual Setup

Step 1:

i. Go to System Settings
ii. Navigate to Users
iii. Click on Add User

![shared image (20)](https://github.com/user-attachments/assets/b32d9fdb-9e1b-4368-8e00-847a4f9cf8ff)

iv . Now click on Enteriser login 
![shared image (15)](https://github.com/user-attachments/assets/0803015e-04f3-4a64-9cc6-930e3804846e)




