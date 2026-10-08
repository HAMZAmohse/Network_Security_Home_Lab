# Continue From Here

## Project
Network Security Home Lab (portfolio project).
Repo: github.com/HAMZAmohse/Network_Security_Home_Lab (branch: main).
Treat the repo files as the source of truth. Do not restart the project or create a new roadmap.

## Working rules
- Work step by step. Explain what each command does before the user runs it.
- Verify each important step's output before moving on. Do not assume completed work.
- The user learns by doing. He is comfortable with general networking but new to firewalls, VLAN implementation and security tools. For each step explain: the idea (simple example), what we do, why it matters, how to verify.
- Reply in simple Arabic. Keep English terms minimal; put commands and technical names on their own lines or in code blocks, not inside Arabic sentences.
- Never store passwords, keys, recovery codes or secrets in the project or in Git.

## Current machine
Dell Latitude E5470 (new laptop).
- CPU: Intel Core i7-6820HQ, 4 cores / 8 threads.
- RAM: 7.9 GB (both slots used, 2 x 4 GB). The user decided NOT to upgrade RAM. RAM is the main constraint of this project.
- Storage: D: ~139 GB free (VMs and project live here), C: ~29 GB free.
- Virtualization: enabled in BIOS (Task Manager shows Enabled).
- Installed and verified: Git, VS Code, Oracle VirtualBox. An empty test VM started successfully.
- Project location: D:\Network_Security_Home_Lab (cloned from GitHub).
- VM folder: D:\VirtualBox_VMs (outside the project folder, never committed).

## Status
Phase 1 (Foundations) is complete:
- Git and GitHub working.
- Platform decision: VirtualBox.
- IP and VLAN plan written in 02_Lab_Design/Topology.md.
- Project migrated from the old laptop to this one. The old laptop is being sold and is no longer needed.

No real lab component is installed yet (no pfSense, no VMs for the lab).

## RAM planning (7.9 GB host)
- Windows host needs about 3.5 to 4 GB.
- Planned VM sizes: pfSense 1 GB, Ubuntu Server 1 GB, Windows Client 2 GB.
- Wazuh needs about 4 GB: deploy it in its own phase with other VMs shut down.
- These are estimates. Measure real usage once the VMs run.
- The user keeps the project design unchanged; only VM sizing and which VMs run together adapt to the RAM.

## Next step
Phase 2: create the VirtualBox internal networks (lab-vlan10, lab-vlan20) and the pfSense VM.
Before starting, explain to the user in simple terms what a VLAN and a firewall do.

## Notes
- VLAN 10 and VLAN 20 are implemented as two separate VirtualBox Internal Networks, not real 802.1Q tagging. This is documented in Topology.md.
- Home network is 192.168.100.0/24 and must not be reused in the lab.
- A previous test VM on the old laptop used the default unattended install (user vboxuser). Never reuse that approach for lab VMs; install manually with proper passwords that are not stored in the project.