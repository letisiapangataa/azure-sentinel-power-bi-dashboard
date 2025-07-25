# Azure Sentinel Security Dashboard Deployment Guide

## Prerequisites Checklist
- [ ] Azure Subscription with appropriate permissions
- [ ] Azure Sentinel workspace configured  
- [ ] Log Analytics workspace connected
- [ ] Power BI Pro or Premium license
- [ ] Network access to Azure from Power BI

## Azure Setup

### 1. Configure Azure Sentinel Data Connectors
Enable these connectors in Azure Sentinel:
- Azure Active Directory Sign-ins
- Azure Activity  
- Security Events via Legacy Agent
- Common Event Format (CEF)
- Microsoft Defender for Endpoint

### 2. Set Up Analytics Rules
Create detection rules for:
- Multiple failed sign-in attempts
- Suspicious PowerShell execution
- Privilege escalation attempts
- Data exfiltration patterns
- Malware detections

### 3. Configure Log Analytics Retention
- Set retention period to 90+ days for trend analysis
- Configure data export if needed for long-term storage

## Power BI Setup

### 1. Install Required Components
```powershell
# Install Power BI Desktop (if not already installed)
winget install Microsoft.PowerBI
```

### 2. Create Service Principal (Recommended)
For automated refresh, create an Azure AD App Registration:
1. Go to Azure AD > App Registrations
2. Create new registration
3. Grant Log Analytics Reader permissions
4. Note Application ID and create client secret

### 3. Configure Gateway (if needed)
For on-premises data sources or enhanced security:
- Install Power BI Gateway
- Configure Azure AD authentication

## Security Considerations

### Data Privacy
- Use Row-Level Security (RLS) in Power BI
- Limit access to sensitive security data
- Implement least privilege access

### Authentication  
- Use Azure AD authentication when possible
- Rotate access keys regularly
- Monitor Power BI access logs

### Compliance
- Ensure data residency requirements are met
- Document data flows for compliance audits
- Implement data retention policies

## Troubleshooting

### Common Connection Issues
1. **Authentication Failed**
   - Verify workspace ID is correct
   - Check if access key is expired
   - Ensure user has Log Analytics Reader role

2. **Query Timeout**  
   - Reduce time range in queries
   - Add filters to limit data volume
   - Use incremental refresh

3. **Data Not Updating**
   - Check refresh schedule settings
   - Verify gateway connectivity (if applicable)
   - Review Power BI service logs

### Performance Optimization
- Use DirectQuery for real-time data
- Implement incremental refresh for historical data  
- Create aggregated tables for dashboards
- Use query folding where possible

## Monitoring and Maintenance

### Regular Tasks
- [ ] Review dashboard performance weekly
- [ ] Update KQL queries based on new threats
- [ ] Validate data accuracy monthly  
- [ ] Review and update security rules quarterly

### Alerts and Notifications
Set up Power BI alerts for:
- Security score drops below threshold
- Critical alert count exceeds limit
- Dashboard refresh failures
- Unusual data patterns

## Cost Optimization
- Use Power BI Embedded for external sharing
- Optimize query complexity to reduce compute costs
- Implement smart caching strategies
- Monitor Log Analytics data ingestion costs
