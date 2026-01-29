# Termux SSH Setup Guide

Follow these steps to access your Termux terminal from your Zorin OS laptop.

## Prerequisites
- Both devices must be connected to the same Wi-Fi network.

## 1. On your Phone (Termux)

Update packages and install OpenSSH:
```bash
pkg update && pkg upgrade
pkg install openssh
```

Set a password for your Termux user:
```bash
passwd
```

Start the SSH server:
```bash
sshd
```

Find your username:
```bash
whoami
```

Find your phone's IP address (look for the IP under `wlan0`):
```bash
ifconfig
```

## 2. On your Laptop (Zorin OS)

Open your terminal and connect using the default Termux SSH port (8022):
```bash
ssh -p 8022 <username>@<ip_address_of_phone>
```

## 3. Stopping the SSH Server (On Termux)

If you want to stop the SSH server, run:
```bash
pkill sshd
```

---
**Note:** The `sshd` server in Termux stops if the app is closed or the phone reboots. You may need to run `sshd` again to reconnect.