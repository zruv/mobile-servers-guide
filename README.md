# Mobile Servers

This repository contains setup guides for running various self-hosted services on Android devices using [Termux](https://termux.dev/en/). Ideally suited for repurposing old smartphones into functional low-power servers.

## Prerequisites

- An Android device (Root is **not** required for these guides).
- **Termux** installed (preferably from [F-Droid](https://f-droid.org/en/packages/com.termux/)).
- Basic knowledge of the command line.

## Available Guides

### 1. [Navidrome Music Server](./Navidrome_Setup_Guide.md)
Turn your phone into a personal music streaming server.
- **Features:** Self-hosted music streaming, web UI, mobile app support.
- **Key steps:** Install ffmpeg, configure `navidrome.toml`, run via `proot`.

### 2. [AdGuard Home DNS Blocker](./AdGuard_Home_Setup_Guide.md)
Run network-wide ad and tracker blocking directly from your phone.
- **Features:** DNS filtering, parental control, safe browsing.
- **Key steps:** Custom "Safe Mode" config to avoid Android port/permission crashes.

### 3. [Termux SSH Access](./Termux_SSH_Setup_Guide.md)
Manage your mobile server remotely from your PC.
- **Features:** Remote terminal access, easier management.
- **Key steps:** Install OpenSSH, set password, connect via port 8022.

## Disclaimer

Running services on mobile devices may drain battery quickly. It is recommended to keep the device plugged in. Some services are configured on non-standard ports to function without root privileges.
