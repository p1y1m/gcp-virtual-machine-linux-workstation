# GCP Virtual Machine Linux Workstation via Chrome Remote Desktop
# Author: Pedro Yanez Melendez

![Debian Linux VM on GCP via Chrome Remote Desktop](debian%20linux%20VM.png)


## Overview

This repository documents the creation and configuration of a **Linux Virtual Machine (VM)** on **Google Cloud Platform (GCP)** using **Compute Engine (GCE)**, accessed graphically through **Chrome Remote Desktop**.

The VM behaves as a **full remote workstation**, capable of running development tools, cloud SDKs, browsers, editors, and administrative workloads.  
By **increasing RAM or disk size**, this same VM can scale from a lightweight admin box to a **full development or data workstation**.

---

## Key Concepts Used

- **Virtual Machine (VM)**  
- **Google Cloud Compute Engine (GCE)**  
- **Persistent Disks (resizable)**  
- **Vertical scaling (RAM / CPU)**  
- **SSH-based provisioning**  
- **Browser-based remote desktop (Chrome Remote Desktop)**  
- **Linux desktop environments (XFCE)**  
- **Cloud networking & firewall model (no inbound RDP/VNC exposure)**  

---

## Why a Virtual Machine?

This setup uses a **real cloud VM**, not a container or temporary environment:

- Dedicated **CPU, RAM, and disk**
- Persistent state across reboots
- OS-level customization
- Suitable for long-running workloads
- Can be resized at any time:
  - **Increase RAM / CPU** → more performance
  - **Increase disk size** → more storage for tools, data, repos

---

## Architecture Summary

- **Cloud Provider**: Google Cloud Platform  
- **Compute**: Compute Engine Virtual Machine  
- **OS**: Debian Linux  
- **Disk**: Persistent Disk (expandable)  
- **Access model**:
  - SSH → initial setup and maintenance
  - Chrome Remote Desktop → daily graphical usage
- **Security**:
  - No exposed RDP / VNC ports
  - OAuth-based Google authentication
  - Default firewall rules only

---

## What Can Be Done Inside This VM?

Once connected, this VM can be used for:

- Software development (Python, Java, JS, etc.)
- Cloud administration (gcloud, Terraform, SDKs)
- Data analysis and scripting
- Documentation and technical writing
- Browsing, testing, demos
- Secure work environment independent from local machines

If more power is needed:
- Increase **RAM** → better multitasking
- Increase **Disk** → more tools, datasets, repositories
- Change **machine type** → more CPU cores

No reinstallation required.

---

## Why Chrome Remote Desktop?

Instead of classic RDP or VNC:

- No inbound firewall ports
- Works over HTTPS via Google infrastructure
- Uses Google Account + PIN
- Accessible from browser or mobile
- Ideal for corporate or restricted devices

---

## VM Creation (Compute Engine)

Typical configuration:
- Debian Linux
- Small or medium machine type (e.g. 4 GB RAM)
- Persistent disk (expandable)
- Internet access (external IP or Cloud NAT)

Firewall:
- Default rules only
- No additional inbound rules required

---

## Initial Provisioning via SSH

SSH is used only for:
- Installing system packages
- Configuring the desktop environment
- Registering Chrome Remote Desktop
- Setting user passwords

---

## Desktop Environment Choice

**XFCE** is used because:
- Lightweight
- Low RAM/CPU usage
- No 3D acceleration dependency
- Stable over remote connections
- Officially recommended by Google for CRD

---

## Remote Access Flow

1. VM boots in GCP
2. Chrome Remote Desktop service starts
3. User connects via browser
4. Full Linux desktop session runs inside the VM

All computation happens **inside the virtual machine**, not on the local computer.

---

## Cost & Scalability

- VM cost depends on:
  - Machine type (RAM / CPU)
  - Disk size
  - Running time
- Disk size can be increased at any time
- VM can be stopped when not in use
- Same VM can evolve as needs grow

---

## Use Cases

- Personal cloud workstation
- Secure remote work environment
- Development sandbox
- Cloud admin jump box
- Portfolio / learning infrastructure project

---

## Conclusion

This project demonstrates how to build a **scalable, persistent Linux virtual machine on GCP**, accessed securely through the browser, with full control over compute resources and operating system configuration.

The VM is not limited in scope: **by increasing RAM and disk**, it can support increasingly demanding workloads without changing architecture.
