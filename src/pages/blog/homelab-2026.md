---
title: "My HomeLab Setup 2025"
description: "A look at my current homelab - from a trusty HP ProLiant to a beefy Dell Precision, and everything in between."
pubDate: 2025-05-03
category: "HomeLab"
tags: ["homelab", "networking", "vmware", "docker"]
---

I've been running a homelab for about six years now, and it is slowly evolved from "one server under the desk" to... well, slightly more servers under the desk. No fancy rack yet, just chaos beneath my gaming setup. But hey, it works.

Here is what I am running these days.

## The New Beast: Dell Precision 7820

I recently got my hands on a Dell Precision 7820 Tower, and it's a bit overkill for a homelab. But that's kind of the point, right?

- **CPU:** Dual Intel Xeon Gold 6234 @ 3.30GHz (16 cores total)
- **RAM:** 384 GB DDR4
- **GPU:** NVIDIA RTX 6000 24GB GDDR6
- **Hypervisor:** ESXi

Why this much power? I wanted to lab with the big stuff — VMware Cloud Foundation 9.0, nested Cisco Nexus 9000v switches, that kind of thing. My old server was just to old even thinking about it...

## The Old Workhorse: HP ProLiant ML310e Gen8 v2

For the past six years, this little guy has been my playground. 32GB of RAM doesn't sound like much anymore, but it taught me a lot.

On this server I learned to set up:

- Home Assistant for smart home stuff
- Plex, Sonarr, Radarr, Prowlarr, Overseerr — the full arr-stack
- Custom Discord bots for notifications (mostly just for fun and proof-of-concept)

All running in Docker containers. It was the perfect "break things and learn" environment.

## Networking Gear

Nothing too crazy here, but it gets the job done:

- **Firewall:** Fortigate 40F — solid little box for home use
- **Access Points:** 2x UniFi U6 Lite — great coverage, no complaints
- **Switches:** 2x Ubiquiti UniFi Switch 8-Port PoE (60W, managed)

Those UniFi 8-port PoE switches are sadly discontinued, which is a shame because I love them. I've looked at the newer UISP Switch line as a replacement, but honestly, I'll keep using these until they die.

## Network Setup

I'm currently running 24 VLANs on ESXi. No fancy micro-segmentation yet — just good old VLANs keeping things separated. Though I've been eyeing Illumio to play with zero-trust segmentation at home. We'll see if I get around to it.

## What's Running Right Now

On a Ubuntu (Debian-based) VM, I've got a few Docker containers doing the heavy lifting:

- **Technitium DNS** — handling all internal DNS
- **UniFi Controller** — managing the APs and switches
- **Nginx** — simple reverse proxy for internal services
- **Custom notification containers** — pushing alerts to ntfy (more on this in a future post)

And on the ESXi side:

- **VMware Cloud Foundation 9.0** — nested lab for learning VCF
- **EVE-NG** — network simulation for labbing Cisco, Fortinet, and whatever else I want to break

## What's Next?

I've got plans. Too many plans, probably.

- More EVE-NG labs with proper topology diagrams
- Playing with Illumio for micro-segmentation
- Maybe actually building a proper rack setup (we'll see)
- Writing more posts about specific lab projects

For now, everything lives under my gaming desk in a pile of cables and blinking lights. It's not pretty, but it's mine.

---

*Got questions about my setup? Drop a comment below — I'd love to hear what you're running in your homelab too.*
