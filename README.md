<div align="center">

```
Shaon
```

**My Project v2.0** — WPS Security Auditing Tool for Android / Termux


## Overview

My Project is a WPS (Wi-Fi Protected Setup) security auditing tool built for Android devices running Termux. It automates Pixie Dust and Bruteforce attacks against WPS-enabled routers, allowing security researchers and network administrators to evaluate the strength of their own wireless infrastructure.

WiFuX v2.0 is a complete rewrite of the original v1 engine, introducing a global command system, session management, reporting, improved stability, and a built-in interactive help guide — all optimized for Android / Termux.

> This tool is intended for authorized security testing only. Only use it on networks you own or have explicit permission to test.

---
<div align="center">
 
## Requirements

- Android device with root access (Magisk or KernelSU)
- [Termux](https://f-droid.org/en/packages/com.termux/) installed (from fdroid. not from playstore)
- Root-capable WiFi adapter (internal wlan0 or external)

---

## Installation

WiFuX v2.0 installs globally. Once set up, you can run it from any directory using the `wifux` command.

### Method 1 — One Command (Recommended)

```bash
curl -sLo installer.sh https://raw.githubusercontent.com/arifuzzamanshaon/shaon/main/installer.sh && bash installer.sh
```

This will automatically update packages, install all dependencies, clone the repository, and register the `my project` global command.

### Method 2 — Manual

```bash
pkg update && pkg upgrade -y
pkg install root-repo git tsu python wpa-supplicant pixiewps iw -y
git clone https://github.com/arifuzzamanshaon/shaon
cd shaon
chmod +x installer.sh
bash installer.sh
```
---

## Commands

| Command | Description |
|---|---|
| `wifux` | Run WiFuX with default settings (wlan0 + Pixie Dust) |
| `wifux menu` | Open WiFuX interactive menu without auto-attack |
| `wifux old` | Run the legacy engine (w1.py) with wlan0 |
| `wifux update` | Pull latest updates from GitHub |
| `wifux help` | Open the built-in interactive help guide |
| `wifux fix` | Fix root / superuser issues |
| `wifux contact` | Contact the developer |

---

## Usage

**Default run — scan nearby networks and attack:**
```bash
wifux
```

**Pixie Dust on a specific router:**
```bash
wifux -i wlan0 -b <BSSID> -K
```

**Bruteforce on a specific router:**
```bash
wifux -i wlan0 -b <BSSID> -B
```
**Pixie Dust without touching Android WiFi settings:**
```bash
wifux -i wlan0 -K --dts
```
**Resume a previous session:**
```bash
wifux --list-sessions
wifux -i wlan0 --resume-session <BSSID>
```
**Generate an HTML report:**
```bash
wifux -i wlan0 -b <BSSID> -K --html-report
```
For the full argument reference, run `wifux help` and select option 5.
---
## Troubleshooting
**"No superuser binary detected"**
Run the built-in fix first:
```bash
wifux fix
```
If the issue persists, use the dedicated fix script:
```bash
```
---
**Common issues and fixes**
| Problem | Fix |
|---|---|
| "Run it as root" error | Run `su` first, then retry |
| "Unable to up interface" | Check interface name with `ip link show` |
| wpa_supplicant crash | Run `pkill wpa_supplicant`, then retry |
| No WPS networks found | Disable Location/GPS, toggle WiFi off and on |
| Router keeps locking | Add `-d 3` delay or use `--lock-delay 120` |
| WiFi rfkill blocked | Use `--handle-rfkill` or run `rfkill unblock wifi` |
| Pixie Dust not working | Router may not be vulnerable — switch to Bruteforce (`-B`) |
---
## Changelog

See [CHANGELOG.md](CHANGELOG.md) for a full list of changes between versions.
---
## Disclaimer

WiFuX is provided for educational and authorized penetration testing purposes only. You are solely responsible for ensuring you have permission to test any network. The author is not liable for any misuse, damage, or legal consequences resulting from the use of this tool.

---

## Author
**Arifuzzaman Shaon**

| Platform | Link |
|---|---|
| GitHub | [msrofficial](https://github.com/arifuzzamanshaon) |
| Facebook | [sakibur.msr](https://facebook.com/thearifuzzamanshaon) |
| Instagram | [msr.sakibur](https://instagram.com/arifuzzamanshaon) |
---
<div align="center">
If WiFuX has been useful, consider leaving a star on GitHub.<br>
It helps the project grow and encourages further development.
</div>
