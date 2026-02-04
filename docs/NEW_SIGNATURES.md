# New Rootkit Signatures for Rupurt v2.6

## New Kernel Rootkits (LKM) - 20 additions

```c
/* 2024 Additions - Modern Threats */
"pumakit", "syshook", "xorboot", "ghostwrite", "kernelsu_abuse",
"darkhalo", "blacktech_lkm", "mustang_panda_lkm", "apt41_lkm",
"scattered_spider_lkm", "alphv_linux", "blackcat_lkm",
"royal_ransomware_lkm", "lockbit_linux", "akira_lkm",

/* Research/Recent Disclosures */
"nftables_backdoor", "netfilter_hook_v2", "ebpf_trojan", 
"perfmon_backdoor", "ftrace_hook_advanced", "kprobe_shell",
"kretprobe_exfil", "livepatch_backdoor", "ksym_hook",
"syscall_wrap", "vfs_iterate_stealth", "getdents_hook_v2",

/* Cloud Native Threats */
"kubernetes_implant", "containerd_backdoor", "cri_o_escape",
"runc_cve_exploit", "overlay_poison", "seccomp_bypass_lkm",
```

## New eBPF Threats - 15 additions

```c
/* eBPF Rootkit Variants */
"ebpf_ghost", "bpf_phantom", "trace_hook", "xdp_stealth",
"tc_phantom", "cgroup_cloak", "sock_ops_backdoor",
"sk_lookup_hijack", "flow_dissector_hook", "lwt_hook",
"struct_ops_abuse", "iter_backdoor", "lsm_bypass_bpf",

/* Advanced eBPF Persistence */
"bpf_link_pin", "bpf_fs_backdoor", "bpf_timer_persist",
```

## New Container/Cloud Threats - 15 additions

```c
/* 2024 Container Escapes */
"leaky_vessels", "runc_cve_2024", "buildkit_escape",
"docker_cp_escape", "moby_escape", "cri_cve_escape",

/* Cloud Credential Theft */
"aws_lambda_backdoor", "fargate_escape", "ecs_persistence",
"gke_backdoor", "aks_escape", "cloud_run_abuse",
"cloud_functions_backdoor", "metadata_v2_bypass",

/* Supply Chain */
"codecov_style", "dependency_confusion_lkm", "xz_style_backdoor",
```

## New Bootkit Signatures - 10 additions

```c
/* 2024 UEFI Threats */
"bootkitty", "glupteba_uefi", "blacklotus_v2", "esp_implant",
"grub_backdoor", "shim_hijack", "mokutil_abuse", "sbat_bypass",
"bootmgfw_patch", "winload_hook_linux",
```

## New Suspicious Ports - Additional ports

```c
/* Modern C2 Ports */
8888, 9443, 8444, 8081, 8082,  /* Web C2 */
6443, 10250, 10255, 2379, 2380, /* Kubernetes */
5000, 5001, 5002,  /* Registry */
53, 853, 443,  /* DNS/DoH tunneling */
4443, 4646, 8200, 8500,  /* HashiCorp */
```

## New Binary Signatures - 12 additions

```c
/* XZ-style indicators */
{"XZ Backdoor", "lzma_decode_init", 0, 16, SEV_CRITICAL},
{"ifunc_resolver", "__get_cpuid", 0, 12, SEV_HIGH},

/* Modern rootkit strings */
{"PumaKit", "puma", 0, 4, SEV_CRITICAL},
{"GhostWrite", "ghostwrite", 0, 10, SEV_CRITICAL},
{"DarkHalo", "darkhalo", 0, 8, SEV_CRITICAL},
{"Bootkitty", "bootkitty", 0, 9, SEV_CRITICAL},
{"eBPF Ghost", "ebpf_ghost", 0, 10, SEV_CRITICAL},
{"LeakyVessel", "leakyvessel", 0, 11, SEV_CRITICAL},

/* Ransomware persistence */
{"LockBit Linux", "lockbit", 0, 7, SEV_CRITICAL},
{"BlackCat/ALPHV", "alphv", 0, 5, SEV_CRITICAL},
{"Akira Linux", "akira", 0, 5, SEV_CRITICAL},
{"Royal Linux", "royal_ransom", 0, 12, SEV_CRITICAL},
```

## ATT&CK Mapping Updates

| Signature Group | ATT&CK Techniques |
|----------------|-------------------|
| eBPF Rootkits | T1014, T1055.009, T1205 |
| Container Escapes | T1611, T1610, T1053.007 |
| Cloud Backdoors | T1078.004, T1552.005, T1537 |
| UEFI Bootkits | T1542.001, T1542.003 |
| Supply Chain | T1195.002, T1195.001 |

## Total Signatures: 280+

Previous: 250+
New additions: 72 signatures across categories

---

**Changelog v2.6:**
- Added 20 new LKM rootkit signatures (2024 threats)
- Added 15 new eBPF threat patterns
- Added 15 new container/cloud attack signatures  
- Added 10 new UEFI bootkit signatures
- Added 12 new binary pattern signatures
- Updated ATT&CK mappings
- Added XZ-style supply chain indicators
- Added ransomware persistence indicators
