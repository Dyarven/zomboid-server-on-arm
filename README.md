# 🧟‍♂️ Zomboid Server on ARM

[![Star this repo](https://img.shields.io/github/stars/Dyarven/zomboid-server-on-arm?style=social)](https://github.com/Dyarven/zomboid-server-on-arm/stargazers)
[![Follow me](https://img.shields.io/github/followers/Dyarven?style=social)](https://github.com/Dyarven)
[![License](https://img.shields.io/github/license/Dyarven/zomboid-server-on-arm)](https://github.com/Dyarven/zomboid-server-on-arm/blob/main/LICENSE)

A bash script to ease the set up of a **Project Zomboid server** on ARM64 devices like Raspberry Pi or OCI Ampere Arm-based cloud instances using an emulation layer.

---

## Features
- **Automated Setup:** Installs everything you need for a functioning Zomboid server set up as a systemd service.
- **ARM64 Compatible:** Configures an emulation layer with Box86 and Box64 for both SteamCMD and Zomboid x86/64 binaries.
- **Version Selection:** You can specify the release of Project Zomboid you want to install (including beta branches).

## Important things to know
- The first time you run the server it must be manually launching it from start-server.sh.
- It will create the necessary files and folders and ask you to set up an admin password to access the server. _-> You could theoretically automate this by setting a custom servername and providing an ini file, but since this is a PoC and often unstable, I'd rather not skip this manual step._
- After that you can just shut it down and run it like a systemd service. 
- Default server takes 8GB of RAM.
- This script opens ports 16261 and 16262 UDP on your firewall but you still need to forward them in the oracle cloud console for your vm instance.
- Notice we are using /opt/zomboid-server as a dir but zomboid's starting script will generate files in the homedir of the user. Files will be split in two directories but are accessible through 
  symlinks from a single place to easily set startup parameters.
- I recommend using tmux or screen during the process if you're on a single SSH session.

## Setup guide

### 1. Clone the Repository
```bash
git clone https://github.com/Dyarven/Zomboid-Server-on-ARM.git
cd Zomboid-Server-on-ARM
```
### 2. Run the Script
```bash
chmod +x arm64_zomboid_server
bash arm64_zomboid_server
```
### 3. When the script promtps you to, on another terminal run the server for the first time and set a password. When finished, shut it down.
```bash
cd /opt/zomboid-server && sh start-server
```
### 4. Go back to the first terminal and finish running my script.

### 5. Done! The server should automatically start as a systemd service.


