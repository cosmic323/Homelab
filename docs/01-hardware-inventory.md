# Hardware Inventory

This document describes the physical machines that make up my homelab environment, including their hardware specifications, operating systems, and responsibilities.

## 1. Infrastructure Overview

The environment consists of three machines:

| Machine | Hostname | Operating System | Primary Role |
|---|---|---|---|
| Lenovo ThinkPad T480 | `homelab` | Ubuntu Server 24.04.5 LTS | Homelab server |
| Lenovo ThinkPad T480 | `arch34` | Arch Linux | Portable workstation |
| Lenovo LOQ | Not recorded | Windows | Home workstation |

## 2. Primary Server — Ubuntu

**Hostname:** `homelab`

**Hardware:** Lenovo ThinkPad T480

| Component | Specification |
|---|---|
| CPU | Intel Core i5-8350U @ 1.70 GHz |
| RAM | 8 GB |
| Swap | 4 GB |
| Internal storage | 256 GB SSD |
| External storage | 1 TB HDD |
| Operating system | Ubuntu Server 24.04.5 LTS |
| Network address | `192.168.1.64` |

**Responsibilities:**
- Host homelab services and applications.
- Provide centralized media storage.
- Run containerized applications.
- Provide monitoring and administration services.

## 3. Portable Workstation — Arch Linux

**Hostname:** `arch34`

**Hardware:** Lenovo ThinkPad T480

| Component | Specification |
|---|---|
| CPU | Intel Core i5-8350U |
| RAM | 16 GB |
| Internal storage | Kingston SA400S37240G, 223.6 GB |
| Operating system | Arch Linux |
| Architecture | x86-64 |
| Kernel | `7.2.14-arch1-1` |

**Responsibilities:**
- Portable Linux workstation.
- Remote server administration through SSH.
- Linux experimentation and learning.
- Network troubleshooting and testing.

## 4. Home Workstation — Windows

**Hostname:** Not recorded

**Hardware:** Lenovo LOQ

**Model identifier:** `83JE`

| Component | Specification |
|---|---|
| CPU | Intel Core i7-13650HX (13th Gen) |
| RAM | 16 GB |
| Internal storage | WD PC SN5000S, approximately 1 TB |
| Operating system | Windows (version not yet recorded) |

**Responsibilities:**
- Primary at-home desktop environment.
- Development and project documentation.
- Git and GitHub management.
- General computing.

## 5. Infrastructure Roles

Each machine serves a different purpose:

- **Ubuntu Server:** provides the infrastructure and services.
- **Arch Linux:** provides portable access and Linux administration.
- **Windows:** provides the primary home workstation environment.

Together, these machines form the hardware foundation of the homelab.


*Specifications will be updated as the infrastructure evolves.*