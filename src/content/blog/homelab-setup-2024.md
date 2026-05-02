---
title: "My HomeLab Setup 2024"
description: "A walkthrough of my current homelab setup, including networking gear, servers, and the projects I'm running."
pubDate: 2024-12-28
category: "HomeLab"
tags: ["homelab", "networking", "self-hosting"]
---

Welcome to my homelab! In this post, I'll walk you through my current setup and some of the projects I'm running.

## The Hardware

My homelab has evolved over the years. What started as a single Raspberry Pi has grown into a proper rack setup.

### Networking

- **Firewall:** Fortinet FortiGate for edge security
- **Core Switch:** Cisco Catalyst for routing between VLANs  
- **Access Points:** Aruba for wireless coverage

### Compute

I'm running a mix of physical servers and virtualization:

- Proxmox VE as my hypervisor of choice
- Several Ubuntu Server VMs for different workloads
- Docker containers for most services

## What I'm Running

Some of the services I self-host:

- **Monitoring:** Grafana + Prometheus stack
- **DNS:** Pi-hole for ad blocking
- **Media:** Plex for streaming
- **Automation:** Home Assistant for smart home

## Lessons Learned

Running a homelab has taught me more than any certification could. When things break at 2 AM, you learn fast!

The best advice I can give: document everything. Future you will thank present you.

---

*Have questions about my setup? Leave a comment below!*
