# Troubleshooting Log

This document contains issues encountered during deployment and configuration of the Ubuntu Server homelab environment.

---

# Issue 1 - No Internet Connectivity

## Problem
Ubuntu Server VM could not access the internet after installation.

## Symptoms
- ping google.com failed
- apt update could not reach repositories

## Cause
Incorrect VirtualBox network adapter configuration.

## Diagnosis Steps

Checked IP configuration:

```bash
ip a
```

Observed:
- No valid IP address assigned

Checked routing table:

```bash
ip route
```

Verified VirtualBox adapter settings.

## Resolution

Changed VirtualBox network mode from:
- NAT

to:
- Bridged Adapter

Restarted networking and rebooted VM.

## Verification

```bash
ping google.com
```

Successful replies received.

## Lessons Learned
- Learned difference between NAT and bridged networking
- Learned importance of verifying IP assignment
- Improved understanding of VM networking

---

# Issue 2 - SSH Connection Refused

## Problem
Could not connect to Ubuntu Server remotely using SSH.

## Symptoms
Windows PowerShell returned:

```text
Connection refused
```

## Cause
SSH service was not installed and running.

## Diagnosis Steps

Checked SSH service status:

```bash
systemctl status ssh
```

Observed:
- Unit ssh.service could not be found

## Resolution

Installed OpenSSH server:

```bash
sudo apt install openssh-server
```

Started and enabled service:

```bash
sudo systemctl enable ssh
sudo systemctl start ssh
```

## Verification

Successfully connected from Windows:

```powershell
ssh username@192.168.1.115
```

## Lessons Learned
- Learned how Linux services are managed
- Practiced remote administration setup
- Learned importance of service verification

---

# Issue 3 - Nginx Web Page Inaccessible

## Problem
Could not access hosted web page from another device.

## Symptoms
Browser returned:
- Connection timed out

## Cause
Firewall blocked HTTP traffic on port 80.

## Diagnosis Steps

Checked Nginx service:

```bash
systemctl status nginx
```

Verified:
- Nginx was active and running

Checked firewall rules:

```bash
sudo ufw status
```

Observed:
- Port 80 was not allowed

## Resolution

Allowed HTTP traffic:

```bash
sudo ufw allow 80/tcp
```

## Verification

Successfully accessed:
```text
http://192.168.1.115
```

## Lessons Learned
- Learned relationship between services and firewall rules
- Improved understanding of HTTP traffic
- Practiced troubleshooting layered networking issues
