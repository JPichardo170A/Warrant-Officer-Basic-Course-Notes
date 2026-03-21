# 🌐 AWS Global Infrastructure & Azure Regions

*Module 04 — Cloud Foundations | Lesson 02*

---

## 🎯 Learning Objectives

- Understand AWS regions, availability zones, and edge locations
- Compare AWS EC2 and Azure Virtual Machines
- Identify cloud storage security pillars and encryption methods
- Understand Virtual Private Cloud (VPC) concepts

---

## 🧱 AWS Global Infrastructure

| Concept | Description |
|---------|-------------|
| **Regions** | Physical locations in the world (e.g., us-east-1) |
| **Availability Zones (AZ)** | Isolated data centers within a region |
| **Edge Locations** | CDN endpoints for low-latency content delivery |
| **Availability Sets** | Groupings that ensure VM redundancy (Azure) |

---

## 🧱 Elastic Compute Cloud (EC2)

A web service that provides **secure, resizable compute capacity** in the cloud. Run virtual machines (called **instances**) on demand, just like physical computers.

- Scalable on demand

### Azure Virtual Machines (Same Concept)

On-demand, scalable computing resources in the Azure environment. Run applications, host Windows or Linux workloads, perform dev/testing or production tasks.

- Also offer on-demand scalability

---

## 🧱 Cloud Storage Security

### Key Pillars

| Pillar | Description |
|--------|-------------|
| **Encryption** | Protect data at rest and in transit |
| **Access Control** | Restrict who can read/write data |
| **Monitoring & Auditing** | Track access and changes |
| **Backup & Recovery** | Ensure data resilience |

> 🧠 **Tip:** Cloud storage is encrypted by default from the vendor upon spin-up.

### AWS S3 Encryption

| Type | Method | Key Management |
|------|--------|---------------|
| At Rest | SSE-S3 | Managed by AWS |
| At Rest | SSE-KMS | Customer-managed keys via AWS KMS |
| At Rest | SSE-C | Customer-provided keys |
| In Transit | HTTPS/TLS | Standard transport encryption |

### Azure Blob Storage

Microsoft's object storage solution for unstructured data (documents, images, videos, backups).

---

## 🧱 Amazon EBS Encryption

Elastic Block Storage provides **block-level storage volumes** for use with Amazon EC2 instances.

**Monitoring tools:** AWS CloudTrail, CloudWatch Logs

---

## 🧱 Virtual Private Cloud (VPC)

A **logically isolated section** of a cloud provider's network where users can launch resources (servers, databases, etc.) in a private, secure environment.

> 💡 **Key Takeaway:** VPCs provide network isolation — they are the foundation of cloud network security, allowing you to define subnets, route tables, and security groups.

---

## ✅ Summary

- AWS regions contain multiple AZs for high availability
- EC2 (AWS) and Virtual Machines (Azure) provide on-demand compute
- Cloud storage security rests on encryption, access control, monitoring, and backup
- S3 supports three encryption methods (SSE-S3, SSE-KMS, SSE-C)
- VPCs provide logically isolated network environments

---

[⬆️ Back to Module Index](../README.md) | [← Previous: 01 — IAM Overview](01_IAM_Overview.md) | [Next: 03 — Incident Response →](03_Incident_Response_in_Cloud.md)
