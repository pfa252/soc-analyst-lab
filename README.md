# SOC Analyst Lab

## Overview

This project documents the buildout of a hands-on SOC Analyst Lab designed to practice security monitoring, endpoint telemetry collection, KQL detection engineering, and incident response workflows.

The lab focuses on blue-team skills using Microsoft security tools, including Microsoft Sentinel, Microsoft Defender for Endpoint, Windows event logs, Sysmon, and KQL.

## Project Goals

The goals of this project are to:

* Build a small but realistic SOC lab environment
* Collect security telemetry from Windows endpoints
* Forward logs into a SIEM
* Write KQL detections for suspicious activity
* Simulate common attacker behaviors in a safe lab environment
* Investigate alerts using a repeatable incident response process
* Document findings in professional incident report format

## Lab Components

Planned components include:

* Windows 11 lab endpoint
* Microsoft Sentinel
* Azure Log Analytics Workspace
* Microsoft Defender for Endpoint
* Sysmon
* Windows Security Event Logs
* KQL detection queries
* Incident response reports

## Skills Demonstrated

This project demonstrates:

* SIEM setup and configuration
* Endpoint detection and response concepts
* Windows log analysis
* Microsoft Sentinel usage
* KQL query writing
* Threat hunting
* Alert triage
* Incident documentation
* MITRE ATT&CK mapping
* Security operations workflow

## Planned Detection Use Cases

This lab will include detections for:

* Failed logon activity
* Brute-force behavior
* Successful logon after repeated failures
* Suspicious PowerShell usage
* Encoded PowerShell commands
* Local administrator account changes
* Suspicious process execution
* Defender security alerts

## Repository Structure

```text
soc-analyst-lab/
│
├── README.md
├── lab-architecture.md
├── setup-notes.md
│
├── diagrams/
├── screenshots/
├── kql/
├── incident-reports/
└── notes/
```

## Status

Project status: In progress

Current phase: Initial lab planning and repository setup

## Important Note

This lab uses only test systems, lab-generated telemetry, and sanitized documentation. No employer, customer, or production data is included in this repository.
