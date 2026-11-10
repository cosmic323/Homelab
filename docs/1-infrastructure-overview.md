# Infrastructure Overview

## 1. Server

| Property | Value |
|---|---|
| Hostname | `homelab` |
| Operating System | Ubuntu Server 24.04.5 LTS |
| LAN Address | `192.168.1.64` |
| Processor | Intel Core i5-8350U |
| Memory | 8 GB |
| Internal Storage | 256 GB NVMe SSD |
| External Storage | 1 TB HDD |

## 2. Network Environment

| Property | Value |
|---|---|
| Network | `192.168.1.0/24` |
| Gateway | `192.168.1.254` |

### Remote Administration

| Property | Value |
|---|---|
| Username | `cloud` |
| Default SSH Port | `22` |

Connect to the server remotely using:

```bash
ssh cloud@192.168.1.64
```

## 3. Storage Configuration

### Internal NVMe Storage

The internal NVMe SSD was configured using LVM during installation.

| Device | Size | Purpose |
|---|---:|---|
| `/dev/nvme0n1` | 238.5 GB | Primary system drive |
| `/dev/nvme0n1p1` | 1 GB | EFI System Partition |
| `/dev/nvme0n1p2` | 2 GB | Boot partition |
| `/dev/nvme0n1p3` | 235.4 GB | LVM physical volume |

### LVM Configuration

| Component | Value |
|---|---|
| Volume Group | `ubuntu-vg` |
| Logical Volume | `ubuntu-lv` |
| Filesystem | ext4 |
| Logical Volume Size | 100 GB |
| Mount Point | `/` |

The remaining volume group space was left unallocated for future expansion.

### External Storage

| Property | Value |
|---|---|
| Capacity | 1 TB HDD |
| Filesystem | ext4 |
| Label | `HOMELAB` |
| Mount Point | `/srv/media` |

## 4. Documentation Structure

| Location | Purpose |
|---|---|
| `docs/` | System configuration and operational documentation |
| `diagrams/` | Infrastructure and architecture diagrams |
| `screenshots/` | Supporting screenshots |
| `README.md` | Main documentation entry point |

Refer to the documentation index in `README.md` to locate detailed procedures and system information.

## 5. Maintenance

This document should be updated whenever a significant change affects the infrastructure, including:

- Hardware changes or replacements.
- Operating system changes.
- Network configuration changes.
- Storage configuration changes.
- Changes to machine responsibilities.
- Addition or removal of systems.

*All information should reflect the actual state of the environment.*