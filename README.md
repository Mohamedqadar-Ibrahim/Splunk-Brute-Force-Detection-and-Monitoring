# Brute-Force Detection and Monitoring in Splunk

## 🔐 Project Overview
A practical Security Information and Event Management (SIEM) implementation demonstrating brute-force attack detection using Splunk. This project showcases fundamental SOC analyst skills including log analysis, alert configuration, and incident response capabilities.

![Initial Splunk Dashboard](screenshots/Splunk%20Screenshot%201.PNG)
*Initial Splunk environment showing the search interface and key monitoring panels*

## 🎯 Key Features
- **Real-Time Detection Engine**: Custom-configured queries to identify suspicious login patterns
- **SOC Dashboard**: Purpose-built visualization for security monitoring
- **Alert System**: Automated notification system for potential threats
- **MITRE ATT&CK Integration**: Aligned with T1110.001 (Password Guessing)

## 🛠 Technical Implementation

### Detection Logic
```splunk
index=_audit action="login attempt" info="failed"
| stats count by user, src
| where count > 1
```

![Audit Log Query](screenshots/Splunk%20Screenshot%202.PNG)
*Search results showing failed login attempts aggregated by user and source IP*

### Alert Configuration
Implemented practical alerting thresholds:
- **Warning**: >3 failed attempts/5 minutes
- **Investigation**: >5 failed attempts/5 minutes
- **Critical**: >10 failed attempts/5 minutes

![Alert Configuration](screenshots/Splunk%20Screenshot%207.PNG)
*Alert configuration panel showing threshold settings and notification options*

### Dashboard Components
![Threat Detection Dashboard](screenshots/Splunk%20Screenshot%203.PNG)
*Custom dashboard showing real-time login activity monitoring*

Key Panels Include:
1. Failed Login Counter
2. Login Activity Timeline
3. Source IP Distribution
4. Account Impact Assessment

![Login Activity Timechart](screenshots/Splunk%20Screenshot%205.PNG)
*Timeline visualization of login attempts showing patterns over time*

## 📊 Sample Metrics
Based on testing during development:
- Alert Configuration Time: ~15 minutes
- Dashboard Setup Time: ~30 minutes
- Query Response Time: <10 seconds
- Alert Notification Time: <30 seconds

## 🏗 Architecture Details

### Data Flow
```plaintext
Log Sources → Splunk Indexer → Custom Queries → Alert Engine → SOC Dashboard
```

![Dashboard with Data Sources](screenshots/Splunk%20Screenshot%206.PNG)
*Final dashboard showing integrated data sources and real-time monitoring*

### System Components
1. **Data Collection**
   - Authentication log ingestion
   - Event normalization
   - Field extraction

2. **Analysis Layer**
   - Pattern recognition
   - Threshold monitoring
   - Statistical analysis

3. **Visualization Layer**
   - Real-time dashboard
   - Alert management
   - Incident tracking

## 🔄 Testing & Validation

### Simulation Results
![Failed Login Simulation](screenshots/Splunk%20Screenshot%208.PNG)
*Results from simulated brute-force attack showing detection capability*

### Alert Verification
![Triggered Alert](screenshots/Splunk%20Screenshot%209.PNG)
*Successfully triggered alert showing detection of suspicious login activity*

## 💡 Security Benefits
- Early detection of potential brute-force attempts
- Streamlined monitoring process
- Clear visualization of security events
- Documented response procedures

## 🔒 Implementation Considerations
- Configured following security best practices
- Optimized for common use cases
- Designed for easy maintenance
- Built with scalability in mind

## 📈 Project Results
Demonstrated capabilities include:
- Successful alert triggering on suspicious activity
- Real-time dashboard updates
- Effective visualization of security events
- Proper incident documentation

![Dashboard with Results](screenshots/Splunk%20Screenshot%2010.PNG)
*Dashboard showing actual detection results from testing*

## 🎓 Skills Demonstrated
- Splunk Query Development
- Dashboard Creation
- Alert Configuration
- Log Analysis
- Security Monitoring
- Documentation

## 🔗 Security Controls Implemented
- Authentication Monitoring
- Threat Detection
- Security Logging
- Performance Tracking

## 📝 Future Enhancements
1. Additional correlation rules
2. Expanded dashboard metrics
3. Enhanced alert conditions
4. Additional data source integration

## 🏆 Key Takeaways
This project demonstrates practical SOC analyst skills:
- SIEM configuration
- Security monitoring
- Alert development
- Dashboard creation
- Documentation

## 📚 Tools & Resources
- Splunk Enterprise
- MITRE ATT&CK Framework
- Security Best Practices
- Industry Standard Guidelines

## 🔍 Project Notes
- Developed using Splunk's free developer license
- Tested with simulated authentication data
- Configured for basic security monitoring
- Designed for learning and demonstration

## 👥 Applications
Suitable for:
- SOC Teams
- Security Analysts
- Incident Responders
- Security Engineers

---
*Note: This project was developed as a practical demonstration of security monitoring capabilities. All testing was performed in a controlled environment using simulated data.*
