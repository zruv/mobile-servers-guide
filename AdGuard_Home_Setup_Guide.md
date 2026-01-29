# AdGuard Home Android (Termux) Setup Guide

This guide explains how to run AdGuard Home on an Android phone using Termux.

## 1. Initial Setup
Install **Termux** (from F-Droid) and update packages:
```bash
pkg update && pkg upgrade -y
pkg install wget tar nano -y
```

## 2. Install AdGuard Home
```bash
mkdir -p ~/adguard-home
cd ~/adguard-home
wget https://github.com/AdguardTeam/AdGuardHome/releases/latest/download/AdGuardHome_linux_arm64.tar.gz
tar -xvzf AdGuardHome_linux_arm64.tar.gz
cd AdGuardHome
```

## 3. Configuration (Fixing Android Crashes)
Android prevents non-root apps from using standard ports and accessing system tables (ARP/DHCP), which causes AdGuard Home to crash. You **must** create a configuration file manually before the first run.

Create the file:
```bash
nano AdGuardHome.yaml
```

Paste this "Safe Mode" configuration:
```yaml
bind_host: 0.0.0.0
bind_port: 8080
auth_attempts: 5
block_auth_min: 15
http_proxy_port: 0
language: en
theme: auto
debug_pprof: false
web_session_ttl: 720
dns:
  bind_hosts:
  - 0.0.0.0
  port: 5553
  resolve_clients: false 
clients:
  runtime_sources:
    arp: false
    dhcp: false
    hosts: true
    rdns: false
    whois: false
os:
  user: ""
  group: ""
schema_version: 32
```
*Press `Ctrl+O`, `Enter`, then `Ctrl+X` to save and exit.*

## 4. How to Start the Server
Run the binary with the work-dir flag:
```bash
./AdGuardHome --no-check-update --work-dir .
```

## 5. Web Dashboard Access
1. Open your browser on any device on the same Wi-Fi.
2. Go to: `http://<YOUR_PHONE_IP>:8080`
3. Since we skipped the setup wizard, there is no password. **Go to Settings -> Change Password immediately** to secure your dashboard.

## 6. Using It on Your Network
- **Admin Panel:** `http://<YOUR_PHONE_IP>:8080`
- **DNS Port:** `5553`

### Client Setup (Android/PC)
Since Android blocks Port 53, you must use an app that supports custom DNS ports (like **Nebulo** or **Personal DNS Filter** on Android) or configure your device to use the IP and Port 5553.