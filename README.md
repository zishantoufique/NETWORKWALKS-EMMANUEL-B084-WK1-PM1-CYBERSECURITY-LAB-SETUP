# 🔐 Cybersecurity Virtual Lab Setup

### Building a Virtual Cybersecurity Lab Using VirtualBox and Kali Linux

## 📌 1. Project Overview

This project documents my journey of building a virtual cybersecurity lab using Oracle VirtualBox and Kali Linux.

The main objective is to create a controlled environment for learning networking, cybersecurity, ethical hacking, penetration testing, and security tools.

I configured Kali Linux as my primary virtual machine and worked on virtual networking, IP configuration, shared folders, and connectivity testing.

## 🎯 2. Project Objectives

- Install and configure Oracle VirtualBox.
- Install Kali Linux using the official ISO image.
- Create and configure a virtual machine.
- Set up a NAT Network.
- Configure a static IPv4 address.
- Enable clipboard and drag-and-drop sharing.
- Configure a shared folder between Windows and Kali Linux.
- Test network connectivity and DNS resolution.
- Create a VM snapshot for recovery.
- Document technical challenges and solutions.

## 💻 3. My Laptop Specifications
<img width="1280" height="800" alt="kali-network-setting" src="https://github.com/user-attachments/assets/0e1b61b0-6fdd-4454-a322-a02449323635" />

| Component | Configuration |
|---|---|
| Host Operating System | Windows 11 |
| Processor | AMD |
| Host RAM | 16 GB |
| Virtualization Software | Oracle VirtualBox 7.2.22 |
| Guest Operating System | Kali Linux 2026.3 |
| VM RAM | 6 GB (6144 MB) |
| VM Processors | 2 CPUs |
| Virtual Disk | Approximately 42 GB |

## 🌐 4. Virtual Network Configuration
<img width="1160" height="814" alt="laptop-specification" src="https://github.com/user-attachments/assets/f6ba5236-d0df-42c4-974c-24b62f287f53" />
| Setting | Configuration |
|---|---|
| Network Type | NAT Network |
| Network Name | NATNetwork |
| Network Address | 10.0.0.0/24 |
| Kali IP Address | 10.0.0.2/24 |
| Default Gateway | 10.0.0.1 |
| DNS Servers Configured | 8.8.8.8|

### Network Configuration

The Kali Linux network interface was configured with the IP address:

`10.0.0.2/24`

The network interface was checked using:

```bash
ip -4 addr show eth0
```
<img width="1280" height="800" alt="ip-configuration" src="https://github.com/user-attachments/assets/104cf348-4080-4ca1-beda-ec3eb64aab57" />

The interface showed the configured IPv4 address.

## ⚙️ 5. Lab Setup Procedure

### Step 1: Install Oracle VirtualBox

<img width="1535" height="811" alt="virtualbox-version" src="https://github.com/user-attachments/assets/4cb1a484-15a7-48cb-9f3a-3cd1daccf064" />

Installed Oracle VirtualBox 7.2.22 on my Windows 11 laptop.


### Step 2: Download and Install Kali Linux
<img width="1280" height="800" alt="kali-desktop" src="https://github.com/user-attachments/assets/ff847245-d801-4408-b076-91165f9bcde6" />


Downloaded the official Kali Linux 2026.3 installer ISO and installed it as a virtual machine.

Selected the Xfce desktop environment.

### Step 3: Configure the Virtual Machine

Configured the virtual machine with:

- 6 GB RAM
- 2 CPU cores
- Approximately 42 GB virtual disk
- Kali Linux 2026.3

### Step 4: Configure NAT Network
<img width="1535" height="811" alt="nat-network" src="https://github.com/user-attachments/assets/78b4ddec-4637-4afe-9c55-c014855523ad" />

Created a NAT Network named `NATNetwork` with the IPv4 network:

`10.0.0.0/24`

Configured the Kali VM network adapter to use this NAT Network.

### Step 5: Configure Kali Linux IP Address
<img width="1280" height="800" alt="kali-network-setting" src="https://github.com/user-attachments/assets/432ad9c0-369e-4b68-8a48-7afb33ff79b0" />

Configured and verified the Kali network interface with:

