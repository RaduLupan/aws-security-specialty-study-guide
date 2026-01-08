# Domain 1: Threat Detection & Incident Response (14%)

> 🚧 **Status:** In Progress

## Overview

This domain covers threat detection services, incident response procedures, and security investigation capabilities in AWS.

---

## Key Services

| Service | Purpose |
|---------|---------|
| **Amazon GuardDuty** | Threat detection using ML and threat intelligence |
| **AWS Security Hub** | Security posture management and aggregation |
| **Amazon Detective** | Security investigation and root cause analysis |
| **AWS CloudTrail** | API activity logging (used for detection) |
| **Amazon EventBridge** | Event-driven automation for responses |

---

## 🔍 Amazon GuardDuty

### What You Need to Know

- **Data Sources**: CloudTrail Management Events, VPC Flow Logs, DNS Logs, S3 Data Events, EKS Audit Logs, RDS Login Activity, Lambda Network Activity
- **Finding Types**: Backdoor, Behavior, CryptoCurrency, PenTest, Policy, Recon, Stealth, Trojan, UnauthorizedAccess
- **Severity Levels**: Low (0.1-3.9), Medium (4.0-6.9), High (7.0-8.9), Critical (9.0-10.0)

### Extended Threat Detection (NEW in SCS-C02)

- Detects **multi-stage attack sequences** across your AWS environment
- Uses AI/ML to correlate individual findings into attack sequences
- **Attack Sequence Finding Types**:
  - Credential compromise followed by privilege escalation
  - Data exfiltration patterns
  - Lateral movement across accounts

### GuardDuty Malware Protection

- Scans EBS volumes attached to EC2 instances
- Triggered by specific GuardDuty findings
- Creates snapshot, scans, then deletes snapshot

### Key Documentation Links

- [GuardDuty Extended Threat Detection](https://docs.aws.amazon.com/guardduty/latest/ug/guardduty-extended-threat-detection.html)
- [Working with GuardDuty in Network Firewall](https://docs.aws.amazon.com/network-firewall/latest/developerguide/nwfw-atd-guardduty-use-case.html)
- [Detect threats with GuardDuty (Secrets Manager)](https://docs.aws.amazon.com/secretsmanager/latest/userguide/monitoring-guardduty.html)

📖 **Documentation**: [GuardDuty User Guide](https://docs.aws.amazon.com/guardduty/latest/ug/)

---

## 🛡️ AWS Security Hub

### What You Need to Know

- **Aggregates findings** from GuardDuty, Inspector, Macie, IAM Access Analyzer, Firewall Manager
- **Security Standards**: AWS Foundational Security Best Practices, CIS AWS Foundations, PCI DSS
- **Findings format**: AWS Security Finding Format (ASFF)
- **Cross-account/cross-region** aggregation

### Key Concepts

- **Controls**: Individual security checks
- **Insights**: Grouped findings by criteria
- **Automations**: EventBridge integration for auto-remediation

📖 **Documentation**: [Security Hub User Guide](https://docs.aws.amazon.com/securityhub/latest/userguide/)

---

## 🔎 Amazon Detective

### What You Need to Know

- Uses **graph database** to analyze relationships
- **Data sources**: CloudTrail, VPC Flow Logs, GuardDuty findings, EKS audit logs
- Helps answer: "What happened?", "Who did it?", "What was affected?"
- **36-month data retention**

📖 **Documentation**: [Detective User Guide](https://docs.aws.amazon.com/detective/latest/userguide/)

---

## 🚨 Incident Response

### AWS Incident Response Framework

1. **Preparation**: IAM roles, runbooks, forensic accounts
2. **Detection**: GuardDuty, CloudTrail, Security Hub
3. **Containment**: Security groups, NACLs, IAM deny policies
4. **Eradication**: Remove compromised resources
5. **Recovery**: Restore from clean backups
6. **Lessons Learned**: Post-incident review

### EC2 Incident Response Steps

1. **Don't terminate** - preserve evidence
2. **Isolate** - modify security group to deny all traffic
3. **Snapshot** - create EBS snapshots for forensics
4. **Memory capture** - if possible
5. **Tag** - mark as compromised
6. **Investigate** - use Detective, CloudTrail, VPC Flow Logs

### Key Documentation Links

- [AWS Security Incident Response Guide - Introduction](https://docs.aws.amazon.com/whitepapers/latest/aws-security-incident-response-guide/introduction.html)
- [Threat Detection - AWS CAF Security Perspective](https://docs.aws.amazon.com/whitepapers/latest/aws-caf-security-perspective/threat-detection.html)

📖 **Documentation**: [AWS Security Incident Response Guide](https://docs.aws.amazon.com/whitepapers/latest/aws-security-incident-response-guide/)

---

## 📺 Recommended Videos

- [AWS re:Inforce 2022: Introducing Amazon GuardDuty Malware Protection (TDR210)](https://www.youtube.com/watch?v=9wCxAZtrjpw)
- [AWS re:Inforce 2022: Running effective security incident response simulations (TDR201)](https://www.youtube.com/watch?v=63EdzHT25_A)

---

## 🎮 Practice Quizzes

- [Amazon GuardDuty Comprehensive Quiz](../quizzes/guardduty-comprehensive.html) (25 questions)
- [GuardDuty Extended Threat Detection Quiz](../quizzes/guardduty-extended-threat-detection.html) (15 questions)

---

## ✅ Exam Tips

- Know the difference between GuardDuty, Security Hub, and Detective
- Understand GuardDuty finding severities and types
- Know which data sources each service uses
- Understand EC2 incident response isolation steps
- Know how to aggregate findings across accounts

---

*Last updated: January 2026*
