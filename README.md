A Virtual Lab Environment for Cybersecurity Learning and Practical Exercises

• Project Overview

This project documents the setup of a basic cybersecurity lab environment using Oracle VirtualBox and Kali Linux as part of 
Week 1 of the Network Walks Cybersecurity Internship under the guidance of Waqas Karim Sir.

The main purpose of this project is to create a virtual environment where cybersecurity tools, networking concepts, and ethical hacking techniques can be explored safely without affecting the host computer.

Kali Linux is used as the virtual machine, while VirtualBox provides the platform to run and manage the virtual environment.

•Project Objectives

Install and configure 7-Zip and Oracle VirtualBox.
Download and import the Kali Linux virtual machine.
Create a dedicated NAT Network.
Configure the virtual machine's network adapter.
Enable shared clipboard and drag-and-drop features.
Configure a shared folder between Windows and Kali Linux.
Assign and verify a static IP address.
Test network and internet connectivity.
Create a snapshot of the configured virtual machine.
Document the complete setup process.

•Tools and Technologies Used

| Tool | Purpose |
|---|---|
| Oracle VirtualBox | Creating and managing virtual machines |
| Kali Linux | Cybersecurity and penetration-testing environment |
| 7-Zip | Extracting compressed Kali Linux files |
| Windows OS | Host operating system |
| Command Line / Terminal | Network configuration and testing |
| GitHub | Project documentation and version control |

Lab Configuration

The following configuration is based on the reference lab setup. Update any values that differ from your actual system.

| Component | Configuration |
|---|---|
| Host Operating System | Windows |
| Virtualization Software | Oracle VirtualBox |
| Virtual Machine | Kali Linux (64-bit) |
| Virtual Network | NAT Network |
| Network Name | `NatNetwork` |
| Network Address | `10.0.0.0/24` |
| DHCP | Disabled |
| Kali Linux IP | `10.0.0.2/24` |
| Default Gateway | `10.0.0.1` |
| DNS Server | `8.8.8.8` |
| Shared Clipboard | Bidirectional |
| Drag and Drop | Bidirectional |

•Step-by-Step Implementation

Step 1: Install 7-Zip

7-Zip is used to extract the compressed Kali Linux virtual machine files.

1. Visit the official 7-Zip website.
2. Download the compatible version.
3. Install it on the Windows system.
4. Verify that the application is installed successfully.

Step 2: Install Oracle VirtualBox

VirtualBox is a virtualization platform that allows multiple operating systems to run on a single computer.

1. Visit the official VirtualBox website.
2. Download the Windows installer.
3. Run the installer and follow the installation instructions.
4. Open VirtualBox after installation.
5. Verify that it launches successfully.

Step 3: Download Kali Linux

1. Visit the official Kali Linux website.
2. Navigate to the Virtual Machines section.
3. Download the pre-built VirtualBox image.
4. Extract the downloaded archive using 7-Zip.
5. Locate the extracted virtual machine configuration file.

Step 4: Import Kali Linux into VirtualBox

1. Open Oracle VirtualBox.
2. Locate the extracted Kali Linux virtual machine.
3. Open the `.vbox` configuration file or use the import option if required by the downloaded image.
4. Wait for the virtual machine to appear in VirtualBox.
5. Check the VM settings before starting it.

Step 5: Create a NAT Network

A NAT Network allows virtual machines connected to it to communicate with each other and access the internet.

1. Open VirtualBox.
2. Navigate to File → Tools → Network Manager.
3. Select the NAT Networks section.
4. Create a new NAT Network.
5. Configure the network using the required settings.

•Reference configuration:

- Network Name: `NatNetwork`
- IPv4 Prefix: `10.0.0.0/24`
- DHCP: Disabled
- IPv6: Disabled

Step 6: Configure the Kali Linux Network Adapter

1. Select the Kali Linux virtual machine.
2. Open Settings → Network.
3. Enable Adapter 1.
4. Select NAT Network as the attachment type.
5. Choose `NatNetwork`.
6. Ensure that the Cable Connected option is enabled.
7. Save the configuration.

Step 7: Enable Shared Clipboard and Drag-and-Drop

These features allow convenient communication between the host operating system and the virtual machine.

1. Open Kali Linux VM settings.
2. Navigate to **General → Advanced** or the Features section, depending on the VirtualBox version.
3. Set Shared Clipboard to Bidirectional.
4. Set Drag and Drop to Bidirectional.
5. Save the changes.

Step 8: Configure a Shared Folder

A shared folder allows files to be accessed between Windows and Kali Linux.