`10.0.0.2/24`

### Step 6: Configure Shared Folder

Created a shared folder between Windows and Kali Linux.

| Host Windows | Kali Linux |
|---|---|
| D:\downloads | /media/sf_downloads |

Enabled the shared folder in VirtualBox and verified its accessibility from Kali Linux.

Tested the folder using:

```bash
ls /media/sf_downloads
```
<img width="1280" height="800" alt="shared-folder" src="https://github.com/user-attachments/assets/c9ce9cfc-52de-4316-911c-2d5f8ca3e91f" />


Also tested file creation inside the shared folder.

### Step 7: Configure Clipboard and Drag-and-Drop
<img width="1533" height="817" alt="bidirectional" src="https://github.com/user-attachments/assets/c3fa7636-9a5d-4924-aa2f-981ecadeca93" />

Enabled bidirectional clipboard and drag-and-drop settings in VirtualBox.

## 🔎 6. Network Verification

The following commands were used during network troubleshooting.

| Purpose | Command |
|---|---|
| Check IP address | `ip -4 addr show eth0` |
| Check routing table | `ip route` |
| Test gateway | `ping -c 4 10.0.0.1` |
| Test internet connectivity | `ping -c 4 8.8.8.8` |
| Test DNS resolution | `nslookup google.com` |
| Check DNS configuration | `cat /etc/resolv.conf` |
<img width="516" height="413" alt="Screenshot 2026-10-30 130028" src="https://github.com/user-attachments/assets/ea65c3bf-c66a-4f1b-b5a3-141d16c92fff" />


### Current Verification Status

- Kali Linux installation: Completed
- Static IP configuration: Verified
- Shared folder access: Verified
- Initial gateway connectivity test: 0% packet loss reported
- External internet connectivity: Still troubleshooting
- DNS resolution: Not working yet
- Virtual machine snapshot: Pending verification

## 🐞 7. Challenges Faced During Setup

### Problem 1: VirtualBox Network Connectivity

Initially, Kali Linux was unable to obtain an IPv4 address through the NAT Network.

I investigated the NetworkManager configuration and tested the standard NAT adapter to identify the source of the issue.

### Problem 2: Shared Folder Not Appearing

Initially, the shared folder was not visible inside Kali Linux.

I checked the VirtualBox shared-folder settings, enabled auto-mount, and verified the mounted directory:

`/media/sf_downloads`

### Problem 3: Guest Additions Integration

I encountered errors while running VirtualBox shared-folder commands and checking the Guest Additions service.

I investigated the issue and verified that the shared-folder mount was accessible.

### Problem 4: DNS Resolution Failure

During testing, `nslookup google.com` returned:

```text
communications error to 8.8.8.8#53:
network unreachable

no servers could be reached
```

The DNS servers were configured, but Kali Linux could not reach them. Further network troubleshooting is required.

### Problem 5: Network Packet Loss

During initial connectivity testing, packet loss was observed. After troubleshooting, a subsequent test reported 0% packet loss.

## 📚 8. What I Learned

Through this project, I gained practical experience with:

1. Virtual machine creation and configuration.
2. Installing Kali Linux using an ISO image.
3. Understanding NAT and NAT Network.
4. IPv4 addressing and subnet masks.
5. Network interface configuration in Linux.
6. Shared folders between host and guest systems.
7. Linux terminal commands.
8. Network connectivity and DNS troubleshooting.
9. Documenting technical errors and troubleshooting steps.

## 🔒 9. Security and Ethical Use

This laboratory is intended for educational purposes, cybersecurity learning, and authorized security testing only.

Any future penetration-testing activities will be conducted only on systems that I own or have explicit permission to test.

## 🔗 10. Tools and Resources

- Oracle VirtualBox: https://www.virtualbox.org/
- Kali Linux: https://www.kali.org/get-kali/
- GitHub: https://github.com/

## 👤 11. Author

**Name:** Zishan Toufique

**Field:** Cybersecurity

**Project:** Virtual Cybersecurity Lab Setup

**Platform:** GitHub

---

*This repository documents my actual setup process, configurations, troubleshooting experience, and learning outcomes. It will be updated as I complete the remaining lab requirements.*
