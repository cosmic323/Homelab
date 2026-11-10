# Ubuntu Server Installation

This document covers the installation and initial configuration of Ubuntu Server on the Lenovo ThinkPad T480, which serves as the primary homelab server.

## 1. Installation Overview

| Item | Details |
|---|---|
| Machine | Lenovo ThinkPad T480 |
| Hostname | `homelab` |
| Operating system | Ubuntu Server 24.04.5 LTS |
| Architecture | x86-64 |
| Installation type | Fresh installation |
| Primary storage | Internal NVMe SSD |
| Additional storage | External 1 TB HDD |

## 2. Installation Media

Ubuntu Server was installed using the official Ubuntu Server 24.04.5 LTS ISO image.

| Item | Details |
|---|---|
| ISO image | `ubuntu-24.04.5-live-server-amd64.iso` |
| Architecture | AMD64 (x86-64) |
| Media | Bootable USB drive |
| Verification | SHA-256 checksum |

The downloaded ISO was verified against the official Ubuntu checksum before creating the installation media.

**SHA-256:**

```text
97f3d7ffb032c3eb3b23d2c8be9cc76e60c2c1f2c0146ba5ba9fe01cafae0fd8
```

## 3. Disk Partitioning and LVM

The internal NVMe SSD was configured using the installer's LVM storage option.

### Internal Storage Layout

| Device | Size | Purpose |
|---|---:|---|
| `/dev/nvme0n1` | 238.5 GB | Primary system drive |
| `/dev/nvme0n1p1` | 1 GB | EFI System Partition |
| `/dev/nvme0n1p2` | 2 GB | `/boot` |
| `/dev/nvme0n1p3` | 235.4 GB | LVM physical volume |

### LVM Configuration

| Component | Configuration |
|---|---|
| Volume group | `ubuntu-vg` |
| Logical volume | `ubuntu-lv` |
| Root filesystem | ext4 |
| Logical volume size | 100 GB |
| Mount point | `/` |

The remaining volume group space was left unallocated for future storage expansion.

The external HDD was kept separate from the operating system drive. It uses ext4, has the label `HOMELAB`, and is mounted at `/srv/media`.

## 4. Initial System Configuration

| Setting | Value |
|---|---|
| Hostname | `homelab` |
| Primary user | `cloud` |
| Kernel | `6.8.0-147-generic` |
| Network interface | Ethernet |
| Server IP | `192.168.1.64` |
| Network | `192.168.1.0/24` |
| Gateway | `192.168.1.254` |

The external HDD was configured to mount automatically through `/etc/fstab`. Its filesystem UUID is used instead of its device name to ensure consistent identification across reboots.

## 5. SSH and Remote Administration

OpenSSH Server was installed to allow remote administration over the local network.

| Setting | Value |
|---|---|
| Service | `ssh` |
| Default port | `22` |
| Username | `cloud` |
| Server address | `192.168.1.64` |

The server can be accessed from both Windows PowerShell and Arch Linux using:

```bash
ssh cloud@192.168.1.64
```

This allows the server to be managed remotely without requiring direct physical access.

## 6. Post-Installation Verification

The following commands were used to verify the system configuration:

| Command | Purpose |
|---|---|
| `hostnamectl` | Inspect hostname, OS, kernel, and hardware |
| `lsblk -f` | Inspect disks, filesystems, UUIDs, and mount points |
| `free -h` | Check memory and swap usage |
| `ip addr` | Inspect network interfaces and IP addresses |
| `findmnt /srv/media` | Verify the external HDD mount |
| `sudo mount -a` | Test `/etc/fstab` configuration |

The server was rebooted to verify that the external HDD mounted automatically.

SSH connectivity was also tested from both Windows and Arch Linux.

The installation established the Ubuntu Server environment, internal LVM storage, persistent external storage, network connectivity, and remote administration needed for the next stages of the homelab.