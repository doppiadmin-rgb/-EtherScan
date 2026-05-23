<div align="center">

<img src="https://i.postimg.cc/TPZs1v9B/photo-2026-05-23-21-49-59.jpg" width="0">

# ⬡ EtherScan
### WiFi CSI Spatial Intelligence V2.0

**See Wi-Fi. Understand Space.**

Real-time Wi-Fi CSI visualization for human presence detection, vital signs monitoring, and spatial intelligence — without cameras or wearables.

[![Live Demo](https://img.shields.io/badge/LIVE-Demo-00d878?style=for-the-badge&logo=google-chrome&logoColor=white)](https://github.com/doppiadmin-rgb/-EtherScan)
[![License](https://img.shields.io/badge/License-MIT-blue?style=for-the-badge)](LICENSE)
[![Version](https://img.shields.io/badge/Version-2.0-378ADD?style=for-the-badge)](https://github.com/doppiadmin-rgb/-EtherScan)
[![WiFi CSI](https://img.shields.io/badge/WiFi-CSI_Sensing-ff4060?style=for-the-badge&logo=wifi&logoColor=white)](https://github.com/doppiadmin-rgb/-EtherScan)

</div>

---

![EtherScan Screenshot](https://i.postimg.cc/TPZs1v9B/photo-2026-05-23-21-49-59.jpg)

> *Advanced life signal detection based on Wi-Fi micro-movements. No cameras. No wearables. Just physics.*

---

## ✨ What is EtherScan?

EtherScan turns ordinary WiFi signals into a real-time spatial intelligence system. When people move, breathe, or even sit still — they disturb WiFi radio waves in measurable ways. EtherScan captures these disturbances using **Channel State Information (CSI)** and visualizes them as a cinematic 3D holographic experience.

---

## 🚀 Features

| Feature | Description |
|---|---|
| ❤️ **Vital Signs Monitoring** | Real-time heart rate (BPM) and breathing rate (RPM) detection |
| 🧍 **Human Pose Estimation** | 3D wireframe body visualization from WiFi signals |
| 📡 **Presence Detection** | Instant detection of human presence in a room |
| 📊 **CSI Subcarrier Analysis** | Deep signal analysis across 64+ subcarriers |
| 🚨 **Fall Detection Alarm** | Automatic audio alert when fall or lying detected |
| 🌐 **Live WebSocket Mode** | Connect to real sensing server for live data |
| 🎬 **12+ Demo Scenarios** | Breathing, walking, sleeping, intrusion and more |
| 🎨 **3D Holographic UI** | Cinematic Three.js visualization with bloom effects |

---

## 📸 Screenshots

<div align="center">
<table>
<tr>
<td><b>Main Dashboard</b></td>
<td><b>Live Spatial View</b></td>
</tr>
<tr>
<td><img src="https://i.postimg.cc/7P1RHc2r/photo-2026-05-23-21-50-05.jpg" width="400"></td>
<td><img src="https://i.postimg.cc/cJjp3nx4/photo-2026-05-23-21-48-27.jpg" width="400"></td>
</tr>
</table>
</div>

---

## 🛠️ Quick Start

### Option 1 — Demo Mode (No hardware needed)

```bash
# Clone the repo
git clone https://github.com/doppiadmin-rgb/-EtherScan.git
cd -EtherScan/EtherScan_modified

# Start local server
python -m http.server 8080

# Open in browser
# http://localhost:8080
```

### Option 2 — Live Mode (Docker)

```bash
# Pull and run the sensing server
docker run -p 3000:3000 -p 3001:3001 \
  -e CSI_SOURCE=simulate \
  ruvnet/wifi-densepose:latest

# Open in browser
# http://localhost:3000
```

The HUD badge will switch from **DEMO** → **🟢 LIVE** automatically.

### Option 3 — Real Hardware (ESP32-S3)

```bash
docker run -p 3000:3000 -p 3001:3001 -p 5005:5005/udp \
  -e CSI_SOURCE=esp32 \
  ruvnet/wifi-densepose:latest
```

> Requires **ESP32-S3-DevKitC-1** flashed with CSI firmware. See [Hardware Setup](#hardware).

---

## 🏗️ Project Structure

```
EtherScan_modified/
├── index.html                    # Main entry point
├── fire-alarm.mp3                # Fall detection alarm sound
└── observatory/
    ├── css/
    │   └── observatory.css       # All styles + dark theme
    └── js/
        ├── main.js               # App entry, Three.js init
        ├── demo-data.js          # 12 scenario data generator
        ├── hud-controller.js     # HUD panels, vitals display
        ├── pose-system.js        # 3D human wireframe rendering
        ├── vitals-oracle.js      # Heart rate & breathing detection
        ├── presence-cartography.js # Presence heatmap
        ├── figure-pool.js        # Multi-person figure management
        ├── convergence-engine.js # Signal convergence visualization
        ├── subcarrier-manifold.js # CSI subcarrier 3D surface
        ├── phase-constellation.js # I/Q phase star map
        ├── scenario-props.js     # Room props & scene objects
        └── nebula-background.js  # Particle background
```

---

## 📡 Demo Scenarios

EtherScan includes 12 built-in sensing scenarios:

| Scenario | Description |
|---|---|
| 🏠 Empty Room | Baseline calibration, no presence |
| 💓 Vital Signs | Breathing ~15 RPM, heart rate ~73 BPM |
| 👥 Multi-Person | Two people tracked simultaneously |
| 🚨 Fall Detection | Sudden posture change with **alarm** |
| 😴 Sleep Monitor | Breathing patterns and apnea detection |
| 🔒 Intrusion | Passive perimeter monitoring |
| 👋 Gesture Control | DTW gesture recognition |
| 👴 Elderly Care | Gait analysis for mobility detection |
| 🏋️ Fitness | Rep counting and exercise classification |
| 🔍 Search & Rescue | Through-wall survivor detection |
| 👮 Security Patrol | Multi-zone presence monitoring |
| 🏢 Crowd Occupancy | Room occupancy estimation |

---

## ⚙️ Settings

Press `[S]` or click the gear icon to access:

- **Rendering** — Bloom, exposure, vignette, film grain
- **Wireframe** — Bone thickness, joint size, glow intensity
- **Scene** — WiFi waves, room brightness, FOV
- **Data** — Scenarios, cycle speed, WebSocket URL

**Style Presets:** Foundation · Cinematic · Minimal · Neon · Tactical · Medical

---

## 🔧 Hardware Setup <a name="hardware"></a>

For real WiFi CSI sensing you need:

| Hardware | Cost | Notes |
|---|---|---|
| **ESP32-S3-DevKitC-1** | ~$9 | Required. ESP32-C3/original not supported |
| ESP32-S3 WROOM (8MB) | ~$10 | Alternative with OTA support |

```
ESP32-S3 Node          Host Machine (your PC)
+──────────────+  UDP  +──────────────────────+
│ WiFi CSI     │──────▶│ sensing-server       │
│ 20 Hz stream │ :5005 │ REST API  :3000      │
│ 64 subcarriers│      │ WebSocket :3000      │
+──────────────+       │ EtherScan UI         │
                       +──────────────────────+
```

---

## 🎮 Keyboard Shortcuts

| Key | Action |
|---|---|
| `A` | Toggle orbit camera |
| `D` | Next scenario |
| `F` | Show FPS counter |
| `S` | Open settings |
| `Space` | Pause / Resume |

---

## 🚨 Fall Detection Alert

When a person is detected falling or lying down:
- 🔴 Full-screen red alert overlay appears
- 🔊 Audio alarm plays (fire-alarm.mp3)
- ✓ Confirm button to dismiss

---

<div align="center">

**Built with ❤️ by [doppiadmin-rgb](https://github.com/doppiadmin-rgb)**

⬡ EtherScan — See the invisible. Understand the space.

</div>
