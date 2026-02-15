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
- Ideally you'd create a **"zomboid"** user and run the script/service as that user.
- The first time you run the actual zomboid server must be manually launching it with `start-server.sh`. Once you launch my setup script and it reaches that point, it will tell you to do so. 
  - `start_server.sh` will eventually ask you to set up an admin password to access the server. _-> You could theoretically automate this by setting a custom servername and providing an ini file, but since this is a PoC and often unstable, I'd rather not skip this manual step._
  - When that is done, you can just shut the zomboid server down, continue running my script and once its finished, zomboid will start automatically as a systemd service.
- This script opens ports 16261 and 16262 UDP on your firewall but you still need to forward them in the oracle cloud console for your vm instance.


## Setup guide step by step

### 1. Clone the Repository
```bash
git clone https://github.com/Dyarven/Zomboid-Server-on-ARM.git
cd Zomboid-Server-on-ARM
```
### 2. Run the Script
```bash
chmod +x arm64_zomboid_server
sudo bash arm64_zomboid_server
```
### 3. When the script promtps you to, on another terminal (don't close this one), run the server for the first time and set a password. When finished, shut it down and check that you correctly kill the process.
```bash
cd /opt/zomboid-server && sh start-server.sh
```
### 4. Go back to the first terminal and finish running the script.

### 5. Done! The server should automatically start as a systemd service. You can validate and check the logs with:
```bash
systemctl status zomboid-server
journalctl -xeu zomboid-server --follow
```