1. Open the VM settings.
2. Navigate to Shared Folders.
3. Add a folder from the Windows system.
4. Enable Auto-mount and Make Permanent.
5. Start Kali Linux and verify that the folder is accessible.

If required, add the Kali user to the shared-folder group:

```bash
sudo usermod -aG vboxsf kali
sudo reboot
```

Step 9: Configure a Static IP Address

A static IP address provides a fixed network address to the Kali Linux virtual machine.

•Reference network settings:

- Method: Manual
- Address: `10.0.0.2`
- Netmask: `24`
- Gateway: `10.0.0.1`
- DNS: `8.8.8.8`

The configuration can also be applied through the terminal, if the connection name and network details match your setup:

```bash
sudo nmcli con mod "Wired connection 1" ipv4.method manual \
ipv4.addresses 10.0.0.2/24 ipv4.gateway 10.0.0.1 ipv4.dns 8.8.8.8

sudo nmcli con up "Wired connection 1"
```

Step 10: Verify Network Connectivity

After configuring the network, connectivity can be checked using terminal commands.

Check IP configuration:

```bash
ip a
```

This command displays the network interfaces and their assigned IP addresses.

Test internet connectivity:

```bash
ping -c 4 google.com
```

This command sends four packets to check whether the system can reach the destination and resolve its domain name.

Test gateway connectivity:

```bash
ping -c 3 10.0.0.1
```

Successful replies indicate that the gateway is reachable.

Step 11: Take a Virtual Machine Snapshot

A snapshot saves the current state of the virtual machine.

1. Open VirtualBox.
2. Select the configured Kali Linux VM.
3. Navigate to the Snapshots section.
4. Select Take Snapshot.
5. Give it a suitable name, such as `Initial_Lab_Setup`.

This allows the virtual machine to be restored to its saved state if future experiments cause configuration issues.

•Lab Verification

| Task | Command / Method | Expected Verification |
|---|---|---|
| Check IP address | `ip a` | Displays assigned IP |
| Check gateway | `ping -c 3 10.0.0.1` | Receives replies |
| Check internet | `ping -c 4 google.com` | Receives replies |
| Shared folder | `ls /downloads` | Displays shared files |
| Snapshot | VirtualBox Snapshots | Snapshot is saved |

•Challenges and Troubleshooting

During my virtual lab setup, I faced a few technical issues while configuring Kali Linux and VirtualBox. Some of the challenges I encountered were:

Network Connectivity Issues:Initially, my Kali Linux VM was unable to connect to the network. I checked the network adapter settings and made sure the correct NAT Network was selected and enabled.

IP Configuration Errors: I faced difficulties while assigning the static IP address. I rechecked the IP address, subnet prefix, gateway, and DNS settings to ensure that the network configuration was correct.

Shared Folder Access Issues: I had trouble accessing the shared folder between Windows and Kali Linux. I revisited the shared-folder settings and checked the required permissions to resolve the issue.

Virtual Machine Startup Issues: I also faced issues while starting the virtual machine. I checked the downloaded Kali Linux image and reviewed the system resources allocated to the VM.

I resolved these issues by troubleshooting each configuration step individually, checking the settings carefully, and testing the setup again. This helped me understand the importance of patience and systematic troubleshooting while working with virtual environments.

•What I Learned Through this practical, I gained knowledge of:

1. Understanding virtualization and how virtual machines work.
2. Installing and configuring VirtualBox and Kali Linux.
3. Learning the difference between NAT and NAT Network.
4. Understanding IP addresses, gateways, DNS, and static IP configuration.
5. Setting up communication between the host system and virtual machine.
6. Using Linux terminal commands for network verification.
7. Understanding the importance of snapshots and system recovery.
8. Documenting technical work through GitHub.

•Security and Ethical Considerations

This virtual lab is intended for educational purposes and authorised cybersecurity practice only. All testing should be performed on systems owned by me or where explicit permission has been provided.

• References and Resources

- 7-Zip: https://www.7-zip.org/
- Oracle VirtualBox: https://www.virtualbox.org/wiki/Downloads
- Kali Linux: https://www.kali.org/get-kali/

#Author

Tejal Patil  
Cybersecurity Intern  
Network Walks

•Project Information

- Program: Network Walks Cybersecurity Internship
- Week: 01
- Project: Cybersecurity Lab Setup
- Tools:VirtualBox, Kali Linux, 7-Zip
- Documentation Platform:GitHub

This project is part of my learning journey in cybersecurity, focusing on virtualization, networking fundamentals, and practical lab configuration.
