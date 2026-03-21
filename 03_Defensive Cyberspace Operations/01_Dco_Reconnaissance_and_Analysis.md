# 🔍 DCO Reconnaissance and Analysis

*Module 03 — Defensive Cyberspace Operations | Recon & Analysis*

---

## 🎯 Learning Objectives

- Differentiate between passive and active reconnaissance
- Identify log sources for passive analysis
- Understand network mapping tools and techniques
- Apply reconnaissance methods within mission owner guidance

---

## 🔍 Passive vs. Active Recon

> ⚠️ **Warning:** Determination of what scanning can be used is made by the Mission or Network Owners. Always get authorization before performing active scans.

### Passive Reconnaissance

Passive recon does not interact directly with target systems:

| Technique | Sources |
|-----------|---------|
| **Log Analysis** | Records of events occurring within an organization's systems |
| Network Logs | Zeek, DNS, Router, PCAP, Windows Event Logs (System, Application, Setup, Security) |
| Host Logs | Windows Event Logs, Sysmon, other OS-based logging |
| Passive Capture | Network traffic monitoring without active probing |
| Configuration Mapping | Mapping from existing configuration files |
| Given Config Files | Configuration files provided by network owners |

> 💡 **Key Takeaway:** A log is a record of events occurring within an organization's system. Log analysis is a foundational passive recon skill.

### Active Reconnaissance

Active recon involves direct interaction with target systems:

| Tool/Technique | Description |
|----------------|-------------|
| `ping` | ICMP echo to verify host availability |
| `nmap` | Network scanner for port/service discovery |
| DNS Queries | Active domain name resolution |
| Config Downloads | Downloading configuration files from devices |

---

## 🗺️ Network Mapping

Network mapping is analyzing the network to provide a visual graphical representation of the network design — knowing what is connected to what and where.

**Mapping Tools:**
- Microsoft Visio
- SolarWinds

> 🧠 **Tip:** A thorough network map is critical for identifying Cyber Key Terrain (KT-C) and understanding the attack surface.

---

## ✅ Summary

- Passive recon uses logs, captures, and configs — no direct target interaction
- Active recon uses tools like `ping`, `nmap`, and DNS queries
- Always get mission/network owner authorization before active scanning
- Network mapping provides the visual foundation for all DCO operations

---

[⬆️ Back to Module Index](../README.md) | [← Previous: 00 — DCO Foundations](00_Dco_Defensive_Cyberspace_Operations.md) | [Next: 02 — Crew Lead Operations →](02_Dco_Crew_Lead_Operations.md)
