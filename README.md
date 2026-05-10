# Thet Htoo Zin
**Junior Network Engineer Intern · HND Computing Student · Gusto College**

---

## About Me

I'm a Year 1 HND Computing student with a focus on network infrastructure design and implementation. My work sits at the intersection of structured systems thinking and hands-on Cisco lab configuration — I care about building networks that are not just functional, but maintainable, documented, and scalable by design.

Currently interning at **Apex Core IT Services**, where I'm working on real-world LAN deployments for institutional clients.

---

## Featured Project — Summit Ridge Institute LAN

> **Design and Implementation of a Secure and Scalable LAN**
> *Cisco Packet Tracer · January 2026*

A full-lifecycle network engineering project for a 3-storey academic institution: from requirements gathering through to fault injection testing and improvement roadmapping.

### Architecture at a Glance

```
[Outside-PC] ── 198.51.100.0/24
                    │
              [ISR 4331 Router]  ← Edge / WAN
                    │ 192.168.200.0/30
              [CORE-3560 L3]     ← Inter-VLAN routing (SVIs), collapsed core
             /    |    |    \
         SW-3F  SW-2F  SW-2F  SW-1F  SW-1F
         (Lab)  (SSA)  (FAA) (HR&Acc)(BDO)
```

### VLAN Topology

| VLAN | Department | Subnet | Gateway | Hosts |
|------|-----------|--------|---------|-------|
| 10 | Student Services & Admin | `192.168.10.32/27` | `.33` | 12 PCs + 2 printers |
| 20 | Faculty Academic Affairs | `192.168.10.0/27` | `.1` | 16 PCs + 1 printer |
| 30 | HR & Accounts | `192.168.10.64/27` | `.65` | 10 PCs + 2 printers |
| 40 | Business Dev & Outreach | `192.168.10.128/28` | `.129` | 8 PCs |
| 50 | Computer Training Lab | `192.168.10.96/27` | `.97` | 24 PCs |
| 60 | Servers (DNS/Web/Email/File) | `192.168.10.144/28` | `.145` | 4 servers |
| 99 | Network Management | `192.168.10.160/28` | `.161` | Switch mgmt |

### Centralised Services (VLAN 60)

| Server | IP | Role |
|--------|-----|------|
| DNS | `192.168.10.146` | Internal name resolution |
| Web | `192.168.10.147` | Internal portal (HTTP) |
| Email | `192.168.10.148` | SMTP / POP3 internal mail |
| File | `192.168.10.149` | Centralised file sharing |

### Test Results

| Test Case | Objective | Result |
|-----------|-----------|--------|
| TC-01 | VLAN 50 host addressing & gateway reachability | ✅ Pass |
| TC-02 | Inter-VLAN routing → DNS server (VLAN 60) | ✅ Pass |
| TC-03 | HTTP access to internal web server | ✅ Pass |
| TC-04 | External connectivity via ISR4331 | ✅ Pass |
| TC-05 | Fault injection: incorrect default gateway | ❌ Fail → ✅ Corrected |

**100% functional test pass rate.** TC-05 intentionally validated the troubleshooting methodology: isolate → identify root cause → correct → verify.

### Key Design Decisions & Trade-offs

- **Collapsed core/distribution** — CORE-3560 handles both switching and L3 routing via SVIs. Simplifies management for a 70-endpoint network; acknowledged trade-off is a single point of failure at the core.
- **VLSM addressing** — subnets right-sized per department using `/27` and `/28` masks, consuming only 180 of 254 available addresses in `192.168.10.0/24`.
- **Static IP (prototype phase)** — chosen for lab simplicity; production deployment improvement calls for centralised DHCP per VLAN to eliminate manual configuration errors (as demonstrated by TC-05).
- **Single-vendor Cisco stack** — operational consistency and CLI familiarity prioritised over multi-vendor cost optimisation.

### Identified Bottlenecks & Improvement Roadmap

```
Phase 1 (0–1 month)   │ DHCP deployment, ACL security policies, syslog server
Phase 2 (1–3 months)  │ Network monitoring (LibreNMS/Zabbix), RSTP, DNS redundancy
Phase 3 (3–12 months) │ EtherChannel uplinks, file server clustering, IP re-addressing
Phase 4 (Annual)      │ Web/email redundancy, capacity expansion
```

---

## Skills & Tools

**Networking**
`VLANs` `Inter-VLAN Routing` `STP / RSTP` `Subnetting / VLSM` `NAT` `SSH` `EtherChannel / LACP`

**Platforms & Hardware**
`Cisco IOS` `Catalyst 3560` `ISR 4331` `Cisco Packet Tracer`

**Protocols**
`DNS` `HTTP` `SMTP / POP3` `FTP` `SMB/CIFS` `ARP` `ICMP`

**Concepts**
`Hierarchical Network Design` `VLAN Segmentation` `Fault Diagnosis` `Network Documentation` `Maintenance Scheduling`

---

## Education

**HND Computing** — Gusto College *(Year 1, in progress)*
Module: Network Design & Implementation

---

## Currently Learning

- Access Control Lists (ACLs) and VLAN security policies
- Redundancy protocols (HSRP / VRRP)
- Network monitoring with SNMP-based tools

---

*Last updated: January 2026*
