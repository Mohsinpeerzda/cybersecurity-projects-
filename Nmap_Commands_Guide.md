# Nmap Commands and Usage Guide

This repository contains essential **Nmap commands** for network discovery, scanning, and vulnerability assessment, complete with explanations and sample implementations. Ideal for cybersecurity labs, penetration testing, and ethical hacking learning.

---

## 📅 Date Created: 2025-05-11

## 🔍 1. Basic Host Discovery
```bash
nmap -sn 192.168.1.0/24
```
- **Description**: Ping scan for active hosts (no port scan).

---

## 🚪 2. Port Scanning
```bash
nmap 192.168.1.10            # Top 1000 TCP ports
nmap -p 22,80,443 192.168.1.10 # Specific ports
nmap -p- 192.168.1.10          # All 65535 ports
```

---

## 🔥 3. Scan Techniques
```bash
nmap -sS 192.168.1.10    # SYN Scan (Stealth)
nmap -sT 192.168.1.10    # TCP Connect Scan
nmap -sU -p 53,161 192.168.1.10 # UDP scan
```

---

## 🧠 4. Service and Version Detection
```bash
nmap -sV 192.168.1.10
```

---

## 🎯 5. OS Detection
```bash
nmap -O 192.168.1.10
```

---

## 🕵️ 6. Aggressive Scan
```bash
nmap -A 192.168.1.10
```

---

## 🔎 7. Nmap Scripting Engine (NSE)
```bash
nmap --script vuln 192.168.1.10
nmap -p 445 --script smb-vuln-ms17-010 192.168.1.10
```

---

## 🗃 8. Output Formats
```bash
nmap -oN output.txt -oX output.xml 192.168.1.10
```

---

## ⚙️ 9. Scan Timing
```bash
nmap -T4 192.168.1.10
```

---

## 🧱 10. Firewall/IDS Evasion
```bash
nmap -f 192.168.1.10         # Fragmented packets
nmap --spoof-mac 0 192.168.1.10 # MAC spoofing
```

---

## 🎛 11. Full Recon Command
```bash
nmap -sS -sV -O -p- -T4 -A -oN full_recon.txt 192.168.1.10
```

---

## 📂 Bash Script: `nmap_full_recon.sh`
```bash
#!/bin/bash
TARGET=$1
OUTPUT="$TARGET-$(date +%F).txt"

echo "[*] Starting Nmap full recon on $TARGET"
nmap -sS -sV -O -p- -T4 -A -oN $OUTPUT $TARGET
echo "[+] Scan complete. Output saved to $OUTPUT"
```

Make it executable:
```bash
chmod +x nmap_full_recon.sh
./nmap_full_recon.sh 192.168.1.10
```

---
