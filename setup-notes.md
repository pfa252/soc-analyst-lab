# Setup Notes

## Phase 1: Repository Setup

Created the initial GitHub repository for the SOC Analyst Lab.

Repository name:

```text
soc-analyst-lab
```

Initial folders created:

```text
diagrams/
screenshots/
kql/
incident-reports/
notes/
```

Initial documentation files created:

```text
README.md
lab-architecture.md
setup-notes.md
```

## Phase 2: Planned Lab Build

The next phase is to build the actual lab environment.

Planned build steps:

1. Create or identify a Windows 11 lab machine
2. Enable advanced Windows logging
3. Install and configure Sysmon
4. Create an Azure Log Analytics Workspace
5. Enable Microsoft Sentinel
6. Connect Windows endpoint logs to the workspace
7. Connect Microsoft Defender for Endpoint, if available
8. Run safe test activity
9. Write KQL detections
10. Document incident investigations

## Change Log

| Date       | Change                                               |
| ---------- | ---------------------------------------------------- |
| 2026-06-28 | Created initial SOC Analyst Lab repository structure |

## Windows 11 Lab VM Baseline

The Windows 11 lab endpoint was successfully installed and configured.

VM baseline details:

```text
VM Name: SOC-WIN11-01
Operating System: Windows 11
Virtualization Platform: Hyper-V
Primary Admin Account: socadmin
Standard Test Account: testuser
Network: Default Switch
```

Local accounts:

```text
socadmin - Local administrator account used for lab administration
testuser - Standard local user account used to generate test activity
```

A baseline checkpoint was created after the Windows installation and initial account setup.

Checkpoint name:

```text
Baseline-Windows-Installed
```

Purpose:

This checkpoint provides a clean restore point before enabling advanced logging, installing Sysmon, forwarding logs to Microsoft Sentinel, or generating simulated security events.
