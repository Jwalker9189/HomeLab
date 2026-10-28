# HomeLab Journey

## Introduction

I've always been interested in technology and figuring out how things work. I've built and worked on computers before, but I wanted to take things further and learn more about what happens behind the scenes.

That's what led me to start building my own homelab.

My goal is to get more hands-on experience with networking, servers, virtualization, and cybersecurity. I have a background in IT through school, but I know there's a difference between learning something in a classroom and actually setting it up yourself.

I'm still learning a lot of this, and that's part of the reason I started this project. I don't want to just watch videos or follow tutorials without understanding what I'm doing. I want to be able to set things up, troubleshoot problems, and eventually understand how everything connects and works together.

I'm also building things that I'll actually use at home, so this isn't just a practice environment. I want to create a setup that's useful while giving me real experience managing it.

I created this repository to document everything from start to finish, including the equipment I started with, upgrades I make, projects I complete, mistakes I run into, and how I figure things out.

I'm not starting with a perfect setup or pretending to know everything. The whole point is to learn as I go and be able to look back.

## What I Want to Accomplish

- Get comfortable working with networks, servers, and virtual machines.
- Learn how to set up and manage services instead of relying on plug-and-play solutions.
- Build a better understanding of network security, firewalls, and VLANs.
- Get hands-on experience with Linux and Windows Server.
- Build useful services for my home, including media storage, network monitoring, and backups.
- Develop skills that will help me move into an IT infrastructure, networking, or cybersecurity role.

This repository is basically my way of keeping track of everything I'm learning and building along the way.



# My Homelab Hardware

This is the equipment I'm currently using or have available for my homelab. My goal is to understand how each device works, how they communicate with each other, and how to manage the entire environment.

| Equipment | Specifications | Purpose |
|---|---|---|
| TP-Link ER605 | Multi-WAN Gigabit VPN Router | Main router for my home network. Handles routing between my local network and the internet. |
| TP-Link TL-SG108E | 8-Port Gigabit Managed Switch | Connects my wired devices and allows me to practice network management, VLANs, and network segmentation. |
| Google Nest WiFi | Wireless networking system | Provides wireless connectivity throughout my home. Connected to my managed switch. |
| Intel NUC 10 | Intel Core i7-10710U, 16GB RAM, 500GB NVMe SSD | Main virtualization server running Proxmox VE. Used for virtual machines and future self-hosted services. |
| Minisforum Mini PC | Specifications to be confirmed | Spare computer for testing operating systems and future projects. |
| Main Desktop PC | Personal Windows workstation | Used to remotely access, configure, and manage my homelab. |



# Network Topology

This section documents how my home network and homelab equipment are connected. I'll update it as I add devices, configure VLANs, and make changes to the network.

### Physical Network Layout

```text
             Internet
                |
             Fiber ONT
                |
          TP-Link ER605
           Main Router
                |
       TP-Link TL-SG108E
         Managed Switch
                |
       +--------+---------+
       |        |         |
   Google     Intel      Main PC
   Nest       NUC 10     
   WiFi       Proxmox
       |
   Wireless Devices
```
### Network Information

- **Router:** TP-Link ER605
- **Managed Switch:** TP-Link TL-SG108E
- **Wireless Network:** Google Nest WiFi
- **Virtualization Server:** Intel NUC 10 running Proxmox VE
- **LAN Subnet:** 192.168.40.0/24
- **Default Gateway:** 192.168.40.1
- **Proxmox Management:** Static/reserved LAN address (exact IP documented privately)
- **VLANs:** Not yet configured or verified

This represents my current documented network connections. I'll expand the diagram as I verify additional devices and make changes.
