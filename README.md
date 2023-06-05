# Cloud-SOC-Honeynet

# Building a SOC + Honeynet in Azure (Live Traffic)
![Cloud Honeynet / SOC](https://i.imgur.com/ZWxe03e.jpg)

## Introduction

In this project, a mini honeynet was constructed in Microsoft Azure to create a secure environment for monitoring and analyzing security events. The architecture consisted of various components, including a Virtual Network, Network Security Group, Virtual Machines, Log Analytics Workspace, Azure Key Vault, Azure Storage Account, and Microsoft Sentinel. Initially, the environment was insecure, with resources exposed to the internet and minimal restrictions on access. The metrics we will show are:

- AzureNetworkAnalytics_CL (Malicious Flows allowed into our honeynet)
- SecurityEvent (Windows Event Logs)
- SecurityAlert (Log Analytics Alerts Triggered)
- SecurityIncident (Incidents created by Sentinel)
- Syslog (Linux Event Logs)

## Architecture Before Hardening / Security Controls
![Architecture Diagram](https://i.imgur.com/aBDwnKb.jpg)

## Architecture After Hardening / Security Controls
![Architecture Diagram](https://i.imgur.com/YQNa9Pp.jpg)

The architecture of the mini honeynet in Azure consists of the following components:

Log Analytics Workspace
Microsoft Sentinel
Azure Storage Account
Network Security Group (NSG)
Virtual Machines (2 windows, 1 Linux)
Azure Key Vault
Virtual Network (VNet)

Before implementing security controls, metrics were measured for a 24-hour period. These metrics included SecurityEvent (Windows Event Logs), Syslog (Linux Event Logs), SecurityAlert (Log Analytics Alerts Triggered), SecurityIncident (Incidents created by Sentinel), and AzureNetworkAnalytics_CL (Malicious Flows allowed into the honeynet). The results indicated a relatively high number of security events, alerts, incidents, and malicious flows, highlighting the vulnerabilities in the environment.

To address these security risks, security controls were applied to harden the environment. Network Security Groups were configured to block all traffic except for the admin workstation, and built-in firewalls and Private Endpoints were utilized for resource protection. After implementing these measures, the metrics were measured again for another 24-hour period.


## Attack Maps Before Hardening / Security Controls
![NSG Allowed Inbound Malicious Flows](https://i.imgur.com/1qvswSX.png)<br>
![Linux Syslog Auth Failures](https://i.imgur.com/G1YgZt6.png)<br>
![Windows RDP/SMB Auth Failures](https://i.imgur.com/ESr9Dlv.png)<br>

## Metrics Before Hardening / Security Controls

The following table shows the metrics we measured in our insecure environment for 24 hours:
Start Time 5/31/2023 8:23:11 AM
Stop Time 6/1/2023 8:23:11 AM

| Metric                   | Count
| ------------------------ | -----
| SecurityEvent            | 13559
| Syslog                   | 72
| SecurityAlert            | 1003
| SecurityIncident         | 2725
| AzureNetworkAnalytics_CL | 5610

## Attack Maps Before Hardening / Security Controls

```All map queries actually returned no results due to no instances of malicious activity for the 24 hour period after hardening.```

## Metrics After Hardening / Security Controls

The following table shows the metrics we measured in our environment for another 24 hours, but after we have applied security controls:
Start Time 6/4/2023 10:16:12 AM
Stop Time	6/5/2023 10:16:12 AM

| Metric                   | Count
| ------------------------ | -----
| SecurityEvent            | 5070
| Syslog                   | 24
| SecurityAlert            | 0
| SecurityIncident         | 0
| AzureNetworkAnalytics_CL | 0

## Conclusion

The results post-implementation showed a significant reduction in security events, syslog entries, alerts triggered, incidents created, and malicious flows allowed. These improvements demonstrated the effectiveness of the applied security controls in mitigating security risks and enhancing the overall security posture of the honeynet environment. By leveraging Azure's capabilities, such as Log Analytics and Sentinel, this project successfully showcased the value of proactive security measures in safeguarding the Azure infrastructure.

If the network resources were heavily utilized by regular users, it is important to consider that implementing the security controls might have resulted in an increased number of security events and alerts during the 24-hour period.

