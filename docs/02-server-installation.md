# Ubuntu Server Installation

This document describes the installation and initial configuration of Ubuntu Server on the Lenovo ThinkPad T480 used as the primary homelab server.

The goal was to establish a clean, reliable Linux server environment that can support containerized applications, centralized storage, remote administration, and future infrastructure projects.

## 1. Installation Overview

| Item | Details |
|---|---|
| Machine | Lenovo ThinkPad T480 |
| Hostname | `homelab` |
| Operating system | Ubuntu Server 24.04.5 LTS |
| Architecture | x86-64 |
| Installation type | Fresh installation |
| Installation media | Bootable USB drive |
| Primary storage | Internal NVMe SSD |
| Additional storage | External 1 TB HDD |

### Installation Objectives

- Establish a clean Ubuntu Server environment.
- Configure reliable internal storage.
- Prepare the system for remote administration through SSH.
- Preserve external storage as a separate data drive.
- Create a foundation for future homelab services.

## 2. Installation Media Preparation

Ubuntu Server was installed using the official Ubuntu Server 24.04.5 LTS ISO image.

### Installation Media Details

| Item | Details |
|---|---|
| ISO image | `ubuntu-24.04.5-live-server-amd64.iso` |
| Version | Ubuntu Server 24.04.5 LTS |
| Architecture | AMD64 (x86-64) |
| Installation media | USB flash drive |
| ISO verification | SHA-256 checksum |

### Integrity Verification

Before creating the bootable USB drive, the downloaded ISO image was verified using its SHA-256 checksum.

Expected SHA-256:

`97f3d7ffb032c3eb3b23d2c8be9cc76e60c2c1f2c0146ba5ba9fe01cafae0fd8`

The checksum was compared against the official Ubuntu release information to verify the integrity of the downloaded installation image.

## 3. Disk Partitioning and LVM Configuration

During installation, the internal NVMe SSD was selected as the primary system drive. The installer was configured to use the entire disk with Logical Volume Management (LVM).

### Internal Storage Layout

| Device | Size | Type | Purpose |
|---|---:|---|---|
| `/dev/nvme0n1` | 238.5 GB | NVMe SSD | Primary system drive |
| `/dev/nvme0n1p1` | 1 GB | EFI System Partition | UEFI boot files |
| `/dev/nvme0n1p2` | 2 GB | ext4 | `/boot` |
| `/dev/nvme0n1p3` | 235.4 GB | LVM physical volume | Logical volume storage |

### LVM Configuration

The third partition was configured as an LVM physical volume.

Within the volume group, the installer created a logical volume for the Ubuntu root filesystem.

| LVM Component | Name / Size |
|---|---|
| Volume group | `ubuntu-vg` |
| Logical volume | `ubuntu-lv` |
| Root filesystem | ext4 |
| Root logical volume size | 100 GB |
| Mount point | `/` |

The remaining volume group space was left unallocated, providing flexibility for future storage expansion.

### External Storage

The external 1 TB HDD was kept separate from the internal operating system storage.

The drive uses the ext4 filesystem and has the label `HOMELAB`. It is mounted at `/srv/media` and used for homelab data.

Keeping system storage and external data storage separate makes it easier to manage the operating system independently from personal and application data.

## 4. Initial System Configuration

After installation, the server was configured with a hostname, administrative user, network connectivity, and remote access.

### System Identity

| Setting | Value |
|---|---|
| Hostname | `homelab` |
| Operating system | Ubuntu Server 24.04.5 LTS |
| Kernel | `6.8.0-147-generic` |
| Primary user | `cloud` |
| Network interface | Ethernet |

### Network Configuration

The server was connected to the local network through its Ethernet interface.

| Setting | Value |
|---|---|
| Server IP address | `192.168.1.64` |
| Network | `192.168.1.0/24` |
| Router / Gateway | `192.168.1.254` |

The server was assigned a local network address so that other machines could communicate with it.

### Storage Mount Configuration

The external HDD was configured to mount automatically at `/srv/media`.

An entry was added to `/etc/fstab` using the filesystem UUID rather than the device name.

This ensures that the drive can be identified consistently even if its device designation changes between boots.

## 5. SSH and Remote Administration

OpenSSH Server was installed and configured to allow remote administration over the local network.

### SSH Configuration

| Setting | Value |
|---|---|
| SSH service | OpenSSH Server |
| Service name | `ssh` |
| Default port | `22` |
| Server address | `192.168.1.64` |
| SSH username | `cloud` |

### Remote Access

The server can be accessed remotely from other machines on the local network.

**Windows PowerShell:**

```powershell
ssh cloud@192.168.1.64
```

**Arch Linux:**

```bash
ssh cloud@192.168.1.64
```

SSH provides an encrypted connection for remote command execution and system administration.

### Administration Workflow

The Ubuntu Server acts as the central system, while the Windows and Arch Linux machines provide remote access.

This allows server administration without requiring direct physical access to the machine.

## 6. Post-Installation Verification

After installation and initial configuration, several checks were performed to confirm that the server was operating correctly.

### System Information

The following commands were used to inspect the system:

```bash
hostnamectl
```

Displays the hostname, operating system, kernel, and hardware information.

```bash
lsblk -f
```

Displays block devices, filesystems, UUIDs, labels, and mount points.

```bash
free -h
```

Displays memory and swap usage.

```bash
ip addr
```

Displays network interfaces and assigned IP addresses.

### Storage Verification

The external HDD mount was checked using:

```bash
findmnt /srv/media
```

The `/etc/fstab` configuration was tested using:

```bash
sudo mount -a
```

The server was also rebooted to verify that the external HDD mounted automatically.

### Remote Access Verification

SSH connectivity was tested from both Windows and Arch Linux.

Successful remote connections confirmed that the server could be administered over the local network.

### Installation Result

The installation established a working Ubuntu Server environment with:

- Ubuntu Server 24.04.5 LTS.
- LVM-based internal storage.
- Separate external storage mounted at `/srv/media`.
- Persistent storage configuration through `/etc/fstab`.
- Remote administration through SSH.
- Verified network connectivity.

This provides the foundation for deploying and managing homelab services.