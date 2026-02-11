# Signature Documentation

## High-Priority Rootkits

### Diamorphine (RKID-0001)
- **Type**: Loadable Kernel Module
- **Capabilities**: Process hiding, file hiding, privilege escalation
- **Detection**: Module name, hooked getdents, magic signal 63

### Reptile (RKID-0002)
- **Type**: LKM with userland component
- **Capabilities**: Hidden reverse shell, process/file hiding
- **Detection**: /proc/reptile, kmatryoshka loader

### TripleCross (RKID-0050)
- **Type**: eBPF rootkit
- **Capabilities**: Execution hijacking, network hiding, backdoor
- **Detection**: Suspicious BPF program types, TC hook analysis

## Contributing New Signatures

See the [[Signature Database]] wiki page for format and submission guidelines.
