# Network Security Home Lab — Project Context

## Project Goal

This project is a practical Network Security Home Lab designed to build a realistic and reproducible cybersecurity environment for learning, testing, documentation, and portfolio presentation.

The goal is not simply to install security tools.

The project should demonstrate the full security workflow:

Network Design → Segmentation → Firewall Policies → Traffic Analysis → IDS/IPS → SIEM → Detection → Investigation → Documentation

## Planned Lab Architecture

```text
Internet
   |
   v
pfSense Firewall
   |
   +----------------------+
   |                      |
VLAN 10                 VLAN 20
Internal LAN            Servers
   |                      |
Windows Client       Ubuntu Server
                          |
                    Security Services
                    - Suricata
                    - Wazuh
```

## Main Components

* pfSense — Firewall and network gateway
* VLAN 10 — Internal client network
* VLAN 20 — Server network
* Windows Client — Internal endpoint
* Ubuntu Server — Server/security environment
* Suricata — IDS/IPS
* Wazuh — SIEM and security monitoring
* Wireshark — Network traffic analysis

## Planned Roadmap

1. Project and Lab Design
2. Virtual Lab Setup
3. pfSense Firewall
4. VLANs and Network Segmentation
5. Windows Client and Ubuntu Server
6. Firewall Policies and Connectivity Testing
7. Wireshark Traffic Analysis
8. Suricata IDS/IPS
9. Wazuh SIEM and Monitoring
10. Defensive Detection and Investigation Scenarios
11. Documentation and Portfolio Presentation

## Important Project Principle

The project must remain practical and reproducible.

Every major configuration should be documented with:

* What was configured
* Why it was configured
* Commands used
* Configuration details
* Expected result
* Actual result
* Problems encountered
* How the problem was solved
* Screenshots when useful

## Current Implementation Status

The actual virtual lab has NOT started yet.

The following have been completed:

* Project folder created
* Project documentation structure created
* Git repository initialized
* `.gitignore` created
* Project files staged
* Git identity configured
* Git branch renamed from `master` to `main`

The following have NOT been implemented yet:

* Virtual machines
* pfSense
* VLANs
* Windows Client VM
* Ubuntu Server VM
* Suricata
* Wazuh
* Wireshark lab scenarios
* Firewall rules
* Detection scenarios

## Source of Truth

The Git repository and project documentation are the source of truth for the project's current state.

AI assistants are helpers and mentors.

No AI assistant should change the architecture or roadmap without a clear technical reason and explicit agreement from the user.

## AI Continuity Rule

If the conversation with the current AI ends because of a usage limit or another interruption, a new AI should read the files inside `00_AI_Context` before continuing the project.

The new AI should continue from the documented current state instead of restarting the project.

## Working Method

The project should be completed one major step at a time.

Before executing an important command or making a major configuration change:

1. Explain what we are going to do
2. Explain why
3. Give the required command or action
4. Wait for the result
5. Verify the result
6. Update project documentation when appropriate

Do not give a large list of unrelated commands at once.

## Portfolio Goal

The final project should demonstrate practical understanding of:

* Network Security
* Network Segmentation
* Firewall Configuration
* IDS/IPS
* SIEM
* Log Analysis
* Network Traffic Analysis
* Detection Engineering
* Security Investigation
* Troubleshooting
* Technical Documentation

The final repository should be understandable to another technical person who did not participate in building the lab.
