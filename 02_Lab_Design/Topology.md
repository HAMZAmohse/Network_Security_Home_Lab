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
| CPU | AMD A10-8700B, 2 cores / 4 threads |
| RAM | 14.9 GB |
| Free storage (D:) | ~101 GB |
| Firmware virtualization | Enabled |
| Platform | Oracle VirtualBox 7.2.2 |

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