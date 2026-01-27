# RKHunt v2.5 - Advanced Rootkit Hunter

<p align="center">
  <img src="https://img.shields.io/badge/version-2.5.0-blue?style=flat-square" alt="Version">
  <img src="https://img.shields.io/badge/signatures-200%2B-red?style=flat-square" alt="Signatures">
  <img src="https://img.shields.io/badge/language-C-green?style=flat-square" alt="Language">
  <img src="https://img.shields.io/badge/license-MIT-purple?style=flat-square" alt="License">
</p>

Advanced Linux rootkit detection tool with comprehensive signature database covering modern threats, APT implants, eBPF malware, container escapes, and classic rootkits.

## Features

### Detection Modules (13 Total)

| Module | Flag | Description |
|--------|------|-------------|
| **Process Analysis** | `-p` | Hidden process detection via /proc enumeration vs kill() |
| **Library Injection** | (auto) | LD_PRELOAD hooks, ld.so.preload, suspicious libraries |
| **Kernel Modules** | `-m` | LKM rootkits, suspicious module names, tainted kernel |
| **Filesystem** | `-f` | Rootkit file paths, hidden files in /dev, SUID in temp dirs |
| **Network** | `-n` | Backdoor ports, raw sockets, suspicious connections |
| **Syscall Integrity** | `-s` | Kallsyms analysis, kprobes, ftrace hooks |
| **eBPF Analysis** | `-E` | BPF program enumeration, suspicious mounts |
| **Boot Integrity** | `-b` | UEFI variables, initramfs, kernel cmdline, GRUB |
| **Container Security** | `-c` | Docker/K8s escape indicators, privileged mode |
| **Persistence** | `-e` | Cron, systemd, SSH keys, rc.local backdoors |
| **File Integrity** | `-I` | ELF validation, ownership, permissions, symlinks |
| **Memory Analysis** | `-M` | RWX regions, deleted executables, process injection |

### Signature Database (200+ Total)

#### LKM Rootkits (70+)
```
Modern: singularity, reptile, diamorphine, suterusu, kovid, drovorub, 
        facefish, skidmap, pandora, umbreon, r77, nuk3gh0st, medusa_lkm

APT: turla, uroburos, snake, carbon, penquin, equation, regin, hive,
     bvp47, winnti_lkm, lazarus_lkm, apt28_lkm, apt29_lkm, sandworm_lkm,
     lightning_framework, symbiote, orbit_lkm, shikitega

eBPF: ebpfkit, pamspy, boopkit, bad_bpf, bpf_rootkit, bpfdoor

Classic: adore, adore-ng, knark, suckit, shv4, shv5, t0rn, phalanx,
         lrk3-6, superkit, enyelkm
```

#### Userland Rootkits (35+)
```
jynx, jynx2, jynx3, azazel, vlany, beurk, bdvl, libprocesshider,
cub3, erebus, ld_poison, prochide, umbreon_user, pam_backdoor,
nss_backdoor, openssh_backdoor, libkeyutils_backdoor, xorddos_preload
```

#### Bootkits (35+)
```
UEFI: blacklotus, cosmicstrand, moonbounce, especter, lojax,
      finspy_bootkit, mosaic_regressor, trickbot_uefi, thunderstrike

MBR: rovnix, carberp, tdss, tdl1-4, olmarik, sinowal, mebroot,
     alureon, gapz, bootrash, grayfish, petya, zeroaccess
```

#### Container/Cloud Malware (25+)
```
Cryptominers: kinsing, teamtnt, watchdog, graboid, pro_ocean,
              lemon_duck, z0miner, xanthe

Escapes: doki, hildegard, siloscape, azurescape, cr8escape,
         kubernetes_backdoor, docker_escape, cgroup_escape

Cloud: awscli_backdoor, gcp_backdoor, metadata_thief, imds_exfil
```

## Installation

```bash
# Clone
git clone https://github.com/bad-antics/nullsec-rkhunt
cd nullsec-rkhunt

# Compile
gcc -O2 -Wall -o rkhunt src/rkhunt.c -lpthread

# Install (optional)
sudo cp rkhunt /usr/local/bin/
```

