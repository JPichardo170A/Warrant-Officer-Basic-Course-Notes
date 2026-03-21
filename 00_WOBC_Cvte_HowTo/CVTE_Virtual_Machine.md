# 🖥️ CVTE Virtual Machine Access Guide

*Module 00 — WOBC CVTE HowTo*

---

## 🎯 Learning Objectives

- Download and configure VMware Horizon Client for CVTE access
- Connect to your Ops Station virtual machine via the built-in remote console
- Connect to your VM via Remote Desktop Connection (RDP) with multi-monitor support

---

## 🔧 Step 1: Download VMware Horizon Client

1. Download and install the **VMware Horizon Client** (you will likely need to restart your system)
2. Open the **Omnissa Horizon Client**
3. Add Server: `https://vdi.ccoelearning.net`
4. Open Chrome (it should default to `home.ccoecaas.net/SAAS/auth/login`)
   - Domain: `ccoecaas.net`
5. Click **Next** and **Agree**
6. Complete login with **CAC credentials**
7. **Do NOT resize** this VM window if you plan to use multiple monitors via RDP

> ⚠️ **Warning:** Resizing the VM window before switching to RDP can cause display issues with multi-monitor setups.

---

## 🔍 Step 2: Access Your Ops Station

Once logged in via Horizon Client:

1. Select **Open for Aria Automation: CSTN – Production**
2. Click on **Service Broker**
3. On the left, click **Deployments**
4. Click your Ops Station (listed with your name)
5. In the Topology window on the left, select the OS you want to use (in class, typically **Ubuntu**)

> 🧠 **Tip:** Note the VM's **IP address** from this screen — you'll need it if using RDP (Option B).

---

## 📋 Connection Options

At this point, you have two options for connecting to your VM:

| Option | Method | Multi-Monitor Support |
|--------|--------|-----------------------|
| A | Built-in Remote Console | No |
| B | Remote Desktop Connection (RDP) | Yes |

---

### Option A: Built-in Remote Console

> *This method does **NOT** support multiple display screens.*

1. From the Ops Station topology screen, click **Actions** → **Connect to Remote Console**
2. A new tab will open and launch your VM

> ✅ **Expected Result:** Your VM desktop appears in the browser tab.

---

### Option B: Remote Desktop Connection (RDP)

> *This method **supports** multiple display screens.*

1. Follow Steps 1–5 above to note the VM's **IP address**
2. On your local machine, open **Remote Desktop Connection** from the Start menu
3. Enter the previously recorded VM IP address
4. Click **Show Options**, then go to the **Display** tab
5. Check **Use all my monitors for the remote session**
6. Click **Connect**

> ⚠️ **Warning:** If you see a blank screen after connecting, press **Enter** or click inside the window — the VM may be asleep.

> ✅ **Expected Result:** Your VM desktop appears across all connected monitors.

---

## ✅ Summary

- Install **VMware Horizon Client** and connect to `https://vdi.ccoelearning.net`
- Authenticate with **CAC credentials** via `ccoecaas.net`
- Access your Ops Station through **Aria Automation → Service Broker → Deployments**
- Use **Option A** (Remote Console) for quick single-screen access
- Use **Option B** (RDP) for multi-monitor support

---

💡 **Key Takeaway:** RDP is the preferred method if you need multi-monitor support for labs. Always note your VM's IP address before switching connection methods.

---

[⬆️ Back to Module Index](../README.md)
