# Postmortem: Unplanned Outage on January 17, 2024
## Issue Summary:
Duration: January 17, 2024, 14:30 - 17:45 (UTC)
Impact: Affecting the core authentication service; users experienced login failures, leading to a 30% decrease in user activity during the outage.
Timeline:
Detection: January 17, 2024, 14:30 (UTC)
The issue was initially detected through a surge in error rates reported by our monitoring system.
## Actions Taken:
Engineering immediately began investigating potential causes, focusing on recent deployments and network configurations.
Initial assumption: Connection issues with the authentication database due to a recent update.
## Misleading Paths:
Initial investigation leaned towards a misconfiguration in the load balancer, diverting attention from the actual root cause.
Increased scrutiny on recent code deployments distracted from identifying the core issue promptly.
## Escalation:
As the issue persisted, it was escalated to the Database Operations team and senior engineers for additional expertise.
## Resolution:
The root cause, ultimately identified as a misconfigured firewall rule blocking database connections, was rectified by updating the firewall settings.
Normal service was restored after deploying the firewall rule fix at 17:45 (UTC).
Root Cause and Resolution:
## Root Cause:
The issue originated from a recent change in network policies, resulting in a firewall rule blocking communication between the authentication service and the database.
This misconfiguration prevented user authentication requests from reaching the database, leading to login failures.
## Resolution:
The immediate resolution involved updating the firewall rule to permit the necessary connections between the authentication service and the database.
A more comprehensive review of network policies was conducted to prevent similar issues in the future.
Corrective and Preventative Measures:
## Improvements/Fixes:
Strengthen monitoring alerts specifically for critical services, ensuring prompt detection of similar issues.
Enhance the incident response playbook to include a systematic approach for investigating database-related anomalies.
Implement regular review and audit procedures for network policies and configurations to catch discrepancies early.
## Tasks:
### Short-Term:
Conduct a thorough analysis of the network configurations and firewall rules to identify any lingering issues.
Update incident response documentation with a focus on quick identification and resolution of authentication service-related problems.
### Mid-to-Long-Term:
Schedule regular drills for the incident response team to practice identifying and resolving critical issues promptly.
Collaborate with the Database Operations team to establish a proactive review process for database-related network policies.
Implement automated tests in the deployment pipeline to catch potential firewall rule misconfigurations before reaching production.
In conclusion, the unplanned outage on January 17, 2024, was a result of a misconfigured firewall rule impacting the authentication service. The incident was resolved by promptly identifying and correcting the root cause, with comprehensive measures implemented to prevent similar issues in the future. The corrective actions taken are aimed at strengthening monitoring, improving incident response procedures, and instituting proactive measures to safeguard against network configuration issues.


