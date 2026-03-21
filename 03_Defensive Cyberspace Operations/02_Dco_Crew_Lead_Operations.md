# 🎖️ DCO Crew Lead Operations

*Module 03 — Defensive Cyberspace Operations | Crew Lead Ops*

---

## 🎯 Learning Objectives

- Understand CPT mission types (P-DCO and Incident Response)
- Identify CPT core functions (Hunt, Clear, Enable Hardening, Assess)
- Differentiate between Response and Deliberate actions
- Understand the analytics workflow and support structure
- Know key tools including Gabriel Nimbus and Security Onion

---

## 🧱 Cyber Protection Team (CPT) Mission Types

| Mission Type | Description |
|-------------|-------------|
| **Pro-Active DCO (P-DCO)** | Prepares the defense against likely enemy; finds adversary tools, artifacts, and unknown intrusions |
| **Incident Response (IR)** | Reactive mission to manage consequences; opportunity to regain initiative; finding, scoping, clearing, and determining systemic risk |

---

## 🧱 CPT Core Functions

| Function | Description |
|----------|-------------|
| **Hunt** | Searching through networks to detect evidence of Malicious Cyber Activity (MCA) |
| **Clear** | Engage MCA to eliminate or neutralize it from a network system |
| **Enable Hardening** | Strengthening network systems |
| **Assess** | Assess effectiveness of clearing operations and hardening actions taken by local defenders |

---

## 🧱 Response vs. Deliberate Actions

| Response Action | Deliberate Action |
|----------------|-------------------|
| Search logs for signatures | Position alarms to illuminate tactics |
| Known codes and hashes | Generate intelligence through vigilance of anomalous behavior |
| Use intelligence to sweep for "knowns" | Deliberate defense kill chain |
| Chasing the enemy | "Actions on the Objective" |

> 💡 **Key Takeaway:** Response actions are reactive (chasing known indicators), while deliberate actions are proactive (setting conditions to detect unknown threats).

---

## 🧱 Analytic Support Structure

### Command Structure
- Brigade Analytic Support
- CPBn Analytic Support Cell and 2nd CPBn Analytic
- Cyber Protection Team Analytic Support Officer

### What Are Analytics?

The analytics progression:

1. **Data** — Raw information collected
2. **Information** — Processed and organized data
3. **Knowledge** — Contextual understanding
4. **Situational Awareness and Understanding** — Operational picture

### Analytics Workflow

```
Request (OPORD, Tipper, Support Meeting, Email)
  └── Prioritize (Support / Non-Support)
        ├── Specific → Prepare Analytics → Analyze → Specific Report
        └── General → Planning → Prepare → Execute Support (Event Registration) → Mission Report
```

---

## 🔧 Gabriel Nimbus

Army's front end for the **Big Data Platform (BDP)** — aggregates data from various sources within the DODIN-A and can query up to **one year** of data.

### Security Onion

Open-source platform utilized for Army operations as an intrusion detection system. Includes:

| Tool | Purpose |
|------|---------|
| Elastic Stack + Kibana | Log aggregation and visualization |
| Snort | Network intrusion detection |
| Suricata | Network threat detection engine |
| Zeek | Network analysis framework |
| Squil / Squert | Security event management |
| CyberChef | Data analysis and encoding |
| Wireshark | Packet capture analysis |
| NetworkMiner | Network forensics |

---

## ✅ Summary

- CPTs execute P-DCO (proactive) and IR (reactive) missions
- Four core functions: Hunt, Clear, Enable Hardening, Assess
- Response actions chase known threats; deliberate actions set conditions for detection
- Analytics flow from raw data to situational awareness
- Gabriel Nimbus provides up to 1 year of DODIN-A data
- Security Onion integrates multiple open-source security tools

---

## 📚 References

- ATP 2-33.4

---

[⬆️ Back to Module Index](../README.md) | [← Previous: 01 — Reconnaissance and Analysis](01_Dco_Reconnaissance_and_Analysis.md)
