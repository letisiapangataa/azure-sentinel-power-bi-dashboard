# Power BI Dashboard Template Guide

## Dashboard Pages Overview

### 1. Security Overview
**Purpose**: High-level security posture and key metrics
**Visuals**:
- Security Score (Gauge)
- Total Incidents (Card)
- Critical Alerts (Card)  
- Alert Severity Distribution (Donut Chart)
- Security Trends (Line Chart)

### 2. Network Security
**Purpose**: Network-related threats and anomalies
**Visuals**:
- Failed Sign-ins by Location (Map)
- Network Traffic Anomalies (Area Chart)
- Top Suspicious IPs (Table)
- Data Exfiltration Attempts (Matrix)

### 3. Threat Analysis  
**Purpose**: Detailed threat intelligence and malware analysis
**Visuals**:
- Malware Detections by Type (Column Chart)
- PowerShell Suspicious Activity (Treemap)
- Privilege Escalation Risk (Gauge)
- Threat Timeline (Gantt Chart)

### 4. Incident Response
**Purpose**: Active incidents and response metrics
**Visuals**:
- Open Incidents (Table)
- Response Time Metrics (KPI)
- Incident Status Distribution (Pie Chart)
- Assignment Workload (Bar Chart)

## Color Scheme
- **Critical**: #FF4444 (Red)
- **High**: #FF8800 (Orange)  
- **Medium**: #FFCC00 (Yellow)
- **Low**: #00AA44 (Green)
- **Info**: #0088CC (Blue)

## Sample Measures (DAX)
```dax
Security Score = 
100 - (
    COUNTROWS(FILTER(SecurityAlert, SecurityAlert[AlertSeverity] = "Critical")) * 10 +
    COUNTROWS(FILTER(SecurityAlert, SecurityAlert[AlertSeverity] = "High")) * 5 +
    COUNTROWS(FILTER(SecurityAlert, SecurityAlert[AlertSeverity] = "Medium")) * 2 +
    COUNTROWS(FILTER(SecurityAlert, SecurityAlert[AlertSeverity] = "Low")) * 1
)
```

```dax
Risk Level = 
SWITCH(
    TRUE(),
    [Security Score] >= 90, "Low Risk",
    [Security Score] >= 70, "Medium Risk", 
    [Security Score] >= 50, "High Risk",
    "Critical Risk"
)
```

## Filters and Slicers
- Time Range (Last 24h, 7d, 30d)
- Severity Level
- Alert Type
- Computer/Device
- User Account

## Refresh Schedule
- **Real-time**: Every 15 minutes
- **Historical**: Daily at 2 AM
- **Reports**: Weekly on Mondays
