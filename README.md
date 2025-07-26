# Security Monitoring Dashboard (Hackathon)

A real-time security dashboard integrating Azure Sentinel and Power BI to visualize threat activity and security metrics.

## 🎯 Project Overview
This hackathon project demonstrates how to build an enterprise-grade security monitoring solution using Microsoft's cloud security stack. The dashboard provides real-time insights into security threats, failed authentication attempts, network anomalies, and malware detections.

## 🛠️ Technologies
- **Azure Sentinel**: Cloud-native SIEM solution
- **Log Analytics**: Data collection and querying engine  
- **Power BI**: Business intelligence and visualization platform
- **KQL (Kusto Query Language)**: Query language for log analysis

## 📊 Dashboard Features
- **Security Overview**: High-level security posture and KPIs
- **Network Security**: Failed sign-ins, traffic anomalies, and IP analysis
- **Threat Analysis**: Malware detections and suspicious activities
- **Incident Response**: Active incidents and response metrics

## 🏗️ Project Structure
```
azure-sentinel-power-bi-dashboard/
├── log-analytics-queries/          # Sample KQL queries
│   ├── top-10-alerts.kql
│   ├── failed-signins.kql
│   ├── network-anomalies.kql
│   ├── malware-detections.kql
│   ├── suspicious-powershell.kql
│   ├── privilege-escalation.kql
│   └── data-exfiltration.kql
├── powerbi-template/               # Power BI setup and templates
│   ├── instructions.md
│   ├── dashboard-template-guide.md
│   └── deployment-guide.md
└── README.md
```

## 🚀 Quick Start
1. **Set up Azure Sentinel**: Configure your Log Analytics workspace
2. **Review sample queries**: Explore the KQL queries in `log-analytics-queries/`
3. **Connect Power BI**: Follow instructions in `powerbi-template/instructions.md`
4. **Build dashboards**: Use the template guide to create visualizations
5. **Deploy**: Follow the deployment guide for production setup

## 📋 Prerequisites
- Azure subscription with Sentinel enabled
- Power BI Pro or Premium license
- Log Analytics workspace with security data
- Appropriate Azure permissions (Log Analytics Reader minimum)

## 🔧 Setup Instructions
Detailed setup instructions are available in:
- [`powerbi-template/instructions.md`](powerbi-template/instructions.md) - Connection and basic setup
- [`powerbi-template/deployment-guide.md`](powerbi-template/deployment-guide.md) - Production deployment
- [`powerbi-template/dashboard-template-guide.md`](powerbi-template/dashboard-template-guide.md) - Dashboard design

## 📈 Sample Visualizations
The dashboard includes:
- **Security Score Gauge**: Real-time security posture metric
- **Alert Distribution**: Breakdown by severity levels
- **Geographic Threat Map**: Failed sign-ins by location
- **Trend Analysis**: Security incidents over time
- **Top Threats Table**: Most frequent security alerts

## 🔍 Key Queries
| Query | Purpose | Data Source |
|-------|---------|-------------|
| `top-10-alerts.kql` | Most frequent security alerts | SecurityAlert |
| `failed-signins.kql` | Authentication failures by location | SigninLogs |
| `network-anomalies.kql` | Unusual network traffic patterns | CommonSecurityLog |
| `malware-detections.kql` | Malware detection trends | SecurityEvent |
| `suspicious-powershell.kql` | PowerShell-based attacks | SecurityEvent |

## 🎨 Dashboard Color Scheme
- **Critical**: #FF4444 (Red)
- **High**: #FF8800 (Orange)  
- **Medium**: #FFCC00 (Yellow)
- **Low**: #00AA44 (Green)
- **Info**: #0088CC (Blue)

## 🔄 Refresh Schedule
- **Real-time data**: Every 15 minutes
- **Historical reports**: Daily
- **Trend analysis**: Weekly

## 🤝 Contributing
This is a hackathon project template. Feel free to:
- Add more KQL queries for different threat scenarios
- Enhance Power BI visualizations
- Improve documentation and setup guides
- Add automation scripts

## 📚 Resources
- [Azure Sentinel Documentation](https://docs.microsoft.com/azure/sentinel/)
- [Power BI Documentation](https://docs.microsoft.com/power-bi/)
- [KQL Reference](https://docs.microsoft.com/azure/data-explorer/kql-quick-reference)
- [Security Best Practices](https://docs.microsoft.com/security/)

## 📧 Support
For questions or issues:
1. Review the troubleshooting section in the deployment guide
2. Check Azure Sentinel logs for data connectivity issues
3. Validate Power BI refresh logs for dashboard problems

---
**🏆 Hackathon Project**: Built to demonstrate real-world security monitoring capabilities using Microsoft's cloud security platform.
#
