# Domain 1: Detection (16%)

> 🚧 **Status:** In Progress  
> **SCS-C03 Update:** This domain was restructured from "Threat Detection & Incident Response" in SCS-C02. Incident Response is now a separate Domain 2.

## Overview

This domain covers monitoring, alerting, logging, and threat detection capabilities in AWS.

---

## Task Statements (SCS-C03)

1. **Task 1.1**: Design and implement monitoring and alerting for an AWS account or organization
2. **Task 1.2**: Design and implement logging
3. **Task 1.3**: Troubleshoot security monitoring, logging and alerting

---

## Key Services

| Service | Purpose |
|---------|---------|
| **Amazon GuardDuty** | Threat detection using ML and threat intelligence |
| **AWS Security Hub** | Security posture management and aggregation |
| **AWS CloudTrail** | API activity logging |
| **Amazon CloudWatch** | Metrics, logs, alarms, dashboards |
| **VPC Flow Logs** | Network traffic logging |
| **AWS Config** | Resource configuration tracking |
| **Amazon Security Lake** | Centralized security data lake (OCSF format) |

---

## 🔍 Amazon GuardDuty

### What You Need to Know

- **Data Sources**: CloudTrail Management Events, VPC Flow Logs, DNS Logs, S3 Data Events, EKS Audit Logs, RDS Login Activity, Lambda Network Activity
- **Finding Types**: Backdoor, Behavior, CryptoCurrency, PenTest, Policy, Recon, Stealth, Trojan, UnauthorizedAccess
- **Severity Levels**: Low (0.1-3.9), Medium (4.0-6.9), High (7.0-8.9), Critical (9.0-10.0)

### Extended Threat Detection

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

### Key Documentation Links

- [Using Security Hub for vulnerability management](https://docs.aws.amazon.com/prescriptive-guidance/latest/vulnerability-management/aws-security-hub.html)
- [Exposure findings in Security Hub](https://docs.aws.amazon.com/securityhub/latest/userguide/exposure-findings.html)
- [Compliance validation for Security Hub](https://docs.aws.amazon.com/securityhub/latest/userguide/securityhub-compliance.html)

📖 **Documentation**: [Security Hub User Guide](https://docs.aws.amazon.com/securityhub/latest/userguide/)

---

## 📝 AWS CloudTrail

### What You Need to Know

- **Management Events**: Control plane operations (default enabled)
- **Data Events**: Data plane operations (S3, Lambda, DynamoDB) - must enable explicitly
- **Insights Events**: Unusual API activity detection
- **Organization Trail**: Single trail for all accounts in org

### Log Integrity

- **Log File Validation**: SHA-256 hash, RSA signature
- **Digest Files**: Hourly summary of log files
- Validates logs haven't been modified/deleted

### Multi-Account Logging

- Central S3 bucket with bucket policy
- KMS key with cross-account access
- SNS topic for notifications
- CloudTrail Lake for querying events

📖 **Documentation**: [CloudTrail User Guide](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/)

---

## 📊 Amazon CloudWatch

### CloudWatch Logs

- **Log Groups**: Container for log streams
- **Log Streams**: Sequence of events from same source
- **Metric Filters**: Extract metrics from log data
- **Subscription Filters**: Real-time processing to Lambda/Kinesis/Firehose
- **Data Protection** (NEW in SCS-C03): Mask sensitive data in logs

### CloudWatch Alarms

- **Standard Alarms**: Based on metrics
- **Composite Alarms**: Combine multiple alarms with AND/OR
- **Anomaly Detection**: ML-based anomaly detection

### Security Use Cases

- Monitor root account usage
- Track unauthorized API calls
- Alert on security group changes
- Monitor IAM policy changes

📖 **Documentation**: [CloudWatch User Guide](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/)

---

## 🌐 VPC Flow Logs

### What You Need to Know

- **Capture Points**: VPC, Subnet, or ENI level
- **Destinations**: CloudWatch Logs, S3, Kinesis Data Firehose
- **Fields**: srcaddr, dstaddr, srcport, dstport, protocol, packets, bytes, action
- **Custom Format**: Select specific fields

### Security Analysis

- Detect port scanning
- Identify unusual traffic patterns
- Investigate connections to known bad IPs
- Validate security group rules

📖 **Documentation**: [VPC Flow Logs](https://docs.aws.amazon.com/vpc/latest/userguide/flow-logs.html)

---

## 🔐 AWS Security Lake

### What You Need to Know

- Centralizes security data in **OCSF format** (Open Cybersecurity Schema Framework)
- **Sources**: CloudTrail, VPC Flow Logs, Route 53 DNS Logs, Security Hub, custom sources
- **Subscribers**: Query access for SIEM/analytics tools
- Built on S3 with Lake Formation
- **SCS-C03**: Integration with OCSF format for third-party services is new content

📖 **Documentation**: [Security Lake User Guide](https://docs.aws.amazon.com/security-lake/latest/userguide/)

---

## ⚙️ AWS Config

### What You Need to Know

- **Configuration Items**: Point-in-time view of resource config
- **Configuration Recorder**: Records changes
- **Rules**: Evaluate resource compliance
- **Conformance Packs**: Collection of rules

### Rule Types

- **Managed Rules**: AWS-provided rules
- **Custom Rules**: Lambda-based custom logic
- **Trigger Types**: Configuration changes, periodic

### Key Documentation Links

- [What Is AWS Config?](https://docs.aws.amazon.com/config/latest/developerguide/WhatIsConfig.html)
- [Conformance Packs](https://docs.aws.amazon.com/config/latest/developerguide/conformance-packs.html)

📖 **Documentation**: [AWS Config User Guide](https://docs.aws.amazon.com/config/latest/developerguide/)

---

## 📺 Recommended Videos

- [AWS re:Inforce 2022: Introducing Amazon GuardDuty Malware Protection (TDR210)](https://www.youtube.com/watch?v=9wCxAZtrjpw)
- [AWS re:Inforce 2022: What's new with AWS threat detection services (TDR202)](https://www.youtube.com/watch?v=uDvP6tlkpjQ)

---

## 🎮 Practice Quizzes

- [Amazon GuardDuty Comprehensive Quiz](../quizzes/guardduty-comprehensive.html) (25 questions)
- [GuardDuty Extended Threat Detection Quiz](../quizzes/guardduty-extended-threat-detection.html) (15 questions)

---

## ✅ Exam Tips

- Know the difference between GuardDuty, Security Hub, and Config
- Understand GuardDuty finding severities and types
- Know which data sources each service uses
- Understand CloudTrail event types and log integrity validation
- Know VPC Flow Log fields and analysis techniques
- Understand OCSF format and Security Lake integration

---

*Last updated: January 2026 (SCS-C03)*
