# Laptop preparation guide for the Ubuntu Machine 

This comprehensive guide covers the preparation and configuration of Ubuntu machines, domain join installation, ManageEngine Endpoint Central installation, and antivirus installation.

## Prerequisites: Before moving to the installation setup, please make sure that the following things are done on the machine.
.
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

## Note :
#  After running the below-mentioned command, once the command is executed, the domain join feature will be activated, and it will appear as an Enterprise login. This command is mendatory for the both steps once you run this command then  I've attached the reference image.

```
sudo apt install -y realmd sssd sssd-tools libnss-sss libpam-sss adcli samba-common-bin oddjob oddjob-mkhomedir packagekit

```
![shared image (11)](https://github.com/user-attachments/assets/48652fc6-8e78-4bd6-ad51-7bed9c581e9e)

# Opt 1. Manual Setup

Step 1: Go to System Settings

Step 2: Navigate to Users

Step 3:  Click on Add User

Step 4: Now, click on Enteriser login

![shared image (20)](https://github.com/user-attachments/assets/e074f426-2ffb-42ce-b38f-0d02c9136240)

Step 5: Now, enter the Domain name IIPL.COM.

Step 6: Enter the user name ( EMP ID ) and the Password

![shared image (15)](https://github.com/user-attachments/assets/0803015e-04f3-4a64-9cc6-930e3804846e)

Now you will successfully add the domain to the laptop. 

# If it's not working, then go with the setup of through commands.

# Opt 2. Set up through commands 

Step 1. Run the command mentioned below:

```
sudo apt install -y realmd sssd sssd-tools libnss-sss libpam-sss adcli samba-common-bin oddjob oddjob-mkhomedir packagekit

```
Step 2. To join the domain, use this command:
```
sudo realm join --user=<DOMAIN_USERNAME> iipl.com

```
![shared image (5)](https://github.com/user-attachments/assets/fc8ea8ea-338d-4343-91c1-b279e6a514e0)

Example: sudo realm join --user=17204 iipl.com

Once you run this command, the system will prompt for the username and password. Enter the password specified in the command.

# Note: When you start typing the password, it will not be visible on the command line. Simply type it and press Enter.”

Now will get the successful addition in the IIPL Domain.



