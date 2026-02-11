# Signature Database

## Signature Format

Each signature contains:
```json
{
  "id": "RKID-0001",
  "name": "Diamorphine",
  "family": "LKM Rootkit",
  "indicators": [
    {"type": "module_name", "value": "diamorphine"},
    {"type": "symbol", "value": "hacked_getdents"},
    {"type": "magic_signal", "value": "63"}
  ],
  "severity": "critical",
  "references": ["https://github.com/m0nad/Diamorphine"]
}
```

## Signature Categories

| Category | Count | Examples |
|----------|------:|---------|
| LKM Rootkits | 45 | Diamorphine, Reptile, Kovid |
| eBPF Rootkits | 20 | TripleCross, pamspy, ebpfkit |
| Userland Rootkits | 35 | Azazel, Jynx2, Vlany |
| Bootkits | 15 | BlackLotus, MosaicRegressor |
| APT Implants | 40 | Drovorub, Winnti, Rekoobe |
| Miners | 25 | XMRig variants, hidden miners |
| Backdoors | 50 | Turla, cd00r, Prism |
| Generic | 50 | Suspicious patterns |

## Adding Signatures

1. Create JSON file in `signatures/custom/`
2. Follow the signature format above
3. Test: `sudo ./rupurt --test-sig signatures/custom/my-sig.json`
4. Submit PR to share with community
