# Skills Checklist

This is the official skill-tracking roadmap for my HomeLab. A skill is **Resume Ready** only after I can demonstrate it, explain it, and link to truthful documentation. Lab experience is not professional production experience.

Statuses: **To Learn** | **Practicing** | **Resume Ready**

## Networking Fundamentals
| Skill | Status | Evidence required |
|---|---|---|
| TCP/IP and addressing | Practicing | Verified VM IP/subnet/gateway/DNS, /32 routing, and port reachability; continue subnet troubleshooting labs |
| VLANs | To Learn | Configure and verify isolated VLANs |
| DHCP | To Learn | Configure and test lab-only address assignment |
| Windows Server DNS | To Learn | Configure and troubleshoot lab DNS records |
| PoE | To Learn | Explain standards and budgets; document hands-on work if available |
| Firewalls | To Learn | Implement and test safe lab rules |
| Managed switching | Practicing | Audit switch and verify port/VLAN configuration |

## Windows Enterprise Administration
| Skill | Status | Evidence required |
|---|---|---|
| Windows Server 2022 | Practicing | Server Manager audit, IP configuration and remote administration verified; enterprise roles pending |
| Active Directory Domain Services | To Learn | Deploy isolated domain, users, groups, OUs |
| Group Policy | To Learn | Apply and verify policies on a client |
| Microsoft 365 / Entra ID | To Learn | Document authorized tenant administration labs |
| Windows troubleshooting | Practicing | Checked RDP configuration, network connectivity and listener; more scenarios pending |
| PowerShell | To Learn | Run and explain safe administrative commands |

## Field Infrastructure and Documentation
| Skill | Status | Evidence required |
|---|---|---|
| Cat5e/Cat6 termination and testing | To Learn | Demonstrate and document cabling work |
| Patch panels and port maps | To Learn | Create accurate port map |
| Ping and traceroute | To Learn | Record and interpret diagnostic results |
| ipconfig and nslookup | Practicing | ipconfig /all output reviewed; nslookup lab still pending |
| Technical documentation | Practicing | Maintain accurate README, diagrams and lab notes |
| Independent troubleshooting | Resume Ready | Identified Cloudflare 502 X.509 mismatch via journalctl and verified fix |

## Project 01 — Remote Access (verified November 10, 2026)

See [Project 01 documentation](01-Remote-Access/README.md).

| Resume skill | Status | Verified evidence |
|---|---|---|
| Proxmox virtualization | Resume Ready | Created and administered VMs and LXC 102; opened VM console remotely |
| Linux LXC deployment | Resume Ready | Built unprivileged Debian 12 LXC 102 |
| Linux service administration | Resume Ready | Installed cloudflared; verified running and enabled at boot |
| Cloudflare Tunnel | Resume Ready | Connected and verified remote access through tunnel |
| Cloudflare DNS configuration | Resume Ready | Published custom Proxmox hostname and browser-based RDP hostname |
| Zero Trust Access and MFA | Resume Ready | Email-only Access policy, MFA enrollment, remote login verified |
| TLS certificate verification | Resume Ready | Configured trusted Proxmox CA and resolved X.509 mismatch without disabling verification |
| Windows RDP configuration | Resume Ready | Verified NLA, TCP 3389 listener, reachability and actual browser-based sign-in |
| Remote browser access | Resume Ready | Proxmox and Windows Server both accessed from a work laptop without additional client installation |

## Current lab baseline (verified November 10, 2026)

- Proxmox host (Intel NUC) is accessible at `192.168.0.103:8006`.
- Windows Server 2022 Standard Evaluation is running as VM 101; Ubuntu Server VM is stopped, not deleted.
- Windows Server is in WORKGROUP and DHCP-enabled, with IPv4 `192.168.0.105/24`, gateway/DHCP/DNS `192.168.0.1`.
- Remote Desktop is enabled with Network Level Authentication; its TCP 3389 listener and local connectivity from LXC 102 were verified.
- LXC 102 (`cloud-tunnel`) is Debian 12 and has been seen at `192.168.0.104/24`. The container and `cloudflared` are set to start at boot.
- Cloudflare Access, MFA, TLS certificate validation, and both Proxmox and Windows RDP browser access were verified, including from the work laptop.
- Windows Server DHCP reservation, RDP firewall source scoping and full host-reboot recovery tests are **pending**.
- No AD DS, Windows DNS Server, Windows DHCP Server or Group Policy configuration is claimed.

## Documentation standard for each lab
1. **Goal:** Which job skill is being demonstrated?
2. **Starting state:** What was verified before changes?
3. **Why:** Explain the purpose of each major step.
4. **Commands/configuration:** Record actual work only.
5. **Validation:** Include output, screenshots or tests.
6. **Issues and resolution:** Describe mistakes and fixes honestly.
7. **Resume evidence:** Draft a bullet only when validated.

## Next milestone
Project 02 — Windows Server Infrastructure: audit current network settings, plan an isolated lab, then build Active Directory, DNS, DHCP and Group Policy step by step. Do not enable a DHCP Server role on the home LAN.

## Portfolio note
This checklist tracks homelab learning, not employment tenure. Do not imply years of professional experience based on lab work.
