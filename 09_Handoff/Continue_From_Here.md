# Continue From Here

## Project
Network Security Home Lab (portfolio project). Repo: github.com/HAMZAmohse/Network_Security_Home_Lab (branch: main).
Treat the repo files as the source of truth. Do not restart the project or create a new roadmap.

## Working rules
- Work step by step. Explain what each command does before the user runs it.
- Verify each important step's output before moving on. Do not assume completed work.
- The user learns by doing and is strong in general networking but new to firewalls, VLAN implementation and security tools. For each step explain: the idea (simple example), what we do, why it matters, how to verify.
- Reply in simple Arabic. Keep English terms minimal; put commands and technical names on their own lines or in code blocks.
- Never store passwords, keys or secrets in the project or Git.

## Status
Phase 1 (Foundations) is complete:
- Git and GitHub set up and working.
- Host resources: AMD A10-8700B (2 cores / 4 threads), 14.9 GB RAM, ~101 GB free on D:.
- Platform: Oracle VirtualBox 7.2.2.
- Windows already runs a hypervisor (VBS on, Virtual Machine Platform enabled for WSL2). VirtualBox works but may be slower.
- IP and VLAN plan written in 02_Lab_Design/Topology.md.

## Test VM (local only, not in Git)
A throwaway Ubuntu Server VM (test-ubuntu) was created in D:\VirtualBox_VMs and ran successfully. It was installed unattended with the default vboxuser account, so it must NOT be reused for the project. Plan to delete it.

## Open observations
- The test VM showed IP 10.10.10.2 on eth0, not the usual VirtualBox NAT range. Cause unknown; check its network adapter settings.
- Performance was not fully measured. VirtualBoxVM.exe used ~26% CPU while idle at the login prompt, and RadeonSettings.exe was using ~25% CPU (unrelated to the VM). Turtle icon status unknown.

## Next step
Phase 2: create the VirtualBox internal networks (lab-vlan10, lab-vlan20) and the pfSense VM. Nothing for the real lab is installed yet.

## Laptop migration
The user is moving to a new laptop. On the new machine: install Git, VS Code and VirtualBox, run git clone of the repo, verify the files, then continue. The Ubuntu ISO must be downloaded again.