# Infrastructure Overview

## 1. Primary Server

| Property | Value |
|---|---|
| Hostname | `homelab` |
| Operating System | Ubuntu Server 24.04.5 LTS |
| LAN Address | `192.168.1.64` |
| Processor | Intel Core i5-8350U |
| Memory | 8 GB |
| Internal Storage | 256 GB NVMe SSD |
| External Storage | 1 TB HDD |

Detailed hardware specifications are documented in the [Hardware Inventory](docs/01-hardware-inventory.md).

## 2. Network Environment

| Property | Value |
|---|---|
| Network | `192.168.1.0/24` |
| Gateway | `192.168.1.254` |
| Server Address | `192.168.1.64` |

The Ubuntu server can be administered remotely from the other machines using SSH.

## 3. Documentation Structure

| Location | Purpose |
|---|---|
| `docs/` | System configuration and operational documentation |
| `diagrams/` | Infrastructure and architecture diagrams |
| `screenshots/` | Supporting screenshots |
| `README.md` | Main documentation entry point |

Refer to the documentation index in `README.md` to locate detailed procedures and system information.

## 4. Maintenance of This Document

This document should be updated whenever a significant change affects the infrastructure, including:

- Hardware changes or replacements.
- Operating system changes.
- Network configuration changes.
- Changes to machine responsibilities.
- Addition or removal of systems.

*All information should reflect the actual state of the environment.*