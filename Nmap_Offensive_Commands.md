# 🔥 Offensive Nmap Command Arsenal

This document is a **complete and advanced guide** to using **Nmap** offensively for ethical hacking, penetration testing, and red teaming operations. This includes bypassing firewalls, evading IDS, exploiting vulnerable services, and recon at an elite level.

---

## ⚔️ 1. Stealthy and Aggressive Scanning

### 🔸 Full Stealth Recon (Silent but Deep)
```bash
nmap -sS -T2 -Pn -f --data-length 1337 -D RND:10 -p- -oN stealth_scan.txt <target>
```
- `-sS`: SYN scan (stealth).
- `-T2`: Slow timing to reduce detection.
- `-Pn`: No ping (skip host discovery).
- `-f`: Fragment packets to bypass firewalls.
- `--data-length 1337`: Random data padding.
- `-D RND:10`: Use 10 decoy IPs.
- `-p-`: All 65535 ports.

---

## 🎯 2. Aggressive All-in-One Recon

### 🔸 Full Recon with Service, OS, Scripts
```bash
nmap -sS -sV -O -A -p- -T4 -oN full_recon.txt <target>
```
- `-sV`: Version detection.
- `-O`: OS detection.
- `-A`: Aggressive mode (scripts, traceroute).
- `-T4`: Faster timing.

---

## 💣 3. Vulnerability Exploitation Scans (NSE)

### 🔸 All Vulnerability Scripts
```bash
nmap --script vuln -p- <target>
```

### 🔸 Specific SMB Exploit (EternalBlue)
```bash
nmap -p 445 --script smb-vuln-ms17-010 <target>
```

### 🔸 HTTP Vuln Enumeration
```bash
nmap -p 80,443 --script http-vuln* <target>
```

---

## 🕵️ 4. Firewall/IDS Evasion Techniques

### 🔸 MAC Spoof + Fragment + TTL Manipulation
```bash
nmap -sS -Pn -T3 --spoof-mac 00:11:22:33:44:55 -f --ttl 65 -p- <target>
```

---

## 🗃 5. Output for Reporting

### 🔸 Multiple Output Formats
```bash
nmap -sS -sV -p- -oA scan_report <target>
```
- Saves as: `scan_report.nmap`, `.xml`, and `.gnmap`.

---

## 🧪 6. Custom Nmap Lab Bash Script

### 🔸 `nmap_offensive_recon.sh`
```bash
#!/bin/bash
TARGET=$1
OUTDIR="recon-$(date +%F)"
mkdir -p $OUTDIR

echo "[*] Starting offensive scan on $TARGET"
nmap -sS -sV -O -A -T4 -p- -oA $OUTDIR/full_$TARGET $TARGET
nmap -Pn -f --data-length 1337 -D RND:5 --spoof-mac 0 -p- -oA $OUTDIR/stealth_$TARGET $TARGET
nmap --script vuln -p- -oA $OUTDIR/vuln_$TARGET $TARGET
echo "[+] Scan complete. Results saved in $OUTDIR/"
```

Make it executable:
```bash
chmod +x nmap_offensive_recon.sh
./nmap_offensive_recon.sh <target-ip>
```

---

## 📂 Recommended GitHub Structure

```
nmap-offensive/
├── README.md
├── nmap_offensive_recon.sh
├── scan_samples/
│   ├── full_target.nmap
│   ├── stealth_target.nmap
│   └── vuln_target.nmap
└── screenshots/
```

---

**⚠️ WARNING:** Use responsibly. Offensive tools like these are only for educational or authorized penetration testing engagements.

