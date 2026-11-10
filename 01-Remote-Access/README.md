# Project 01 — Secure Remote Access with Cloudflare

## Project Overview

One of my main goals with my Homelab was being able to access it remotely, especially from computers where I can't install additional software.

I wanted to manage Proxmox and Windows Server through a browser without forwarding management ports through my home router.

For this project, I used Cloudflare Zero Trust, a Debian Linux container, and my existing Proxmox environment to create a protected remote-access solution.

## Hardware & Software

- Intel NUC 10 running Proxmox VE
- Debian 12 LXC container (CT 102, `cloud-tunnel`)
- Windows Server 2022 virtual machine (VM 101)
- Cloudflare Tunnel (`cloudflared`)
- Cloudflare Zero Trust, Access policies, and MFA
- Personal domain: `walkertechlab.com`

## What I Configured

**1. Deployed a Linux container.** I created an unprivileged Debian 12 LXC in Proxmox to run Cloudflare Tunnel independently of Windows Server.

**2. Installed Cloudflare Tunnel.** I installed `cloudflared`, configured it as a system service, and verified automatic startup for both the service and the container.

**3. Configured Cloudflare Zero Trust.** I registered a domain and set up an email-restricted Access policy with multifactor authentication.

**4. Configured secure Proxmox access.** I created a protected hostname (`proxmox.walkertechlab.com`) and configured HTTPS certificate validation using Proxmox's internal certificate authority. I also enabled Access-token validation at the tunnel route.

**5. Configured Windows Server Remote Desktop.** I enabled RDP with Network Level Authentication, checked that TCP port 3389 was listening and reachable from the LXC, and configured a Cloudflare private route, target, and browser-rendered RDP application.

## Troubleshooting Experience

During setup, I encountered a **502 Bad Gateway** error after authenticating to Cloudflare Access.

I reviewed the `cloudflared` service logs using `journalctl` and identified an X.509 certificate hostname validation problem.

I corrected the origin hostname configuration while keeping TLS certificate verification enabled and using the Proxmox CA certificate inside my container.

After that correction, I successfully reached Proxmox and its Windows Server VM console.

## Final Results — Verified November 10, 2026

- Successfully authenticated through Cloudflare Access with MFA.
- Opened Proxmox remotely through a browser, logged in, and interacted with its Windows Server VM console.
- Connected directly to Windows Server using browser-rendered RDP.
- Verified **both connections from a work laptop** without installing additional software.
- Used an outbound Cloudflare Tunnel; the setup did not require inbound router port forwarding.
- Verified the `cloudflared` system service was running and enabled, and the container's **Start at boot** setting was enabled.

## Useful Commands

```bash
ip -4 addr                     # Display Linux IPv4 addresses
ping -c 4 1.1.1.1              # Test IP connectivity
systemctl status cloudflared   # Check connector service
systemctl is-enabled cloudflared
journalctl -u cloudflared -n 80 --no-pager
```

```powershell
ipconfig /all
Get-NetTCPConnection -LocalPort 3389 -State Listen
```

## What I Learned

- Virtual machines versus Linux containers
- Linux package management and systemd services
- TCP/IP addressing, DNS, and /32 private network routing
- Identity-based Access policies and MFA
- TLS certificate chains and trusted certificate authorities
- Windows Remote Desktop and Network Level Authentication
- Using logs to troubleshoot connectivity failures

## Future Improvements

- Create a DHCP reservation for the Windows Server VM's IP address.
- Review and restrict Windows RDP firewall rules to approved sources.
- Test recovery after a full Proxmox host restart.
- Continue with Windows Server infrastructure: Active Directory, DNS, DHCP, and Group Policy.
- Keep project documentation current as configurations change.

## Portfolio Note

This is **hands-on Homelab experience**, not a claim of professional production administration. No credentials, access tokens, or private keys are included in this repository.
