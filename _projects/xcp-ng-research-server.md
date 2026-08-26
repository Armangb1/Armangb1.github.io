---
title: "Shared XCP-ng Research Server"
description: "Bare-metal XCP-ng hypervisor for a multi-user research group, with an OPNsense router VM for stable per-VM NAT/port-forwarding, and a full MkDocs admin/ops runbook with PDF export."
date: 2026-08-25
tech: ["XCP-ng", "OPNsense", "Linux", "iptables", "Virtualization", "MkDocs", "Networking"]
# image: "/assets/img/projects/xcp-ng-research-server.png"
tags: ["infrastructure", "system administration", "homelab"]
---

Our research group needed one physical machine (96 GB DDR5, Intel Ultra 9, RTX 5090) to serve several people at once — some needing root-level access, some needing a specific OS, some needing the GPU and others just CPU/RAM — without buying separate hardware per person or per project.

**Problem.** A single shared Linux box can't cleanly give multiple users root access, different OSes, and isolated GPU/CPU allocations at the same time. It also needed to be reachable from outside the faculty network, which meant solving external access without turning the whole machine into a security liability.

**Approach.** I installed XCP-ng as the bare-metal hypervisor so each user gets their own VM with the OS, resource split, and access level they need, with the RTX 5090 available for GPU passthrough where required. Getting there wasn't plug-and-play: the board's Realtek RTL8125 NIC needed a driver built and persisted manually before dom0 even had a management IP.

For external access, the faculty network's DHCP-assigned VM IPs kept shifting, which broke any port-forwarding rules hardcoded against them. I deployed OPNsense as a dedicated router VM sitting between the faculty network and the guest VMs: OPNsense's WAN side takes the (still-dynamic) faculty DHCP lease, while its LAN side runs its own DHCP server handing out stable internal IPs to every guest VM. dom0's iptables only has to DNAT a small, fixed set of public ports to OPNsense's WAN address; OPNsense then NATs each service to the right VM by its stable internal IP. A VM reboot no longer breaks anyone's SSH or RDP access.

Because this setup has enough moving parts (NIC driver quirks, dom0 iptables, OPNsense NAT rules, per-VM provisioning conventions) that a future admin — possibly me, months later — would otherwise have to reverse-engineer from scratch, I also built a proper admin/ops runbook with MkDocs Material: install steps, the networking architecture with diagrams, the full NAT/port-forwarding convention, and a PDF export of the whole thing for offline reference.

**Outcome.** The server now supports multiple simultaneous users with isolated environments and stable external SSH/RDP access per VM, survives VM reboots and IP churn without manual intervention, and the setup is fully documented so it's reproducible without relying on anyone's memory of how it was built.