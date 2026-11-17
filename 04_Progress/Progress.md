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
- Windows 10 client attempted and abandoned (see Troubleshooting); client changed to Xubuntu
- ubuntu-srv VM: Ubuntu Server 26.04.1 LTS, 1 GB RAM, 1 vCPU, 15 GB disk, installed manually
- ubuntu-srv static address 10.20.20.10/24 on lab-vlan20 (gateway 10.20.20.1)
- Verified: ubuntu-srv sees pfSense at layer 2 (ARP entry for 10.20.20.1 = em2 MAC, REACHABLE)
- Observed: ping from ubuntu-srv to 10.20.20.1 gets 100% loss while pfSense is running



## Not completed yet
No software has been installed and no lab component has been configured yet.


## Next step
Create the Xubuntu client VM on lab-vlan10 (power off ubuntu-srv first to save RAM), open https://10.20.10.1,
verify the LAN DHCP range, add an allow rule on OPT1, and re-test the ping.