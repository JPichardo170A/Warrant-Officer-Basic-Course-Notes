# 🔐 IAM Overview — Roles, Policies, MFA & Best Practices

*Module 04 — Cloud Foundations | Lesson 01*

---

## 🎯 Learning Objectives

- Understand IAM roles, policies, and best practices
- Apply Zero Trust Architecture (ZTA) principles
- Differentiate RBAC and ABAC access control models
- Understand Multi-Factor Authentication (MFA) and Privileged Access Management (PAM)

---

## 🧱 IAM Key Concepts

| Concept | Description |
|---------|-------------|
| **IAM Roles** | Identities with specific permissions, assumed by users or services |
| **IAM Policies** | Identity policies, resource policies, service control policies, permission boundaries, session policies |

### IAM Best Practices

- Apply **Least Privilege** — grant only the minimum permissions needed
- **Enable MFA** on all accounts
- **Rotate Keys** regularly
- **No Root User** for daily use
- **Use Roles** instead of long-term credentials

> ⚠️ **Warning:** Using the root account for daily operations is a critical security risk. Always use IAM roles with least privilege.

---

## 🧱 Zero Trust Architecture (ZTA)

**Trust no one by default** — inside or outside your organization.

Protects against:
- Lateral movement
- Credential theft
- Insider threats
- Misconfigurations

> 💡 **Key Takeaway:** Zero Trust assumes breach and verifies every access request regardless of source.

---

## 🧱 RBAC vs. ABAC

| Model | Description |
|-------|-------------|
| **RBAC** (Role-Based Access Control) | Permissions assigned based on user roles |
| **ABAC** (Attribute-Based Access Control) | More flexible and dynamic — permissions based on attributes (user, resource, environment) |

---

## 🧱 Multi-Factor Authentication (MFA)

A security mechanism that requires users to provide **two or more verification factors** to gain access to a system, application, or service.

> 🧠 **Tip:** MFA is a **security** control — it verifies identity.

---

## 🧱 Privileged Access Management (PAM)

A set of technologies, processes, and policies designed to **manage and monitor access** to critical systems and information by users with elevated privileges.

> 🧠 **Tip:** PAM is a **management** framework — it governs how privileged access is granted and monitored.

---

## ✅ Summary

- IAM controls who can access what in cloud environments
- Zero Trust Architecture: never trust, always verify
- RBAC assigns permissions by role; ABAC uses dynamic attributes
- MFA adds layers of identity verification
- PAM manages and monitors privileged access to critical systems

---

[⬆️ Back to Module Index](../README.md) | [← Previous: 00 — Cloud Foundation](00_Cloud_Foundation.md) | [Next: 02 — AWS/Azure Infrastructure →](02_AWS_Global_Infrastructure_and_Azure_Regions.md)
