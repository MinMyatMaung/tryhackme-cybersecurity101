# Incident Response

## Overview

Incident Response is the process organizations use to prepare for, detect, contain, remove, and recover from cybersecurity incidents.

Security tools analyze logs and generate alerts for suspicious activity.

- **False Positive** – An alert that looks malicious but is actually legitimate.
- **True Positive** – An alert that represents real malicious activity.
- Confirmed true positives may be classified as **security incidents**.

Incidents are commonly prioritized as:

- Low
- Medium
- High
- Critical

## Common Types of Incidents

### Malware Infection
Malicious software that can damage systems, steal data, or give attackers unauthorized access.

### Security Breach
Unauthorized access to systems or confidential information.

### Data Leak
Sensitive information is exposed due to attacks, human error, or misconfiguration.

### Insider Attack
A trusted user intentionally misuses their access to harm the organization.

### Denial of Service (DoS)
An attacker overwhelms a system or network, making it unavailable to legitimate users.

## SANS Incident Response Framework

The SANS framework can be remembered as **PICERL**:

1. **Preparation** – Build procedures, teams, tools, and training.
2. **Identification** – Monitor activity and confirm incidents.
3. **Containment** – Limit the spread and impact of the attack.
4. **Eradication** – Remove threats and attacker access.
5. **Recovery** – Restore and test affected systems.
6. **Lessons Learned** – Review the incident and improve defenses.

## NIST Incident Response Framework

NIST uses four main phases:

1. **Preparation**
2. **Detection and Analysis**
3. **Containment, Eradication, and Recovery**
4. **Post-Incident Activity**

SANS and NIST follow similar ideas but organize the response process differently.

## Incident Response Plan

An **Incident Response Plan (IRP)** defines how an organization handles security incidents.

Common components include:

- Roles and responsibilities
- Response procedures
- Communication plans
- Stakeholder notification
- Escalation procedures

## Incident Detection and Response Tools

## Detection and Analysis

The second phase of incident response focuses on identifying suspicious activity and confirming whether an incident has occurred.

Because manually reviewing large amounts of activity is difficult, organizations use security tools to help detect and respond to threats.

## Common Security Tools

### SIEM

A **Security Information and Event Management (SIEM)** system collects logs from multiple sources into one place and analyzes them for suspicious activity.

### Antivirus

**Antivirus (AV)** scans systems for known malicious files and programs.

### EDR

**Endpoint Detection and Response (EDR)** monitors endpoint activity and can detect more advanced threats.

EDR may also help with:

- Containment
- Investigation
- Threat removal

## Playbooks

A **playbook** provides a structured response process for a specific type of incident.

For example, a phishing playbook may include:

1. Notify relevant stakeholders.
2. Analyze the email header and content.
3. Inspect attachments.
4. Check whether users opened the attachment.
5. Isolate infected systems.
6. Block the malicious sender.

Playbooks help security teams respond consistently and quickly.

## Runbooks

A **runbook** contains detailed step-by-step instructions for performing a specific response action.

While a playbook describes the overall process, a runbook explains exactly how individual tasks should be carried out.

## Phishing Incident Investigation

In a phishing incident, analysts may need to:

- Identify hosts that received or downloaded the malicious file.
- Determine which systems executed the malware.
- Isolate infected endpoints.
- Investigate the timeline of activity.
- Remove the threat and prevent further spread.

## Key Takeaway

Incident Response is the process of preparing for, detecting, containing, removing, and recovering from cybersecurity incidents.

I learned about:

- Events, alerts, false positives, true positives, and incidents
- Incident severity and common incident types
- SANS and NIST response frameworks
- SIEM, Antivirus, and EDR tools
- Playbooks and runbooks

Overall, effective incident response helps organizations reduce damage, restore systems, and improve future security.