## Usage

```bash
# Full comprehensive scan (default)
sudo ./rkhunt -a

# Quick scan (processes, modules, preload)
sudo ./rkhunt -q

# Specific modules
sudo ./rkhunt -m -s -E    # Modules, syscalls, eBPF
sudo ./rkhunt -e -I -M    # Persistence, integrity, memory

# Output options
sudo ./rkhunt -a -v               # Verbose
sudo ./rkhunt -a -Q               # Quiet (alerts only)
sudo ./rkhunt -a -j               # JSON output
sudo ./rkhunt -a -l scan.log      # Log to file
sudo ./rkhunt -a -d               # Deep scan (slower)

# Full deep scan with logging
sudo ./rkhunt -a -d -v -l /var/log/rkhunt.log
```

### Command Line Options

```
Scan Options:
  -a, --all           Full comprehensive scan (default)
  -q, --quick         Quick scan (processes, modules, preload)
  -p, --processes     Scan for hidden processes
  -m, --modules       Scan kernel modules
  -f, --files         Scan for rootkit files
  -n, --network       Check network backdoors
  -s, --syscalls      Check syscall table integrity
  -b, --boot          Check boot/UEFI integrity
  -c, --container     Container security checks
  -e, --persistence   Check persistence mechanisms
  -E, --ebpf          eBPF program analysis
  -I, --integrity     File integrity verification
  -M, --memory        Deep memory signature scan

Output Options:
  -v, --verbose       Verbose output
  -Q, --quiet         Minimal output (alerts only)
  -l, --log <file>    Log findings to file
  -j, --json          JSON output format
  -d, --deep          Enable deep scanning (slower)
```

## Severity Levels

| Level | Description | Exit Code |
|-------|-------------|-----------|
| **CRITICAL** | Active rootkit/compromise detected | 2 |
| **HIGH** | Strong indicators of compromise | 1 |
| **MEDIUM** | Suspicious activity, needs review | 0 |
| **LOW** | Minor anomalies, informational | 0 |

## Example Output

```
  ╭──────────────────────────────────────────╮
  │  RKHunt v2.5  │  Advanced Rootkit Hunter  │
  │     github.com/bad-antics/nullsec-rkhunt │
  ╰──────────────────────────────────────────╯
  ▸ System: Linux 6.x.x x86_64
  ▸ Starting rootkit scan...

  ───── Kernel Modules ─────
   [ROOTKIT_LKM] █: Known rootkit module loaded: reptile

  ───── Persistence Mechanisms ─────
   [CRON] █: Reverse shell pattern in cron: /etc/cron.d/update

  ╭────────────────────────────────────────╮
  │           SCAN RESULTS                │
  ├────────────────────────────────────────┤
  │  Critical:             2                │
  │  High:                 0                │
  ╰────────────────────────────────────────╯

  █████ SYSTEM COMPROMISED █████
  2 critical finding(s) detected
  Immediate incident response recommended
```

## Changelog

### v2.5.0 (2026-01-26)
- Added eBPF/BPF program analysis module
- Added file integrity verification module
- Added 50+ new rootkit signatures
- Added severity-based reporting (Critical/High/Medium/Low)
- Added deep scan mode
- Improved memory analysis
- Added APT implant signatures (APT28, APT29, Lazarus, etc.)
- Added modern eBPF rootkits (ebpfkit, bpfdoor, pamspy, boopkit)
- Enhanced container escape detection
- Improved output formatting

### v2.0.0
- Complete rewrite with modular architecture
- Added 150+ rootkit signatures
- Added container security checks
- Added boot integrity analysis
- Added persistence mechanism detection

## Contributing

Pull requests welcome. For major changes, open an issue first.

## License

MIT - See [LICENSE](LICENSE)

---
<p align="center">
  <b>NullSec</b> | <a href="https://github.com/bad-antics">bad-antics</a> | discord.gg/killers
</p>
