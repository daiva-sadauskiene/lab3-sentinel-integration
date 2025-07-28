# lab3: Sentinel Configuration, Threat Intelligence, and Incident Investigation

## 🧩 Overview
In this lab, I configured a Log Analytics Workspace, added Microsoft Sentinel, integrated data sources, created analytics rules, and observed how alerts are generated and grouped into incidents.

## ⚙️ Configuration Steps

### 1. Log Analytics Workspace Setup
- Created a workspace: `SentinelLogWorkspace`
- Region: Switzerland North
- Access control: Resource-level (RBAC)
- Connected to Azure Subscription 1
![Log Analytics Workspace](images/log-analytics-workspace.png)
### 2. Added Microsoft Sentinel
- Enabled Microsoft Sentinel on the Log Analytics workspace
- Confirmed that Sentinel is running with no operational issues

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

### 4. 🔔 Alert Rule Configuration

Configured multiple **Analytics rules**, including:
- Failed logon attempts anomaly (NRT)
- Impossible travel detection (scheduled)
- Advanced Multistage Attack Detection (Fusion)

### Analytics Rule: `Failed logon attempts anomaly`
- **Type:** Near Real-Time (NRT)
- ⏱ I used NRT rules to simulate real SOC scenarios and reduce detection delay
- **Severity:** Medium
- **Detection method:** Custom KQL query on `SecurityEvent` (EventID = 4625)
- **Purpose:** Detect brute-force or repeated failed login attempts

## 🚨 Alerting & Incident Investigation
- Alerts triggered by the rules were automatically grouped into incidents in Sentinel.
- All incidents in this case were related to suspicious failed login attempts.
- Investigated incident severity and source within Sentinel > Incidents.
- Demonstrated use of analytics rules and MITRE ATT&CK mapping.

## 🎯 Key Learning Outcomes
- How to configure Sentinel from scratch
- Real-time alert rule creation and tuning
- Incident investigation in a SOC-like environment
- How Sentinel helps monitor, detect, and respond to security threats

## 🖼️ Screenshots
	1. SentinelLogWorkspace overview 
	2. Active analytics rules in Sentinel 
	3. Triggered incidents based on failed logon attempts 
	4. Rule query configuration (KQL)

## 🔒 Why this matters
This lab demonstrates the ability to:
- Configure and operate Microsoft Sentinel
- Create custom alert rules using KQL
- Investigate alerts and incidents
- Understand and simulate SOC workflows



