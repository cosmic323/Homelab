# Hardware Inventory

This document records the hardware specifications, operating systems, and roles of the machines in my homelab environment.

## 1. Infrastructure Overview

| Machine | Hostname | Operating System | Role |
|---|---|---|---|
| Lenovo ThinkPad T480 | `homelab` | Ubuntu Server 24.04.5 LTS | Homelab server |
| Lenovo ThinkPad T480 | `arch34` | Arch Linux | Portable workstation |
| Lenovo LOQ | Not recorded | Windows | Home workstation |

## 2. Ubuntu Server — `homelab`

| Component | Specification |
|---|---|
| Model | Lenovo ThinkPad T480 |
| CPU | Intel Core i5-8350U @ 1.70 GHz |
| RAM | 8 GB |
| Swap | 4 GB |
| Internal storage | 256 GB NVMe SSD |
| External storage | 1 TB HDD |
| Operating system | Ubuntu Server 24.04.5 LTS |
| IP address | `192.168.1.64` |

**Role:** Hosts homelab services, containerized applications, centralized storage, and monitoring.

## 3. Arch Linux — `arch34`

| Component | Specification |
|---|---|
| Model | Lenovo ThinkPad T480 |
| CPU | Intel Core i5-8350U |
| RAM | 16 GB |
| Storage | Kingston SA400S37240G, 223.6 GB |
| Operating system | Arch Linux |
| Architecture | x86-64 |
| Kernel | `7.2.14-arch1-1` |

**Role:** Portable Linux workstation for server administration, networking, troubleshooting, and Linux experimentation.

## 4. Windows Workstation

| Component | Specification |
|---|---|
| Model | Lenovo LOQ (`83JE`) |
| CPU | Intel Core i7-13650HX |
| RAM | 16 GB |
| Storage | WD PC SN5000S, approximately 1 TB |
| Operating system | Windows (version not recorded) |

**Role:** Primary home workstation for development, project documentation, Git, GitHub, and general computing.

---

*Hardware specifications will be updated as the infrastructure evolves.*