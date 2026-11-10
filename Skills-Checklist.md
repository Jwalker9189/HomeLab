# IT Infrastructure Resume Readiness Checklist

This is the official skill-tracking roadmap for my HomeLab. A skill is **Resume Ready** only after I can demonstrate it, explain it, and link to truthful documentation. Lab experience is not professional production experience.

Statuses: **To Learn** | **Practicing** | **Resume Ready**

## Networking Fundamentals
| Skill | Status | Evidence required |
|---|---|---|
| TCP/IP and addressing | Practicing | Record IP, subnet, gateway, DNS; explain connectivity tests |
| VLANs | To Learn | Configure and verify isolated VLANs |
| DHCP | To Learn | Configure and test lab-only address assignment |
| DNS | To Learn | Configure and troubleshoot lab DNS records |
| PoE | To Learn | Explain standards and budgets; document hands-on work if available |
| Firewalls | To Learn | Implement and test safe lab rules |
| Managed switching | Practicing | Audit switch and verify port/VLAN configuration |

## Windows Enterprise Administration
| Skill | Status | Evidence required |
|---|---|---|
| Windows Server 2022 | Practicing | Inspect configuration; document administration tasks |
| Active Directory Domain Services | To Learn | Deploy isolated domain, users, groups, OUs |
| Group Policy | To Learn | Apply and verify policies on a client |
| Microsoft 365 / Entra ID | To Learn | Document authorized tenant administration labs |
| Windows troubleshooting | To Learn | Diagnose and resolve reproducible issues |
| PowerShell | To Learn | Run and explain safe administrative commands |

## Field Infrastructure and Documentation
| Skill | Status | Evidence required |
|---|---|---|
| Cat5e/Cat6 termination and testing | To Learn | Demonstrate and document cabling work |
| Patch panels and port maps | To Learn | Create accurate port map |
| Ping and traceroute | To Learn | Record and interpret diagnostic results |
| ipconfig and nslookup | To Learn | Record and interpret diagnostic results |
| Technical documentation | Practicing | Maintain accurate README, diagrams and lab notes |
| Independent troubleshooting | Practicing | Document issue, investigation, resolution and verification |

## Verified baseline (November 10, 2026)
- Proxmox on Intel NUC is accessible; Windows Server 2022 VM is running.
- Ubuntu Server VM is stopped, not deleted.
- Windows Server 2022 Standard Evaluation desktop and Server Manager Local Server page were inspected.
- Windows Server is in WORKGROUP, uses DHCP for IPv4, has Remote Desktop disabled, and shows approximately 4 GB allocated RAM and 80 GB total disk.
- Exact Windows Server IPv4 address, subnet, gateway, DNS and DHCP server have **not yet been verified**.
- No AD DS, DNS Server, or DHCP Server configuration is claimed.

## Documentation standard for each lab
1. **Goal:** Which job skill is being demonstrated?
2. **Starting state:** What was verified before changes?
3. **Why:** Explain the purpose of each major step.
4. **Commands/configuration:** Record actual work only.
5. **Validation:** Include output, screenshots or tests.
6. **Issues and resolution:** Describe mistakes and fixes honestly.
7. **Resume evidence:** Draft a bullet only when validated.

## Next milestone
Complete read-only `ipconfig /all` inspection of Windows Server 2022. Design an isolated lab network before enabling any DHCP Server role, to avoid affecting the home network.

## Portfolio note
This checklist tracks homelab learning, not employment tenure. Do not imply years of professional experience based on lab work.
