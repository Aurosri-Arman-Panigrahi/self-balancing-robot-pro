# 🤖 Self Balancing Robot Pro

**Web Bluetooth Controller for BalanceBot_Pro** — Control your self-balancing robot directly from your browser using the Web Bluetooth API.

![Dark Mode UI](https://img.shields.io/badge/theme-dark%20mode-0a0e17?style=flat-square&labelColor=111827&color=00d4ff)
![Web Bluetooth](https://img.shields.io/badge/bluetooth-Web%20BLE-00d4ff?style=flat-square)
![Status](https://img.shields.io/badge/status-active-22d65e?style=flat-square)

---

## ✨ Features

| Feature | Description |
|---------|-------------|
| **📡 Bluetooth Connect** | Pair with HC-05/HM-10 module via Web Bluetooth API |
| **🕹️ Virtual Joystick** | NippleJS-powered joystick, sends motor commands at 20 Hz |
| **⚙️ PID Tuning** | Real-time Kp (0–100), Ki (0–100), Kd (0–10) sliders + manual input |
| **🤖 Arm/Disarm** | Start/Stop robot with one click |
| **📟 Command Console** | Live, color-coded log of all sent Bluetooth commands |
| **🌙 Dark Mode UI** | Neon-blue accents, Orbitron font, animated glows |

## 🚀 Getting Started

### Prerequisites
- **Browser**: Chrome, Edge, or Opera (Web Bluetooth required)
- **Bluetooth Module**: HC-05 (BLE mode) or HM-10 on your robot
- **Serving**: Page must be served over HTTPS or `localhost`

### Quick Start

1. **Clone the repository**
   ```bash
   git clone https://github.com/Aurosri-Arman-Panigrahi/self-balancing-robot-pro.git
   cd self-balancing-robot-pro
   ```

2. **Serve locally** (any static server)
   ```bash
   npx http-server . -p 8080
   ```

3. **Open in browser**
   ```
   http://localhost:8080/website.html
   ```

4. **Connect & drive!**
   - Click **Connect** → select your Bluetooth module
   - Click **▶ Start** to arm the robot
   - Use the **joystick** to control movement
   - Adjust **PID values** via sliders or type manually

## 📡 Communication Protocol

| Command | Format | Example | Description |
|---------|--------|---------|-------------|
| Forward | `FxxRxx` | `F50R50` | Forward at 50% both motors |
| Backward | `BxxRxx` | `B30R30` | Backward at 30% |
| Stop | `S00000` | `S00000` | All motors stop |
| Arm | `START` | `START` | Arm robot |
| Disarm | `STOP0` | `STOP0` | Disarm robot |
| PID | `Pkp,ki,kd` | `P15.0,1.0,0.50` | Set PID values |

Commands are sent as 6-character strings at **50ms intervals** (20 Hz) while the joystick is active. Releasing the joystick immediately sends `S00000`.

## 🎨 Tech Stack

- **HTML5 / CSS3 / Vanilla JavaScript** — Single-file, zero build step
- **[NippleJS](https://yoannmoi.net/nipplejs/)** — Virtual joystick library
- **Web Bluetooth API** — Direct browser-to-device BLE communication
- **Google Fonts** — Orbitron (display) + Inter (body)

## ⚠️ Browser Compatibility

| Browser | Supported |
|---------|-----------|
| Chrome | ✅ |
| Edge | ✅ |
| Opera | ✅ |
| Firefox | ❌ |
| Safari | ❌ |

## 📁 Project Structure

```
self-balancing-robot-pro/
├── website.html    # Complete single-file web application
└── README.md       # This file
```

## 🔧 PID Tuning Guide

| Parameter | Range | Step | Description |
|-----------|-------|------|-------------|
| **Kp** (Proportional) | 0 – 100 | 0.1 | Controls response to current error |
| **Ki** (Integral) | 0 – 100 | 0.1 | Eliminates steady-state error |
| **Kd** (Derivative) | 0 – 10 | 0.01 | Dampens oscillations |

> **Tip:** Start with Kp ≈ 15, Ki ≈ 1, Kd ≈ 0.5 and adjust incrementally.

---

## 📜 License

This project is part of the **Kalinga Project**.

Made with ⚡ by [Aurosri Arman Panigrahi](https://github.com/Aurosri-Arman-Panigrahi)
