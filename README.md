# lab3: Sentinel Configuration, Threat Intelligence, and Incident Investigation

## 🧩 Overview
In this lab, I configured a Log Analytics Workspace, added Microsoft Sentinel, integrated data sources, created analytics rules, and observed how alerts are generated and grouped into incidents.

## ⚙️ Configuration Steps

### 1. Log Analytics Workspace Setup
- Created a workspace: `SentinelLogWorkspace`
- Region: Switzerland North
- Access control: Resource-level (RBAC)
- Connected to Azure Subscription 1

  *This screenshot shows the Log Analytics Workspace created for Microsoft Sentinel.*
- ![Log Analytics Workspace](log-analytics-workspace.png)

### 2. Added Microsoft Sentinel
- Enabled Microsoft Sentinel on the Log Analytics workspace
- Confirmed that Sentinel is running with no operational issues
![Sentinel Overview](sentinel-enabled.png)

### 3. Data Connectors and Threat Intelligence

### Connected Data Sources:
- Azure Virtual Machine
- Connected via **Windows Security Events via AMA**

### Threat Intelligence (TAXII Connector):
- Enabled **Threat Intelligence – TAXII** data connector
- Connected **Pulsedive threat feed**
- Imported ~29,000+ IOCs (IP addresses, domains)
- Source visible in: **Sentinel > Threat Intelligence > Source: pulsefeed**

> Note: TAXII connector allows Microsoft Sentinel to receive real-time threat indicators from trusted open source feeds like Pulsedive.
![Pulsefeed Threat Intelligence](pulsefeed.png)

### 4. 🔔 Alert Rule Configuration

Configured multiple **Analytics rules**, including:
- Failed logon attempts anomaly (NRT)
- Impossible travel detection (scheduled)
- Advanced Multistage Attack Detection (Fusion)
![Analytics Rules](analytics-rules.png)

### Analytics Rule: `Failed logon attempts anomaly`
- **Type:** Near Real-Time (NRT)
- ⏱ I used NRT rules to simulate real SOC scenarios and reduce detection delay
- **Severity:** Medium
- **Detection method:** Custom KQL query on `SecurityEvent` (EventID = 4625)
- **Purpose:** Detect brute-force or repeated failed login attempts
![KQL Rule Query](rule-query.png)
![Failed Logon Incident](sentinel-failed-logon-attempt.png)

## 🚨 Alerting & Incident Investigation
- Alerts triggered by the rules were automatically grouped into incidents in Sentinel.
- All incidents in this case were related to suspicious failed login attempts.
- Investigated incident severity and source within Sentinel > Incidents.
- Demonstrated use of analytics rules and MITRE ATT&CK mapping.
![Sentinel Incidents](sentinel-incidents.png)

## 🎯 Key Learning Outcomes
- How to configure Sentinel from scratch
- Real-time alert rule creation and tuning
- Incident investigation in a SOC-like environment
- How Sentinel helps monitor, detect, and respond to security threats

## 🖼️ Screenshots  
*The screenshots illustrate the process of configuring Microsoft Sentinel, including setting up a Log Analytics Workspace, enabling Sentinel, connecting the TAXII threat intelligence feed, creating custom analytics rules, and reviewing generated incidents based on simulated failed logon attempts.*

## 🔒 Skills Demonstrated
- Microsoft Sentinel configuration from scratch
- TAXII Threat Intelligence integration (Pulsedive)
- Creation of custom analytics rules using KQL
- SOC-style alert investigation and incident management
- Understanding of MITRE ATT&CK mapping in Sentinel

