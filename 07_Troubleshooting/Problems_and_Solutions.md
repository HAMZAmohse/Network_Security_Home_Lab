# Problems and Solutions

## Template
### Problem
### Environment
### Investigation
### Cause
### Fix
### Verification
### Lesson learned
## pfSense installation failed twice ("Failed to commit the file system changes")
- Symptom: the installer reported failure after downloading packages.
- Evidence: console output showed "Timeout was reached" while fetching package 18 of 179 from pkg.pfsense.org.
- Checks: ping 8.8.8.8 from the installer shell worked (0% loss, ~80 ms); DNS resolution from that shell failed.
- Fix: retried the installation on a stable connection; it completed. Probable cause: unstable download (Wi-Fi).
- Note: /tmp/install-log.txt is lost on reboot, so read it before restarting if you need it.

## VM rebooted into the installer after a successful install
- Cause: the installer ISO was still attached, so VirtualBox booted from it.
- Fix: remove the ISO from Settings > Storage (or put Hard Disk first in the boot order). Do not choose Install again.

## Unattended install ran by itself on the first ubuntu-srv VM
- Cause: "Proceed with Unattended Installation" was left enabled in the VirtualBox new-VM wizard.
- Effect: the VM was installed with the default vboxuser account.
- Fix: deleted the VM and recreated it with the option unchecked; installed manually with my own user.

## VM stuck in "Saved" state, storage settings locked
- Cause: the VM had been closed with Save State.
- Fix: Discard saved state (VM becomes Powered Off), then attach the ISO. Use Power Off instead of Save State.

## ISO would not attach / VM said "No bootable medium found"
- Cause: the optical drive was empty (IDE controller) and the VM was in Saved state.
- Fix: attach the ISO to the IDE optical drive while the VM is Powered Off.

## Windows 10 installation stuck at 2%
- Evidence: Task Manager showed memory ~89% and disk 0%; VirtualBox VM using ~1.7 GB.
- Decision: abandon Windows 10 for this host; use a lighter Linux client.
