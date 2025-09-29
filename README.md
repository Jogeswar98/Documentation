# Laptop Preparation Guide for the Ubuntu Machine 

This comprehensive guide covers the preparation and configuration of Ubuntu machines, domain join installation, ManageEngine Endpoint Central installation, and antivirus installation.

---

## Prerequisites 
Before moving to the installation setup, please make sure that the following things are done on the machine.

- Ubuntu 20.04 LTS or later (**recommended: Ubuntu 22.04 LTS**)
- Administrative privileges (sudo access)
- Network connectivity to domain controllers
- Internet access for package downloads
- Hostname changed as per the laptop number format: `COMPND-LTP-****`

![shared image (7)](https://github.com/user-attachments/assets/691e460b-edf7-4a5d-82c5-42703e701807)

---

## Table of Contents  

1. [System Preparation](#1-system-preparation)  
2. [Domain Join Configuration](#2-domain-join-configuration)  
3. [ManageEngine Endpoint Central Setup](#3-manageengine-endpoint-central-setup)  
4. [Antivirus Installation](#4-antivirus-installation)  
5. [Post-Installation Verification](#5-post-installation-verification)
---

## 1. System Preparation

Open the terminal and run the commands mentioned below.

### Update package lists

```
sudo apt update
```
![shared image (12)](https://github.com/user-attachments/assets/4f94335c-4d0d-4a17-824a-a41bafe53776)

### Upgrade existing packages

```
sudo apt upgrade -y
```

---

## 2. Domain Join Configuration

We have two options for domain configuration:
1. Manual setup  
2. Setup through commands  

### Note:  
After running the below-mentioned command, the domain join feature will be activated and will appear as an **Enterprise login**.  
This step is mandatory for both methods.

```
sudo apt install -y realmd sssd sssd-tools libnss-sss libpam-sss adcli samba-common-bin oddjob oddjob-mkhomedir packagekit

```
![shared image (11)](https://github.com/user-attachments/assets/48652fc6-8e78-4bd6-ad51-7bed9c581e9e)

![shared image (11)](https://github.com/user-attachments/assets/48652fc6-8e78-4bd6-ad51-7bed9c581e9e)

---

### Opt 1. Manual Setup

- Step 1: Go to **System Settings**  
- Step 2: Navigate to **Users**  
- Step 3: Click on **Add User**  
- Step 4: Click on **Enterprise login**  

![shared image (20)](https://github.com/user-attachments/assets/e074f426-2ffb-42ce-b38f-0d02c9136240)

- Step 5: Enter the domain name: `IIPL.COM`  
- Step 6: Enter the **Username (EMP ID)** and **Password**  

![shared image (15)](https://github.com/user-attachments/assets/0803015e-04f3-4a64-9cc6-930e3804846e)

Now you will successfully add the domain

**If it's not working, then go with the setup through commands.**

### Opt 2. Set up through commands

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

**Note:** When you start typing the password, it will not be visible on the command line. Simply type it and press Enter.

You will now get the successful addition in the IIPL Domain.

---

## 3. ManageEngine Endpoint Central Setup

Step 1. Open the My Files.  
Step 2. Click on Other Locations.  
     
![shared image (4)](https://github.com/user-attachments/assets/261bb140-70da-4622-8eb1-e6601bda8861)

Step 3. Now, enter the share folder location:

```
smb://10.1.5.114
```

![shared image (17)](https://github.com/user-attachments/assets/2c3b4383-f506-4de5-9d0e-d7918dd5914f)

Step 4. The system will prompt you to enter the user name and password to enter inside 10.1.5.114.

![shared image (9)](https://github.com/user-attachments/assets/a40bebe6-efbb-4df7-8c53-dfd39a9e8d53)

Step 5: Now copy the required AV and EC package to the Downloads folder, or you can move it to any other folder as per your convenience.

To verify whether the package is available inside the folder, run the mentioned commands:

```
cd Downloads/
```

```
ls
```
![shared image (3)](https://github.com/user-attachments/assets/484588f6-cd5e-4074-990f-1af3affb830e)

Step 6: Run the command mentioned below

```
cd Downloads/
```

```
cd NoidaIndia_UEMSLinuxAgent/   # This command is used to navigate into the folder where the installation package is available.
```

```
chmod +x UEMS_LinuxAgent.bin    # This command runs to provide the execute permission to the package
```

![shared image (14)](https://github.com/user-attachments/assets/468b37db-d4e1-43c0-af14-fedd22e093da)

Step 7: Now run the installation package.

```
sudo ./UEMS_LinuxAgent.bin
```

![shared image (8)](https://github.com/user-attachments/assets/c3c17252-7790-4e1a-bcef-6b03a320f460)

The ManageEngine Endpoint Central has been installed successfully. Please verify this in the portal and approve it.

---

## 4. Antivirus Installation

Step 1. Now, enter the Downloads folder where the Antivirus package is located:

```
cd Downloads/
```
To verify the package is available, we can use the command mentioned below 
```
ls
```

```
mv 'falcon-sensor_7.24.0-17706_amd64 (1).deb' falcon-sensor_7.24.0-17706_amd64.deb
```
![shared image (13)](https://github.com/user-attachments/assets/36e502dc-07c9-4026-90c7-1408d9e981e8)

```
sudo apt install ./falcon-sensor_7.24.0-17706_amd64.deb
```
![shared image (6)](https://github.com/user-attachments/assets/6b6d272a-11c5-4cd3-bc48-3e3a1feb0ad4)

After running this, the antivirus was installed on the laptop.but its not connected with linked to your organization's Falcon cloud via the CID (Customer ID

Step 2: Now we have to mention the antivirus key to connect with to your organization's Falcon cloud via the CID (Customer ID).

sudo /opt/CrowdStrike/falconctl -s --cid=YOUR-CID-HERE

```
sudo /opt/CrowdStrike/falconctl -s --cid= DB321762BC9C4B3B8B270A3C1BB24361-33
```

```
sudo systemctl restart falcon-sensor.service
```

![shared image (16)](https://github.com/user-attachments/assets/38f75803-e379-49e3-a156-a01b174b236d)

The installation process for the Antivirus is completed.

## 5. Post-Installation Verification

```
sudo systemctl status falcon-sensor.service
```

![shared image (19)](https://github.com/user-attachments/assets/af983fd6-d792-4a3a-9541-e7a116726bf5)

You can check the laptop's status to confirm if it is running properly. All setup has now been completed.



