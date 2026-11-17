# Initial Topology

```text
                         INTERNET
                             |
                             v
                      +-------------+
                      |   pfSense   |
                      |  Firewall   |
                      +------+------+
                             |
                  +----------+----------+
                  |                     |
               VLAN 10                VLAN 20
             Internal LAN             Servers
                  |                     |
             +----+----+           +----+------+
             | Windows |           |  Ubuntu   |
             | Client  |           |  Server   |
             +---------+           +-----------+
                                       |
                              +--------+--------+
                              |                 |
                         +----v----+       +----v----+
                         | Suricata|       |  Wazuh  |
                         | IDS/IPS |       |   SIEM  |
                         +---------+       +---------+
```

## Important design note
Suricata and Wazuh will not necessarily sit literally in-line after the Windows client. Their final placement will be decided during implementation based on the virtualization design and available hardware.


## Host resources and platform decision

| Item | Value |
|---|---|
| Host | Dell Latitude E5470 |
| CPU | Intel Core i7-6820HQ, 4 cores / 8 threads |
| RAM | 7.9 GB |
| Free storage (D:) | ~139 GB |
| Platform | Oracle VirtualBox |
- Firewall: pfSense CE 2.9.0 (chosen at the Netgate Installer prompt). LAN DHCP range not yet verified against 10.20.10.0/24.

### Initial VM sizing (planned, to be validated)
| VM | RAM | vCPU |
|---|---|---|
| pfSense | 1 GB | 1 |
| Ubuntu Server | 2 GB | 1-2 |
| Windows Client | 3-4 GB | 2 |
| Wazuh (later phase) | ~4 GB | 2 |

### Constraints
- RAM and 4 threads limit how many VMs run at once.
- Virtual disks will be dynamically allocated to preserve D: space.
- Wazuh will be deployed in its own phase, with unused VMs shut down.
- Suricata placement (pfSense package vs. Ubuntu) is decided during implementation.

### Host virtualization state (checked)
- A hypervisor is already active on the host (VBS running; Virtual Machine Platform enabled for WSL2).
- Hyper-V, Windows Hypervisor Platform, and Windows Sandbox are disabled.
- VirtualBox is expected to run in its Hyper-V-compatible mode, which may be slower.
- Decision: change nothing on the host yet. Validate real performance when the first VM is created in Phase 2, then decide.

## IP and VLAN plan (Phase 1)

| Network | Subnet | Gateway | Hosts |
|---|---|---|---|
| WAN (VirtualBox NAT) | 10.0.2.0/24 | VirtualBox default | pfSense |
| VLAN 10 - Internal LAN | 10.20.10.0/24 | 10.20.10.1 (pfSense) | Windows Client 10.20.10.10 |
| VLAN 20 - Servers | 10.20.20.0/24 | 10.20.20.1 (pfSense) | Ubuntu Server 10.20.20.10, Wazuh 10.20.20.20 (later) |

Host LAN is 192.168.100.0/24 and is intentionally not reused.

### Segmentation approach
VLAN 10 and VLAN 20 are implemented as two separate VirtualBox Internal Networks (lab-vlan10, lab-vlan20), each attached to its own pfSense adapter. This isolates segments reliably but does not use 802.1Q tagging. Real tagging may be added later.

### Initial firewall policy (to be tested)
| From -> To | Decision |
|---|---|
| VLAN 10 -> VLAN 20 | Allow only SSH (22), HTTP/HTTPS (80/443), ICMP |
| VLAN 20 -> VLAN 10 | Deny new connections |
| VLAN 10/20 -> Internet | Allow DNS, HTTP/HTTPS |
| Internet -> inside | Deny |

## Implemented state (as built)
| VM | OS | RAM | vCPU | Disk | Network |
|---|---|---|---|---|---|
| pfsense-fw | pfSense CE 2.9.0 | 1024 MB | 2 | 16 GB | em0 NAT (WAN, DHCP 10.0.2.15), em1 lab-vlan10 (10.20.10.1/24), em2 lab-vlan20 (10.20.20.1/24) |
| ubuntu-srv | Ubuntu Server 26.04.1 LTS | 1024 MB | 1 | 15 GB | enp0s3 lab-vlan20, static 10.20.20.10/24 |
| client | Xubuntu 26.04 (planned) | ~2048 MB | 2 | TBD | lab-vlan10, DHCP from pfSense |

### Changes from the original plan
- Client changed from Windows 10 to Xubuntu: the Windows 10 installation stayed at 2% on a host with 7.9 GB RAM (memory at ~89%).
- Host is a Dell Latitude E5470 (i7-6820HQ, 7.9 GB RAM). VMs are not run all together; ubuntu-srv is powered off while the client runs.

### Open points
- LAN DHCP range on pfSense not yet verified (installer default was 192.168.1.100-199; intended 10.20.10.100-199).
- Hypothesis (not yet confirmed): the ping to 10.20.20.1 fails because OPT1 has no allow rule. To be checked in the pfSense web UI.