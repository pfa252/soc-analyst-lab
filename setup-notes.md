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

## Sysmon Installation and Validation

Sysmon was installed on the Windows 11 lab endpoint to provide enhanced endpoint telemetry.

Configured endpoint:

```text
Hostname: SOC-WIN11-01
Operating System: Windows 11
Purpose: Enhanced endpoint telemetry source
```

Sysmon installation path:

```text
C:\SOC-Lab\Sysmon
```

Sysmon event log:

```text
Microsoft-Windows-Sysmon/Operational
```

Validation results:

```text
Sysmon Service: Running
Recent Sysmon events confirmed
```

Observed Sysmon event IDs:

```text
Event ID 1  - Process creation
Event ID 4  - Sysmon service state changed
Event ID 11 - File created
Event ID 13 - Registry value set
```

Reason for installing Sysmon:

Sysmon provides detailed endpoint visibility beyond standard Windows event logs. This includes process creation, parent-child process relationships, file creation, registry activity, and other endpoint behavior useful for detection engineering and incident response.

Detection scenarios supported by Sysmon:

```text
Suspicious process creation
PowerShell child process activity
Command shell execution
Suspicious file creation
Registry modification activity
Potential persistence activity
Malware-like behavior patterns
```

Security note:

Sysmon was installed only on the isolated lab virtual machine. No production systems or employer devices were modified.

## Azure Log Analytics and Microsoft Sentinel Setup

Created the Azure resources required for the SOC Analyst Lab SIEM environment.

Resource group:

```text
rg-soc-analyst-lab
```

Log Analytics workspace:

```text
law-soc-analyst-lab
```

Region:

```text
Central US
```

Microsoft Sentinel was enabled on the Log Analytics workspace.

Cost-control configuration:

```text
Daily cap: 0.5 GB/day
Purpose: Prevent unexpected ingestion growth during lab testing
```

Purpose:

The Log Analytics workspace will store security telemetry collected from the lab endpoint. Microsoft Sentinel will be used as the SIEM for detection engineering, KQL hunting, incident creation, and investigation workflows.

Security note:

This Azure environment is used only for lab-generated telemetry. No employer, customer, production, or confidential data is connected to this workspace.


## Azure Arc Onboarding

The Windows 11 lab endpoint was onboarded to Azure Arc so it can be managed as an Azure-connected machine and used with Azure Monitor Agent.

Onboarded machine:

```text
Hostname: SOC-WIN11-01
Azure Resource Type: Azure Arc-enabled machine
Resource Group: rg-soc-analyst-lab
Region: Central US
Connectivity Method: Public endpoint
```

Purpose:

Azure Arc allows the local Hyper-V lab VM to be managed from Azure even though it is not hosted in Azure. This enables the use of Azure Monitor Agent, Data Collection Rules, and Microsoft Sentinel log ingestion.

Initial issue encountered:

```text
PowerShell execution policy blocked the downloaded Azure Connected Machine Agent installer script.
```

Resolution:

```text
Used a temporary process-scoped PowerShell execution policy bypass.
```

Command used:

```powershell
Set-ExecutionPolicy -ExecutionPolicy Bypass -Scope Process -Force
```

Validation performed:

```text
Confirmed SOC-WIN11-01 appeared under Azure Arc machines.
Confirmed the machine was visible in the rg-soc-analyst-lab resource group.
```

Security note:

Only the isolated lab virtual machine was onboarded to Azure Arc. No production systems, employer devices, or confidential data sources were connected.
