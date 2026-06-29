# Lab Architecture

## Purpose

This document describes the planned architecture for the SOC Analyst Lab.

The lab is designed to simulate a small security operations environment where endpoint telemetry is collected, forwarded to a SIEM, queried using KQL, and investigated through incident response workflows.

## Planned Architecture

```text
Windows 11 Lab Endpoint
        |
        | Security Events, Sysmon Events, Defender Telemetry
        v
Azure Log Analytics Workspace
        |
        v
Microsoft Sentinel
        |
        v
KQL Queries, Analytics Rules, Workbooks, Incidents
```

## Core Components

### Windows 11 Lab Endpoint

The Windows 11 endpoint will act as the primary test device. It will generate security events such as logons, process execution, PowerShell activity, and account changes.

### Sysmon

Sysmon will be used to collect detailed endpoint telemetry, including process creation, network connections, file creation, and other security-relevant activity.

### Log Analytics Workspace

The Log Analytics Workspace will store collected logs and make them available for querying.

### Microsoft Sentinel

Microsoft Sentinel will act as the SIEM. It will be used for log analysis, detection rules, incident generation, and threat hunting.

### Microsoft Defender for Endpoint

Microsoft Defender for Endpoint will provide endpoint detection and response visibility, including alerts, device timeline data, and investigation context.

## Data Sources

Planned data sources include:

* Windows Security Event Logs
* Sysmon Operational Logs
* Microsoft Defender for Endpoint alerts
* Microsoft Sentinel incidents
* Azure Activity Logs, if applicable

## Initial Detection Scenarios

The first detection scenarios will include:

1. Multiple failed logons
2. Successful logon after repeated failures
3. Suspicious PowerShell execution
4. Encoded PowerShell commands
5. Creation of a new local administrator account

## Security and Privacy Notes

This lab must not include production data, company screenshots, real user information, real customer information, public IP addresses from an employer network, or any confidential configuration details.
