# Connect Power BI to Azure Sentinel (Log Analytics)

## Prerequisites
- Power BI Desktop installed
- Access to Azure Sentinel workspace
- Log Analytics Workspace ID and authentication

## Setup Instructions

### Step 1: Get Azure Credentials
1. Go to Azure Portal > Log Analytics Workspace
2. Navigate to **Agents Management**
3. Copy your **Workspace ID** and **Primary Key**

### Step 2: Connect Power BI to Log Analytics
1. Open Power BI Desktop
2. Click **Get Data** > **Azure** > **Azure Log Analytics (Beta)**
3. Enter your Log Analytics Workspace ID
4. Choose authentication method (Key or Azure AD)
5. If using Key, enter your Primary Key

### Step 3: Import Queries
1. Paste KQL queries from `../log-analytics-queries/`
2. Test the query in the query editor
3. Click **Load** to import data

### Step 4: Build Dashboard Visuals
Create the following visualizations:

#### Security Overview Page
- **Card Visuals**: Total alerts, failed sign-ins, malware detections
- **Donut Chart**: Alerts by severity (Critical, High, Medium, Low)
- **Bar Chart**: Top 10 alert types
- **Line Chart**: Security incidents over time (last 30 days)

#### Network Security Page  
- **Map Visual**: Failed sign-ins by location
- **Table**: Top suspicious IP addresses
- **Area Chart**: Network traffic anomalies over time
- **Matrix**: Data exfiltration attempts by user

#### Threat Analysis Page
- **Clustered Column Chart**: Malware detections by type
- **Treemap**: PowerShell suspicious activity by computer
- **Gauge**: Privilege escalation risk score
- **Waterfall Chart**: Monthly security incident trends

## Dashboard Template Structure
```
Security Monitoring Dashboard
├── Page 1: Security Overview
├── Page 2: Network Security  
├── Page 3: Threat Analysis
└── Page 4: Incident Response
```

## Sample Dashboard Queries
Use these optimized queries for Power BI:

### Real-time Security Score
```kql
let TotalAlerts = SecurityAlert | count;
let CriticalAlerts = SecurityAlert | where AlertSeverity == "Critical" | count;
let HighAlerts = SecurityAlert | where AlertSeverity == "High" | count;
SecurityAlert
| summarize 
    Total = count(),
    Critical = countif(AlertSeverity == "Critical"),
    High = countif(AlertSeverity == "High"),
    Medium = countif(AlertSeverity == "Medium"),
    Low = countif(AlertSeverity == "Low")
| extend SecurityScore = 100 - ((Critical * 10) + (High * 5) + (Medium * 2) + (Low * 1))
```

### Threat Timeline
```kql
union SecurityAlert, SecurityEvent, SigninLogs
| where TimeGenerated >= ago(7d)
| summarize Events = count() by EventType = case(
    Type == "SecurityAlert", "Security Alert",
    Type == "SecurityEvent", "Security Event", 
    Type == "SigninLogs", "Sign-in Event",
    "Other"
), bin(TimeGenerated, 1h)
| order by TimeGenerated desc
```

## Refresh Settings
- Set up automatic refresh every 15 minutes for real-time monitoring
- Configure incremental refresh for historical data
- Use DirectQuery for live connections when possible

## Tips for Optimization
- Use time filters to limit data volume
- Create calculated columns for commonly used metrics
- Set up alerts for critical thresholds
- Use bookmarks for different security scenarios
