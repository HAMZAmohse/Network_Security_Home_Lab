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