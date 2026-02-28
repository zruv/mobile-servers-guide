# Shizuku Setup Guide (Android 11+ Non-Rooted)

This guide explains how to enable Shizuku on Android 11 and above without root access using Wireless Debugging.

## Prerequisites
* Device running Android 11 or higher.
* Connection to a Wi-Fi network (or a hotspot from another device).
* Shizuku app installed from the [Play Store](https://play.google.com/store/apps/details?id=moe.shizuku.privileged.api).

## Step 1: Enable Developer Options
1. Go to **Settings > About Phone**.
2. Tap **Build Number** 7 times until you see "You are now a developer!".
3. Go to **Settings > System > Developer Options**.

## Step 2: Enable Wireless Debugging
1. In **Developer Options**, scroll down to **Wireless debugging**.
2. Toggle it **ON**. 
3. Check "Always allow on this network" and tap **Allow**.
4. **Tap the text** "Wireless debugging" to enter its detailed menu.

## Step 3: Pairing with Shizuku
1. Open the **Shizuku app**.
2. Tap **Pairing** in the "Start via Wireless Debugging" section.
3. Tap **Developer options** (this takes you back to settings).
4. In the **Wireless debugging** menu, tap **Pair device with pairing code**.
5. A 6-digit code will appear. 
6. Pull down your notification bar and enter the code into the **Shizuku notification**.
7. It should say "Pairing successful".

## Step 4: Starting the Service
1. Return to the **Shizuku app**.
2. Tap **Start** (under the Wireless Debugging section).
3. Wait for the terminal output to finish.
4. The status at the top should now say **"Shizuku is running"**.

## Step 5: Termux Integration (Optional)
To use Shizuku inside Termux:
1. In Shizuku, tap **Authorized applications** and enable **Termux**.
2. In Shizuku's main screen, tap **"Use Shizuku in terminal (e.g., Termux)"** and tap **"Export files"**. Save them to your internal storage (e.g., the Downloads folder).
3. In Termux, run:
   ```bash
   termux-setup-storage
   # (Grant permission if prompted)
   
   mkdir -p ~/.shizuku
   cp ~/storage/downloads/rish* ~/.shizuku/
   chmod +x ~/.shizuku/rish
   cp ~/.shizuku/rish* $PREFIX/bin/
   ```
4. Type `rish` to enter the ADB shell.

---
**Note:** If you reboot your phone, you must repeat **Step 4** to start the service again.
