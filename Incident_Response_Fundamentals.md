# Incident Response

## Overview

Incident Response is the structured process organizations use to prepare for, detect, contain, remove, and recover from cybersecurity incidents.

Security tools continuously collect and analyze system logs. When suspicious activity is detected, an **alert** is generated and investigated by the security team.

- **False Positive** – An alert that appears malicious but is actually legitimate activity.
- **True Positive** – An alert that represents real malicious activity.
- A confirmed true positive may be classified as a **security incident**.

Incidents are usually prioritized by severity:

- Low
- Medium
- High
- Critical

Critical incidents receive the highest response priority.

## Common Types of Security Incidents

### Malware Infection
Malicious software infects a device or network and may damage systems, steal information, or provide attackers with unauthorized access.

### Security Breach
An unauthorized user gains access to systems or confidential information.

### Data Leak
Sensitive information becomes exposed to unauthorized individuals. Data leaks may result from attacks, human error, or system misconfiguration.

### Insider Attack
A trusted user, such as an employee, intentionally misuses their access to damage or compromise organizational resources.

### Denial of Service (DoS)
An attacker overwhelms a system, application, or network with requests, preventing legitimate users from accessing the service.

## SANS Incident Response Framework

The SANS framework can be remembered using **PICERL**:

1. **Preparation**
   - Create incident response procedures.
   - Establish response teams.
   - Deploy security tools.
   - Train employees.

2. **Identification**
   - Monitor systems and logs.
   - Detect abnormal activity.
   - Determine whether an incident has occurred.

3. **Containment**
   - Limit the spread and impact of the incident.
   - Isolate affected systems.
   - Disable compromised accounts when necessary.

4. **Eradication**
   - Remove malware or other threats.
   - Eliminate the attacker's access.
   - Address the root cause of the compromise.

5. **Recovery**
   - Restore affected systems.
   - Recover data from backups if necessary.
   - Test systems before returning them to normal operation.

6. **Lessons Learned**
   - Review how the incident occurred.
   - Document findings.
   - Identify weaknesses.
   - Improve detection and response procedures.

## NIST Incident Response Framework

NIST uses a similar incident response process with four main phases:

1. **Preparation**
2. **Detection and Analysis**
3. **Containment, Eradication, and Recovery**
4. **Post-Incident Activity**

The SANS and NIST frameworks follow similar principles but organize the response stages differently.

## Incident Response Plan

An **Incident Response Plan (IRP)** is a formal document describing how an organization will respond to cybersecurity incidents.

Common components include:

- Roles and responsibilities
- Incident response procedures
- Communication procedures
- Stakeholder notification
- Law enforcement communication
- Incident escalation procedures
