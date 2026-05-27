# Nginx Web Server Setup

## Objective

Install and configure Nginx on Ubuntu Server to host a basic web page and practice Linux server administration.

---

# Installing Nginx

Updated package repositories:

```bash
sudo apt update
```

Installed Nginx:

```bash
sudo apt install nginx -y
```

---

# Verifying Installation

Checked service status:

```bash
systemctl status nginx
```

Verified that the Nginx service was:
- active
- running
- enabled at boot

---

# Testing the Web Server

Tested locally on the server:

```bash
curl localhost
```

Result:
- Received default Nginx HTML response

Tested from another device using browser:

```text
http://192.168.1.115
```

Result:
- Successfully accessed default Nginx landing page

---

# Firewall Configuration

Allowed HTTP traffic through UFW firewall:

```bash
sudo ufw allow 80/tcp
```

Verified firewall rules:

```bash
sudo ufw status
```

Purpose:
- Allow inbound web traffic
- Permit browser access to hosted content

---

# Creating a Custom Web Page

Edited default Nginx web root:

```bash
sudo nano /var/www/html/index.nginx-debian.html
```

Example custom HTML:

```html
<h1>Ubuntu Server Homelab</h1>
<p>Nginx is running successfully.</p>
```

Saved changes and refreshed browser to verify updates.

---

# Service Management

Restarted Nginx after configuration changes:

```bash
sudo systemctl restart nginx
```

Checked service health:

```bash
sudo systemctl status nginx
```

---

# Troubleshooting

## Issue
Could not access the web page from another device.

## Cause
HTTP traffic was blocked by firewall.

## Resolution

```bash
sudo ufw allow 80/tcp
```

Successfully restored web access.

---

# Lessons Learned

- Learned how to install and manage Linux web services
- Practiced service management using systemctl
- Improved understanding of HTTP traffic and port 80
- Learned how firewall rules affect hosted services
- Practiced testing connectivity locally and remotely

---

# Future Improvements

Planned future upgrades:
- Configure HTTPS with SSL/TLS
- Host multiple websites with virtual hosts
- Add custom domain name
- Implement Fail2Ban for security
- Deploy containerized applications using Docker
