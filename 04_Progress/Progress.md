# Progress

## Current status
Phase 1 — Foundations

## Completed
- Project concept selected
- Initial topology drafted
- High-level roadmap defined
- Project documentation structure created
- Git repository initialized and pushed to GitHub (main)
- Host resources reviewed
- Virtualization platform confirmed: Oracle VirtualBox 7.2.2
- IP and VLAN plan defined (Phase 1 complete)
- Project migrated to a new laptop (Dell Latitude E5470, 7.9 GB RAM); VirtualBox verified
- pfsense-fw VM created in VirtualBox (2 vCPU, 2048 MB RAM, 16 GB disk, 3 adapters)
- pfSense CE 2.9.0 installed via Netgate Installer v1.2
- Interfaces assigned: WAN em0 (NAT, DHCP), LAN em1 10.20.10.1/24 (lab-vlan10), OPT1 em2 10.20.20.1/24 (lab-vlan20)


## Not completed yet
No software has been installed and no lab component has been configured yet.


## Next step
Create a client VM on lab-vlan10 to reach the pfSense web interface (https://10.20.10.1) and verify DHCP and connectivity.