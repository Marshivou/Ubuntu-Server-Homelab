# Ubuntu Server Installation
# Project Purpose

This project was created to practice Linux server administration, networking, remote management, and web hosting using Ubuntu Server.

## VM Configuration
- 4 CPU cores
- 4GB RAM
- 50GB storage

## Installation Steps

### Update Packages
```bash
sudo apt update && sudo apt upgrade -y
sudo apt install openssh-server
systemctl status ssh
