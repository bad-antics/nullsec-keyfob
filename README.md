<div align="center">

# 🔑 NullSec KeyFob

### Automotive Key Fob & Immobilizer Security Research

[![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white)]()
[![C](https://img.shields.io/badge/C-RF_Analysis-A8B9CC?style=for-the-badge&logo=c&logoColor=black)]()
[![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)]()
[![NullSec](https://img.shields.io/badge/NullSec-Linux_v5.0-00ff41?style=for-the-badge&logo=linux&logoColor=white)](https://github.com/bad-antics/nullsec-linux)

*Key fob signal analysis, rolling code research, relay attack detection, and immobilizer security testing*

</div>

---

## 🎯 Overview

NullSec KeyFob provides tools for analyzing the security of automotive keyless entry and immobilizer systems. It supports research into rolling code algorithms, relay attack vectors, and transponder authentication — critical for understanding vehicle access control security.

## ⚡ Features

| Feature | Description |
|---------|-------------|
| **Signal Analyzer** | Capture and decode key fob RF transmissions (315/433/868 MHz) |
| **Rolling Code Analyzer** | Analyze KeeLoq, Hitag2, and proprietary rolling code systems |
| **Relay Detector** | Detect and measure relay/amplification attack viability |
| **Transponder Reader** | Read and analyze immobilizer transponder data |
| **Protocol Decoder** | Decode TPMS, RKE, and PKE protocols |
| **Vulnerability Scanner** | Test for known key fob vulnerabilities |

## 🔬 Supported Systems

| System | Protocol | Analysis | Status |
|--------|----------|----------|--------|
| KeeLoq | Rolling code | Cryptanalysis | ✅ |
| Hitag2 | Challenge-response | Key recovery | ✅ |
| AUT64 | Transponder | Protocol analysis | ✅ |
| DST40 | Transponder | Known weaknesses | ✅ |
| Megamos | Transponder | Protocol analysis | ⚠️ |
| TPMS | Broadcast | Decode | ✅ |

## 🚀 Quick Start

```bash
# Capture key fob signal
nullsec-keyfob capture --freq 433.92M --sdr hackrf -o keyfob_capture.iq

# Analyze rolling code
nullsec-keyfob analyze --input keyfob_capture.iq --protocol keeloq

# Scan for TPMS signals
nullsec-keyfob tpms --freq 315M --duration 60

# Test relay attack range
nullsec-keyfob relay-test --mode measure --timeout 30
```

## 🔗 Related Projects

| Project | Description |
|---------|-------------|
| [nullsec-canbus](https://github.com/bad-antics/nullsec-canbus) | CAN bus analysis & fuzzing |
| [nullsec-carfuzz](https://github.com/bad-antics/nullsec-carfuzz) | Automotive protocol fuzzer |
| [nullsec-sdr](https://github.com/bad-antics/nullsec-sdr) | Software-defined radio toolkit |
| [nullsec-flipper-suite](https://github.com/bad-antics/nullsec-flipper-suite) | Flipper Zero payloads (430+ files) |
| [nullsec-linux](https://github.com/bad-antics/nullsec-linux) | Security Linux distro (140+ tools) |

## ⚠️ Legal

For **authorized automotive security research only**. Testing keyless entry systems without vehicle owner authorization is illegal.

## 📜 License

MIT License — [@bad-antics](https://github.com/bad-antics)

---

<div align="center">

*Part of the [NullSec Automotive Security Suite](https://github.com/bad-antics)*

</div>
