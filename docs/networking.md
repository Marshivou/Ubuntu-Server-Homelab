# Networking Configuration

## Objective

Configure and verify network connectivity for the Ubuntu Server virtual machine.

---

# Network Adapter Configuration

VirtualBox Network Mode:
- Bridged Adapter

Reason:
Bridged mode allows the Ubuntu Server VM to appear as a separate device on the local network, enabling communication with other devices.

---

# IP Configuration

Checked interface configuration using:

```bash
ip a
```

Example output:

```text
inet 192.168.1.115/24
```

Network Details:
- IP Address: 192.168.1.115
- Subnet Mask: /24
- Default Gateway: 192.168.1.1

---

# Routing Table

Verified routing information using:

```bash
ip route
```

Example:

```text
default via 192.168.1.1 dev enp0s3
```

Purpose:
- Confirmed default gateway configuration
- Verified outbound traffic path

---

# Connectivity Testing

## Ping Test

Tested internet connectivity:

```bash
ping google.com
```

Purpose:
- Verify internet access
- Verify DNS resolution

Results:
- Successful replies received
- No packet loss observed

---

# DNS Verification

Verified DNS functionality using:

```bash
nslookup google.com
```

Purpose:
- Confirm DNS server functionality
- Ensure hostname resolution works properly

---

# Remote Access Testing

Verified SSH connectivity from Windows host machine.

Command used from Windows PowerShell:

```powershell
ssh username@192.168.1.115
```

Result:
- Successful remote login established

---

# Firewall Networking Rules

Allowed SSH traffic:

```bash
sudo ufw allow ssh
```

Allowed HTTP traffic:

```bash
sudo ufw allow 80/tcp
```

Verified firewall status:

```bash
sudo ufw status
```

---

# Troubleshooting

## Issue
Unable to access server remotely.

## Cause
Firewall rule for SSH was not enabled.

## Resolution

```bash
sudo ufw allow ssh
```

Successfully restored SSH connectivity.

---

# Lessons Learned

- Learned how bridged networking works
- Improved understanding of IP addressing and gateways
- Practiced network troubleshooting
- Learned how firewall rules affect connectivity
- Practiced remote administration using SSH
