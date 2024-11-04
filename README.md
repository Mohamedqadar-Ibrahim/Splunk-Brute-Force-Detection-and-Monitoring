# Brute-Force Detection and Monitoring in Splunk

Welcome to this project on brute-force detection using **Splunk**. This project demonstrates how to configure a Splunk environment for detecting and alerting on brute-force login attempts, as well as visualizing these events through a custom dashboard. This hands-on demonstration is essential for understanding how Splunk can be used in Security Operations Center (SOC) environments for real-time threat detection and monitoring.

---

## Table of Contents
- [Introduction](#introduction)
- [Project Goals](#project-goals)
- [Architecture Overview](#architecture-overview)
- [Configuration Steps](#configuration-steps)
- [Screenshots & Visualizations](#screenshots--visualizations)
- [Results & Findings](#results--findings)
- [Reflection & Future Work](#reflection--future-work)
- [Conclusion](#conclusion)

---

## Introduction

Brute-force attacks, where attackers attempt multiple login attempts to gain unauthorized access, are a common security threat. This project simulates such attacks, demonstrates how to set up detection alerts, and visualizes these attempts on a custom Splunk dashboard. By showcasing this setup, we illustrate the process of configuring Splunk to monitor, detect, and alert on suspicious login behavior.

---

## Project Goals

The objectives of this project include:
1. **Simulate** a brute-force attack by generating multiple failed login attempts.
2. **Create a Splunk Dashboard** to visualize login activity and brute-force attempts.
3. **Configure a Splunk Alert** to trigger upon detecting suspicious login behavior.
4. **Test and verify** the alert by observing notifications and dashboard results.

This project provides insight into essential SOC skills, including real-time monitoring, data visualization, and alert configuration.

---

## Architecture Overview

The project is structured into three main components:
1. **Data Source Configuration**: Queries were crafted to capture specific login actions and events in Splunk.
2. **Dashboard Setup**: A custom dashboard was created to visually display login activity and attempted brute-force attacks.
3. **Alert Configuration**: An alert was configured to notify when multiple failed login attempts were detected in real-time.

---

## Configuration Steps

### Step 1: Splunk Environment Setup

1. **Login to Splunk**: Accessed the Splunk dashboard for setup and configuration.  
   ![Screenshot 1 - Splunk Dashboard](screenshots/screenshot1.png)

2. **Initial Query**: Used `index=_audit` to view Splunk logs and analyze key fields related to login attempts.
   ![Screenshot 2 - Initial Query](screenshots/screenshot2.png)

### Step 2: Dashboard Creation

1. **Created a New Dashboard**: Named it "Threat Detection Dashboard" to visualize and track suspicious login activity.
   ![Screenshot 3 - New Dashboard](screenshots/screenshot3.png)

2. **Added Data Sources**:
   - **Brute-Force Detection Panel**: This panel uses the following query to count failed login attempts:
     ```splunk
     index=_audit action="login attempt" info="failed"
     | stats count by user, src
     | where count > 1
     ```
     ![Screenshot 4 - Brute-Force Detection Panel](screenshots/screenshot4.png)

   - **Login Activity Over Time**: Displays login attempts over time to provide context on login patterns.
     ```splunk
     index=_audit action="login attempt" 
     | timechart count by info
     ```
     ![Screenshot 5 - Login Activity Over Time](screenshots/screenshot5.png)

3. **Dashboard View**: Final view showing both data sources, with visual insights into login activity and failed login attempts.
   ![Screenshot 6 - Final Dashboard View](screenshots/screenshot6.png)

### Step 3: Alert Configuration

1. **Configuring Brute-Force Detection Alert**:
   - **Alert Query**:
     ```splunk
     index=_audit action="login attempt" info="failed"
     ```
   - **Trigger Condition**: Configured to trigger if the count of failed login attempts is greater than 5 in real-time.
   ![Screenshot 7 - Alert Configuration](screenshots/screenshot7.png)

2. **Testing the Alert**: Simulated failed login attempts using incorrect credentials to test the alert.
   ![Screenshot 8 - Failed Login Simulation](screenshots/screenshot8.png)

3. **Triggered Alert**: Observed that the alert was successfully triggered, logging multiple failed attempts for the user 'hacker'.
   ![Screenshot 9 - Triggered Alert](screenshots/screenshot9.png)

---

## Screenshots & Visualizations

Here's a summary of the visuals used in this project:
- **Splunk Dashboard Login** - Initial Splunk dashboard upon login.
- **Audit Log Query** - Reviewing `_audit` logs to identify key fields for alerting.
- **Threat Detection Dashboard** - Custom dashboard for monitoring brute-force attacks.
- **Brute-Force Detection Data Source** - Panel for counting failed login attempts.
- **Login Activity Timechart** - Visualizes login attempts over time.
- **Dashboard with Active Data Sources** - Final dashboard with data panels for login monitoring.
- **Brute-Force Detection Alert Setup** - Configured alert to monitor failed logins.
- **Failed Login Simulation** - Manual failed login attempts to trigger the alert.
- **Alert Triggered** - Alert log indicating brute-force detection.
- **Dashboard with Updated Results** - Updated dashboard reflecting activity of both 'splunkstudent' and 'hacker'.

---

## Results & Findings

The configured alert successfully detected multiple consecutive failed login attempts, verifying the efficacy of this setup in identifying brute-force activity. Notable outcomes include:
- **Effective Real-Time Monitoring**: Splunk reliably identified repeated login failures as they occurred.
- **Clear Visualization**: The dashboard provided actionable insights into login trends, supporting further investigation.
- **Customizable Alerts**: The alert’s parameters can easily be adjusted to match evolving security requirements.

---

## Reflection & Future Work

### Reflection
This project reinforced key skills in Splunk for monitoring and alerting on security threats. From creating specific search queries to configuring real-time alerts, this exercise covered essential SOC analyst skills in detection and response.

### Future Work
Potential expansions include:
1. **Enhanced Correlation**: Integrate with other logs to correlate brute-force attacks with suspicious IP geolocation data.
2. **Dashboard Expansion**: Add panels for additional insights, such as geolocation of failed attempts or user-specific activity.
3. **Automation**: Integrate with incident response workflows to automatically notify relevant teams or block malicious IPs.

---

## Conclusion

This project highlights how Splunk can be configured to detect and monitor brute-force login attempts, leveraging SIEM capabilities to provide robust security insights. The project demonstrates not only technical proficiency but also practical applications for real-world security monitoring, making it a valuable reference for SOC analysts and cybersecurity enthusiasts.

---

### Repository Structure

```plaintext
├── brute_force_simulation_script.bat  # Script to simulate login attempts
├── screenshots/                       # Project screenshots
│   ├── screenshot1.png
│   ├── screenshot2.png
│   ├── screenshot3.png
│   └── ...
└── README.md                          # Project documentation
