# Domain 2: Incident Response (14%)

> 🚧 **Status:** In Progress  
> **SCS-C03 Update:** This is now a separate domain (was part of "Threat Detection & Incident Response" in SCS-C02)

## Overview

This domain covers incident response planning, execution, and security event handling in AWS.

---

## Task Statements (SCS-C03)

1. **Task 2.1**: Design and test an incident response plan
2. **Task 2.2**: Respond to security events

### New in SCS-C03
- **Task 2.2.3**: Validate findings from AWS security services to assess the scope and impact of an event

---

## Key Services

| Service | Purpose |
|---------|---------|
| **Amazon Detective** | Security investigation and root cause analysis |
| **AWS Security Hub** | Central finding aggregation and automation |
| **Amazon EventBridge** | Event-driven automation for responses |
| **AWS Lambda** | Automated remediation actions |
| **AWS Systems Manager** | Runbook automation and patch management |
| **AWS Step Functions** | Orchestration of incident response workflows |

---

## 🚨 Incident Response Framework

### AWS Incident Response Phases

1. **Preparation**
   - IAM roles for responders
   - Runbooks and playbooks
   - Forensic accounts (isolated)
   - Training and simulations

2. **Detection**
   - GuardDuty findings
   - CloudTrail anomalies
   - Security Hub alerts
   - Config rule violations

3. **Containment**
   - Security groups (isolate resources)
   - NACLs (network isolation)
   - IAM deny policies
   - Resource tagging for tracking

4. **Eradication**
   - Remove compromised resources
   - Rotate credentials
   - Patch vulnerabilities
   - Update security controls

5. **Recovery**
   - Restore from clean backups
   - Validate security posture
   - Gradual service restoration
   - Monitoring for recurrence

6. **Lessons Learned**
   - Post-incident review
   - Update runbooks
   - Improve detection rules
   - Share findings (if appropriate)

---

## 🔎 Amazon Detective

### What You Need to Know

- Uses **graph database** to analyze relationships
- **Data sources**: CloudTrail, VPC Flow Logs, GuardDuty findings, EKS audit logs
- Helps answer: "What happened?", "Who did it?", "What was affected?"
- **36-month data retention**
- Integrates with GuardDuty and Security Hub

📖 **Documentation**: [Detective User Guide](https://docs.aws.amazon.com/detective/latest/userguide/)

---

## 🖥️ EC2 Incident Response

### Isolation Steps

1. **Don't terminate** - preserve evidence
2. **Isolate** - modify security group to deny all traffic (attach "quarantine" SG)
3. **Snapshot** - create EBS snapshots for forensics
4. **Memory capture** - if possible (requires agent)
5. **Tag** - mark as compromised
6. **Investigate** - use Detective, CloudTrail, VPC Flow Logs

### Forensic Best Practices

- Maintain forensic account (separate, isolated)
- Use cross-account IAM roles for access
- Preserve chain of custody
- Document all actions with timestamps
- Never modify evidence directly

---

## 🔄 Automated Response

### EventBridge Rules

```
GuardDuty Finding → EventBridge → Lambda → Remediation
```

### Common Automations

| Finding | Automated Response |
|---------|-------------------|
| Unauthorized access | Disable IAM user/role |
| Compromised EC2 | Isolate with quarantine SG |
| S3 bucket public | Block public access |
| Crypto mining | Stop/terminate instance |
| Credential exfiltration | Rotate credentials |

### AWS Systems Manager Runbooks

- Pre-built and custom runbooks
- Automated or approval-required execution
- Integration with incident response workflows

---

## 📋 Incident Response Plan Components

### Required Elements

- **Roles and Responsibilities**: Who does what
- **Communication Plan**: Internal and external notifications
- **Escalation Procedures**: When and how to escalate
- **Runbooks**: Step-by-step procedures
- **Evidence Collection**: What to capture and preserve
- **Recovery Procedures**: How to restore services

### Testing

- **Tabletop exercises**: Discussion-based walkthroughs
- **Simulations**: Controlled security events (GameDay)
- **Red team exercises**: Adversarial testing
- Regular updates based on lessons learned

---

## 🛡️ Containment Strategies

### Network Isolation

| Method | Use Case |
|--------|----------|
| Security Group | Instance-level isolation (fastest) |
| NACL | Subnet-level isolation |
| Route Table | VPC/subnet routing changes |
| AWS Network Firewall | Deep packet inspection |

### Identity Isolation

- Attach explicit deny policy to user/role
- Deactivate access keys
- Revoke IAM sessions (with permission boundary)
- Disable AWS Identity Center user

### Resource Isolation

- Move to isolated subnet
- Disable API access (resource policy)
- Enable S3 Object Lock (for evidence)

---

## 📖 Key Documentation Links

- [AWS Security Incident Response Guide - Introduction](https://docs.aws.amazon.com/whitepapers/latest/aws-security-incident-response-guide/introduction.html)
- [Threat Detection - AWS CAF Security Perspective](https://docs.aws.amazon.com/whitepapers/latest/aws-caf-security-perspective/threat-detection.html)
- [AWS Security Incident Response Guide (Full)](https://docs.aws.amazon.com/whitepapers/latest/aws-security-incident-response-guide/)

---

## 📺 Recommended Videos

- [AWS re:Inforce 2022: Running effective security incident response simulations (TDR201)](https://www.youtube.com/watch?v=63EdzHT25_A)
- [AWS re:Inforce 2022: A proactive approach to zero-days: Lessons from Log4j (TDR301)](https://www.youtube.com/watch?v=CEq5wGJjh1g)

---

## ✅ Exam Tips

- Know the incident response phases and what happens in each
- Understand EC2 isolation steps (don't terminate, quarantine SG, snapshot)
- Know how to use Detective for investigation
- Understand automated response patterns with EventBridge
- Know containment strategies at network, identity, and resource levels
- **SCS-C03**: Validate findings to assess scope and impact (new task)

---

*Last updated: January 2026 (SCS-C03)*
