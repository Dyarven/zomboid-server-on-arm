# 🧟‍♂️ Zomboid Server on ARM

[![Star this repo](https://img.shields.io/github/stars/Dyarven/Zomboid-Server-on-ARM?style=social)](https://github.com/Dyarven/Zomboid-Server-on-ARM/stargazers)
[![Follow me](https://img.shields.io/github/followers/Dyarven?style=social)](https://github.com/Dyarven)
[![License](https://img.shields.io/github/license/Dyarven/Zomboid-Server-on-ARM)](https://github.com/Dyarven/Zomboid-Server-on-ARM/blob/main/LICENSE)

A bash script to ease the set up of a **Project Zomboid server** on ARM64 devices like Raspberry Pi. or OCI Ampere Arm-based cloud instances.🎮

---

## 🛠 Features
- **Automated Setup:** Installs everything you need for a functioning Zomboid server.
- **ARM64 Compatible:** Specifically designed for ARM-based platforms.
- **Lightweight & Efficient:** Ensures minimal resource usage for smooth performance.

## ⚠️ Important
- The first time you run the server it must be manually launching it from start-server.sh.
- It will create the necessary files and folders and ask you to set up an admin password to access the server.
- After that you can just shut it down and use "systemctl enable zomboid-server" and "systemctl start zomboid-server" to run it. 
- Default server takes 8GB of RAM.
- This script asumes you opened ports 16261 and 16262 tcp/udp on your firewall and forwarded them in the oracle cloud console for your vm instance.
- Notice we are using /opt/zomboid-server as a dir but zomboid's starting script will generate files in the homedir of the user. Files will be split in two directories but are accessible through 
  symlinks from a single place. 
  set startup parameters.

## 🚀 Quick Start

### Clone the Repository
```bash
git clone https://github.com/Dyarven/Zomboid-Server-on-ARM.git
cd Zomboid-Server-on-ARM
```
### Run the Script
```bash
chmod +x arm64_zomboid_server.sh
./arm64_zomboid_server.sh
```


