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