# Navidrome Android (Termux) Setup Guide

This guide summarizes how to run a Navidrome music server on an old Android phone using Termux.

## 1. Initial Setup
Install **Termux** (from F-Droid) and run these commands to prepare the environment:
```bash
termux-setup-storage
pkg update && pkg upgrade -y
pkg install wget ffmpeg proot openssh -y
```

## 2. Install Navidrome
```bash
mkdir -p ~/navidrome-server
cd ~/navidrome-server
wget https://github.com/navidrome/navidrome/releases/download/v0.59.0/navidrome_0.59.0_Linux_arm64.tar.gz
tar -xvzf navidrome_0.59.0_Linux_arm64.tar.gz
```

## 3. Configuration
Create the `navidrome.toml` file to point to your music:
```bash
cat <<EOF > navidrome.toml
MusicFolder = "/data/data/com.termux/files/home/storage/music"
DataFolder = "./data"
LogLevel = "info"
Port = 4533
EOF
```

## 4. How to Start the Server
Because of Android security (Seccomp), you must use `proot` to run the binary:
```bash
cd ~/navidrome-server
proot -0 ./navidrome
```
*Keep this session running.*

## 5. Access via Local Network
Open your browser and go to:
- **On the same phone:** `http://localhost:4533`
- **On another device:** `http://<YOUR_PHONE_IP>:4533` (Find IP by running `ifconfig`)

## 6. Access via Internet (Tunnel)
Open a **New Session** in Termux and run:
```bash
ssh -R 80:localhost:4533 serveo.net
```
*This will give you a unique `https://...serveousercontent.com` link.*

---
**Important Security Note:** Since your server is public via the tunnel, ensure you set a **strong password** for your Navidrome admin account.
