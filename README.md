# disable-unpriviledged-ebpf
A simple tweak that affects linux behaviour in kernel and module-level for security hardening runtime by disabling unpriviledged eBPF

## Instructions

#### Add in /etc/systctl.d/98-disable-bpf.conf:
```bash
kernel.unprivileged_bpf_disabled=1
```
#### Apply with:
```bash
sudo sysctl --system > /dev/null
```

#### To affect modules too add (e.g. in /etc/modprobe.d/1-install.conf):
```bash
install ntsync      /bin/true
install bpf_preload /bin/true
```

#### also add (e.g. in /etc/modprobe.d/2-blacklist.conf):
```bash
blacklist ntsync
blacklist bpf_preload
```
