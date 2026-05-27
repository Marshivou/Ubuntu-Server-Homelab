# Ubuntu Server Installation
# Project Purpose
This project was created to practice Linux server administration, networking, remote management, and web hosting using Ubuntu Server.

# Environment

Host Machine:
- Ryzen 7 5800X
- 32GB RAM
- Fedora Workstation 44

Virtualization Software:
- VirtualBox

Guest Operating System:
- Ubuntu Server 24.04 LTS

## VM Configuration
- 4 CPU cores
- 4GB RAM
- 50GB storage

# Installation Steps

1. Downloaded Ubuntu Server ISO
2. Created Virtual Machine
3. Mounted ISO
4. Installed Ubuntu Server
5. Created administrator account
6. Rebooted into installed system

### Update Packages
```bash
sudo apt update && sudo apt upgrade -y
sudo apt install openssh-server
systemctl status ssh
