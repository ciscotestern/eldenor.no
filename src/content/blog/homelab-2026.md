---
title: "My HomeLab Setup 2026"
description: "A look at my current homelab - from a trusty HP ProLiant to a beefy Dell Precision, and everything in between."
pubDate: 2026-05-03
category: "HomeLab"
tags: ["homelab", "networking", "vmware", "docker"]
---

I have been running a homelab for about six years now, and it has slowly evolved from "one server under the desk" to... well, a slightly more beefy server under the desk. No fancy rack yet, just chaos beneath my gaming setup. But hey, it hopefully delivers what I want to accomplish.

Here is what I am running these days.

## The New Beast: Dell Precision 7820

I recently got my hands on a Dell Precision 7820 Tower, and it is a bit overkill for a homelab. But that is kind of the point, right?

- **CPU:** Dual Intel Xeon Gold 6234 @ 3.30GHz (16 cores total)
- **RAM:** 384 GB DDR4
- **GPU:** NVIDIA RTX 6000 24GB GDDR6
- **Hypervisor:** ESXi

Why this much power? I wanted to lab with the big stuff — VMware Cloud Foundation 9.0, nested Cisco Nexus 9000v switches, that kind of thing. My old server was just too old to even think about running any of that.

## The Old Workhorse: HP ProLiant ML310e Gen8 v2

For the past six years, this little guy has been my playground. 32GB of RAM does not sound like much anymore, but it taught me a lot.

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

Those UniFi 8-port PoE switches are sadly discontinued, which is a shame because I love them. I have looked at the newer UISP Switch line as a replacement, but honestly, I will keep using these until they die.

## Network Setup

I am currently running 24 VLANs on ESXi. No fancy micro-segmentation yet, just good old VLANs keeping things separated. Though I have been eyeing Illumio to play with zero-trust segmentation at home. I am sure i will get a post on it rather soon :)

## What is Running Right Now

On a Ubuntu VM, I have got a few Docker containers doing the heavy lifting:

- **Technitium DNS** — handling all internal DNS
- **UniFi Controller** — managing the APs and switches
- **Nginx** — simple reverse proxy for internal services
- **Custom notification containers** — pushing alerts to ntfy (more on this in a future post)

And on rest of the ESXi:

- **VMware Cloud Foundation 9.0** — nested lab for learning VCF (holodeck)
- **EVE-NG** — network simulation for labbing Cisco, Fortinet, Palo Alto and whatever else I want to break

## This Website

Speaking of homelab projects — this website is one of them. I recently ditched WordPress and rebuilt the whole thing using Astro, a static site generator.

The setup is stupidly simple and I love it:

- **Code:** Astro + Markdown, hosted on [GitHub](https://github.com/ciscotestern/eldenor.no)
- **Hosting:** Netlify (free tier, and it is great!)
- **Comments:** Giscus (uses GitHub Discussions)
- **SSL:** Free, automatic via Netlify (Just like nginx)

The workflow is beautiful. I write a blog post in Markdown, push it to GitHub, and Netlify automatically builds and deploys the site within 30 seconds. No FTP, no manual uploads, no nonsense. Just write and push. Who ever wants wordpress?

If you are still running WordPress for a simple blog or portfolio, do yourself a favor and look into static site generators. Simplisity is and security is the best right?

## What is Next?

I have got plans. Too many plans, probably?

- More EVE-NG labs with proper topology diagrams
- Playing with Illumio for micro-segmentation
- Maybe actually building a proper rack setup (we will see)
- Writing more posts about specific lab projects

For now, everything lives under my gaming desk in a pile of cables and blinking lights. Follow and more blogposts is right around the corner.

---

*Got questions about my setup? Drop a comment below, I would love to hear what you are running in your homelab too.*
