# Initial Proxmox Audit

**Date:** October 28, 2026  
**Node:** ProxmoxNUC  
**Related GitHub Issue:** [#1 Proxmox Audit](https://github.com/Jwalker9189/HomeLab/issues/1)

## Goal

Review my existing Proxmox installation before creating any virtual machines or containers. I wanted to understand the hardware, storage, network settings, and update status without making changes.

## System Information

| Item | Verified result |
|---|---|
| Hardware | Intel NUC 10 |
| CPU | Intel Core i7 10710U |
| Logical CPUs | 12 |
| RAM available to Proxmox | 16.47 GB |
| Proxmox Manager | 9.1.1 |
| Boot mode | EFI |
| Main drive | Samsung SSD 980 500 GB NVMe |
| SSD health | S.M.A.R.T. passed |
| SSD wear | 3% |

## Storage

| Storage | Configuration | Purpose |
|---|---|---|
| Physical SSD | 500.11 GB reported | Hosts Proxmox and its storage volumes |
| Root filesystem | 100.86 GB total | Proxmox system storage |
| `local` | Directory at `/var/lib/vz` | ISO images, templates, backups, imports |
| `local-lvm` | LVM Thin pool (`data`, volume group `pve`) | VM and container disks |
| LVM Thin capacity | 361.98 GB | Available thin pool capacity |
| LVM Thin usage | 0% | No data allocated in this pool at the time of review |

Both `local` and `local-lvm` are enabled and use the same physical SSD. Saving a backup to `local` alone would not protect against failure of that SSD.

## Network Configuration

| Setting | Verified result |
|---|---|
| Router | TP-Link ER605 |
| Router LAN address | `192.168.0.1` |
| LAN subnet | `192.168.0.0/24` |
| Router DHCP | Enabled |
| Router LAN VLAN | 1 |
| Proxmox management address | `192.168.0.103/24` |
| Default gateway | `192.168.0.1` |
| Physical interface in use | `nic0` |
| Linux bridge | `vmbr0` |
| Bridge port | `nic0` |
| VLAN aware bridge | No |

I verified the management address by opening the Proxmox web interface at `https://192.168.0.103:8006`.

## Existing Workloads

- Virtual machines: 0
- LXC containers: 0

I checked the Proxmox server tree and did not find any VMs or containers configured at the time of the audit.

## System Health and Updates

These measurements are a snapshot, not a guarantee of future performance.

| Check | Result |
|---|---|
| CPU usage | Approximately 0.08% |
| RAM usage | 1.81 GB of 16.47 GB |
| Root storage usage | 4.26 GB of 100.86 GB |
| Swap usage | 0 of 8.59 GB |
| Available package updates | 82 listed |

I reviewed the update repositories:

- Debian and Debian Security repositories: enabled
- Proxmox No Subscription repository: enabled
- Proxmox Enterprise repository: disabled
- Ceph Enterprise repository: disabled

No updates were installed during this audit.

## Issues and Troubleshooting

### Issue 1: IP Address Mismatch

**Issue:** My earlier documentation listed Proxmox at `192.168.40.50` with gateway `192.168.40.1`. The current settings showed different addresses.

**What I checked:** Reviewed the Proxmox network page, accessed its web interface at `192.168.0.103:8006`, and confirmed that the ER605 LAN uses `192.168.0.1/24`.

**Resolution:** The current Proxmox address and router subnet were verified. I updated the README to reflect the current network. The reason for the historical difference was not established.

### Issue 2: Update Repository Warning

**Issue:** Proxmox displayed a warning that a nonproduction repository was enabled.

**What I checked:** Opened **Updates → Repositories** and reviewed which repositories were enabled.

**Resolution:** Confirmed that the No Subscription repository is enabled and the Enterprise repositories are disabled. This warning is expected for this homelab configuration. I left the settings unchanged.

### Separate Follow Up: Router System Time

The ER605 Status page displayed the wrong date. This is tracked separately in [Issue #2](https://github.com/Jwalker9189/HomeLab/issues/2). It has not been resolved yet.

## What I Learned

- Proxmox uses a Linux bridge to connect virtual networking to a physical network interface.
- Virtual machines run their own kernel, while LXC containers share the Proxmox host's Linux kernel.
- One SSD can contain separate system and virtual disk storage areas.
- Router and server settings should be checked before assuming old network documentation is correct.
- A repository warning does not always mean something is broken.

## Next Steps

1. Plan backups and recovery before installing updates or important services.
2. Review updates and decide when to apply them.
3. Begin the first Ubuntu Server project after the audit is closed.

**Audit scope:** Review and documentation only. No network, storage, or package settings were changed.
