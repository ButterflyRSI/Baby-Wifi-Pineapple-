# GL.iNet WiFi Pentesting Platform

A complete, affordable WiFi pentesting platform using GL.iNet router, automated capture scripts, real-time web dashboard, and GPU-accelerated password cracking.

![Platform Overview](docs/images/dashboard.png)

## 🎯 Features

- **Autonomous WiFi Handshake Capture** - Deploy and forget, automatically captures WPA2 handshakes
- **Real-Time Web Dashboard** - Monitor operations from any device
- **GPU-Accelerated Cracking** - Leverage RTX 3060 for fast password recovery
- **Dual-Band Support** - 2.4GHz and 5GHz attacks (with PAU0D adapter)
- **Remote Access** - WireGuard VPN for deployed operations
- **Complete Automation** - One-click installation and deployment

## 💰 Cost Breakdown

| Component | Price | Purpose |
|-----------|-------|---------|
| GL.iNet GL-AR300M16-Ext | $40 | Attack platform |
| Panda PAU0D WiFi Adapter | $40 | Dual-band attacks |
| MicroSD Card (64GB) | $10 | Capture storage |
| Power Bank (10000mAh) | $20 | Portable power |
| **Total** | **~$110** | vs $200+ Pineapple |

## 🚀 Quick Start

### Prerequisites

**Hardware:**
- GL.iNet GL-AR300M16-Ext router
- MicroSD card (32GB+ recommended)
- Panda PAU0D USB WiFi adapter (optional but recommended)
- USB power bank for portable deployment

**Desktop (for cracking):**
- NVIDIA GPU (recommended: RTX 3050+)
- Hashcat installed
- Windows 10/11 or Linux

### Installation

1. **Clone repository:**
```bash
git clone https://github.com/yourusername/glinet-pentesting-platform.git
cd glinet-pentesting-platform
```

2. **Connect to GL.iNet:**
   - Connect to GL.iNet WiFi (SSID: GL-AR300M-XXX, Password: goodlife)
   - Router IP: 192.168.8.1

3. **Run installer:**
```bash
chmod +x install_all.sh
./install_all.sh
```

4. **Access dashboard:**
   - Open browser: http://192.168.8.1:8080

## 📖 Documentation

- [Installation Guide](docs/INSTALLATION.md)
- [Usage Guide](docs/USAGE.md)
- [Troubleshooting](docs/TROUBLESHOOTING.md)
- [Hardware Setup](docs/HARDWARE.md)
- [Legal Information](docs/LEGAL.md)

## 🎮 Usage Examples

### Autonomous Drop Box Deployment
```bash
# SSH into router
ssh root@192.168.8.1

# Start drop box
/root/scripts/dropbox_deploy.sh start wlan0

# Deploy at target location
# Returns in 8 hours to retrieve captures
```

### Manual Handshake Capture
```bash
# Scan for networks
/root/scripts/autoscan.sh wlan0

# Capture specific network
/root/scripts/capture.sh AA:BB:CC:DD:EE:FF 6 wlan0

# Transfer to desktop and crack
scp root@192.168.8.1:/mnt/sd/dropbox/captures/*.hc22000 ~/captures/
hashcat -m 22000 capture.hc22000 rockyou.txt -d 1
```

### Desktop Cracking Workflow
```powershell
# Windows - automated workflow
.\desktop\crack_workflow.ps1

# Downloads captures, cracks with GPU, uploads results
```

## 🏗️ Architecture
```
┌─────────────────────────────────────┐
│  GL.iNet Router (Attack Platform)  │
│  ├── Drop Box Script                │
│  ├── Web Dashboard                  │
│  ├── PAU0D Adapter (dual-band)      │
│  └── Autonomous Capture             │
└──────────────┬──────────────────────┘
               │ WiFi/VPN
               ▼
┌─────────────────────────────────────┐
│  Desktop (Cracking Station)         │
│  ├── RTX 3060 12GB                  │
│  ├── Hashcat                        │
│  └── Automated Workflow             │
└─────────────────────────────────────┘
```

## 🛠️ Components

### Router Scripts

- **autoscan.sh** - Automated network scanning
- **capture.sh** - Handshake capture with deauth
- **deauth.sh** - Targeted deauthentication
- **monitor.sh** - Monitor mode management
- **status.sh** - System status check
- **dropbox_deploy.sh** - Autonomous deployment
- **dropbox_config.sh** - Remote transfer configuration

### Web Dashboard

- Real-time monitoring
- System statistics
- Capture management
- File downloads
- Drop box control

### Desktop Tools

- **crack_workflow.ps1** - Automated cracking workflow
- GPU-accelerated password recovery
- Results management
- Auto-transfer integration

## ⚖️ Legal Disclaimer

**THIS TOOL IS FOR EDUCATIONAL AND AUTHORIZED TESTING ONLY.**

- Only use on networks you own
- Or with explicit written permission
- Unauthorized access is illegal
- Know your local laws
- You are responsible for your actions

See [LEGAL.md](docs/LEGAL.md) for detailed information.

## 🤝 Contributing

Contributions welcome! Please read [CONTRIBUTING.md](CONTRIBUTING.md) first.

## 📜 License

MIT License - See [LICENSE](LICENSE) for details.

## 🙏 Credits

- Built for the 2600 community
- Inspired by WiFi Pineapple
- Powered by Aircrack-ng, Hashcat, and Flask

## 📧 Contact

- GitHub Issues: [Project Issues](https://github.com/yourusername/glinet-pentesting-platform/issues)
- 2600 Meetings: First Friday, 30th Street Station, Philadelphia

---

**Remember:** With great power comes great responsibility. Use ethically. ✌️
