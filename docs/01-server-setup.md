# Ubuntu Server Setup

This document records the installation and initial configuration of the Ubuntu Server system used as the primary homelab server.

## 1. System Configuration

| Property | Value |
|---|---|
| Hostname | `homelab` |
| Operating System | Ubuntu Server 24.04.5 LTS |
| Architecture | x86-64 |
| Primary User | `cloud` |
| Kernel | `6.8.0-147-generic` |
| Server Address | `192.168.1.64` |

## 2. Installation Media

Ubuntu Server was installed using the official Ubuntu Server 24.04.5 LTS installation image.

| Property | Value |
|---|---|
| ISO Image | `ubuntu-24.04.5-live-server-amd64.iso` |
| Installation Media | Bootable USB |
| Verification | SHA-256 checksum |

The ISO image was verified against the official Ubuntu checksum before installation.

**SHA-256 Checksum**

```text
97f3d7ffb032c3eb3b23d2c8be9cc76e60c2c1f2c0146ba5ba9fe01cafae0fd8
```

## 3. Operating System Storage

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

## 4. Network Configuration

| Property | Value |
|---|---|
| Network Interface | Ethernet |
| Server Address | `192.168.1.64` |
| Network | `192.168.1.0/24` |
| Default Gateway | `192.168.1.254` |

## 5. Remote Administration

| Property | Value |
|---|---|
| Username | `cloud` |
| Default Port | `22` |

```bash
ssh cloud@192.168.1.64
```