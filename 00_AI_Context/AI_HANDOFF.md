AI Handoff — Network Security Home Lab
Purpose

This file is intended to help any AI assistant continue the Network Security Home Lab project if the current conversation becomes unavailable because of a usage limit, technical issue, or any other interruption.

The project must be continued from the documented state.

Do not restart the project from the beginning.

Project Identity

Project name:

Network Security Home Lab

Project location:

D:\Network_Security_Home_Lab

Primary goal:

Build a realistic, practical, reproducible Network Security Home Lab suitable for learning, technical documentation, and portfolio presentation.

Current State

The project is currently in the initial documentation and Git setup phase.

Completed:

Project folder created
Project structure created
Project documentation files created
00_AI_Context/ created
PROJECT_CONTEXT.md created
CURRENT_STATUS.md created
Git initialized
.gitignore created
Project files staged
Git identity configured
Branch renamed from master to main

Not completed:

Initial Git commit
GitHub remote
GitHub push
Virtual machines
pfSense
VLANs
Windows Client
Ubuntu Server
Wireshark
Suricata
Wazuh
Security scenarios
Planned Architecture
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
                    Suricata
                    Wazuh
Planned Security Workflow
Network Design
      ↓
Segmentation
      ↓
Firewall Policies
      ↓
Connectivity Testing
      ↓
Traffic Analysis
      ↓
IDS/IPS
      ↓
SIEM
      ↓
Detection
      ↓
Investigation
      ↓
Documentation
Roadmap
Project and Lab Design
Virtual Lab Setup
pfSense Firewall
VLANs and Network Segmentation
Windows Client and Ubuntu Server
Firewall Policies and Connectivity Testing
Wireshark Traffic Analysis
Suricata IDS/IPS
Wazuh SIEM and Monitoring
Defensive Detection and Investigation Scenarios
Documentation and Portfolio Presentation
Rules for Continuing the Project
1. Preserve the Architecture

Do not replace the planned architecture or major tools without a clear technical reason.

2. Preserve the Roadmap

Do not randomly skip phases.

If a better technical approach is discovered, explain the reason before changing the plan.

3. One Step at a Time

The user prefers controlled step-by-step execution.

For important operations:

Explain what will happen
Explain why
Give the command/action
Wait for the result
Verify the result
Continue only after verification
4. Git Is the Source of Truth

Use the Git repository and project documentation to determine the actual project state.

Do not assume that something has been completed because an AI conversation says it was completed.

5. Do Not Pretend Something Was Tested

If a command, configuration, VM, network rule, or security tool has not actually been tested, do not describe it as working.

6. Document Important Changes

When a meaningful configuration or troubleshooting event occurs, update the appropriate project documentation.

Relevant locations include:

04_Progress/
05_Commands/
06_Configurations/
07_Troubleshooting/
08_Screenshots/
10_Project_Journal/
7. Portfolio Quality

The objective is not merely to install security software.

The final project should demonstrate understanding of:

Network architecture
Segmentation
Firewall policy design
Traffic analysis
IDS/IPS
SIEM
Log analysis
Detection
Investigation
Troubleshooting
Documentation
What the New AI Should Do First

If continuing this project from a new conversation:

Read 00_AI_Context/PROJECT_CONTEXT.md
Read 00_AI_Context/CURRENT_STATUS.md
Read 00_AI_Context/AI_HANDOFF.md
Check the actual Git status
Compare the repository state with the documented status
Continue from the first incomplete step

Do not immediately start installing software.

Current Immediate Task

The three AI context files have been created.

The next action is:

Review Git status
      ↓
Add 00_AI_Context/
      ↓
Review staged files
      ↓
Create initial commit

Only after the initial commit should the project move toward GitHub and the actual virtual lab.

Final Principle

The AI is an assistant and technical mentor.

The project belongs to the user.

The AI should explain decisions, preserve continuity, verify actual results, and help the user understand what is being built rather than blindly executing commands.