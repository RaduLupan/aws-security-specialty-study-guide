# Domain 2: Security Logging & Monitoring (18%)

> 🚧 **Status:** In Progress

## Overview

This domain covers logging, monitoring, and analysis of security-related data in AWS.

---

## Key Services

| Service | Purpose |
|---------|---------|
| **AWS CloudTrail** | API activity logging |
| **Amazon CloudWatch** | Metrics, logs, alarms, dashboards |
| **VPC Flow Logs** | Network traffic logging |
| **AWS Config** | Resource configuration tracking |
| **Amazon S3 Access Logs** | S3 bucket access logging |
| **AWS Security Lake** | Centralized security data lake |

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

### Key Documentation Links

- [Logging and monitoring in AWS Audit Manager](https://docs.aws.amazon.com/audit-manager/latest/userguide/security-logging-and-monitoring.html)
- CloudTrail Lake for querying events
- Organization trails for multi-account logging

📖 **Documentation**: [CloudTrail User Guide](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/)

---

## 📊 Amazon CloudWatch

### CloudWatch Logs

- **Log Groups**: Container for log streams
- **Log Streams**: Sequence of events from same source
- **Metric Filters**: Extract metrics from log data
- **Subscription Filters**: Real-time processing to Lambda/Kinesis/Firehose

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

## 🛡️ AWS Security Hub (also in Domain 1)

### Key Documentation Links

- [Using Security Hub for vulnerability management](https://docs.aws.amazon.com/prescriptive-guidance/latest/vulnerability-management/aws-security-hub.html)
- [Exposure findings in Security Hub](https://docs.aws.amazon.com/securityhub/latest/userguide/exposure-findings.html)
- [Compliance validation for Security Hub](https://docs.aws.amazon.com/securityhub/latest/userguide/securityhub-compliance.html)
- [Creating and updating findings](https://docs.aws.amazon.com/securityhub/latest/userguide/securityhub-findings.html)

📖 **Documentation**: [Security Hub User Guide](https://docs.aws.amazon.com/securityhub/latest/userguide/)

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

## ⚙️ AWS Config

### What You Need to Know

- **Configuration Items**: Point-in-time view of resource config
- **Configuration History**: Changes over time
- **Configuration Recorder**: Records changes
- **Rules**: Evaluate resource compliance
- **Conformance Packs**: Collection of rules

### Rule Types

- **Managed Rules**: AWS-provided rules
- **Custom Rules**: Lambda-based custom logic
- **Trigger Types**: Configuration changes, periodic

### Aggregator

- Cross-account/cross-region aggregation
- View compliance across organization

### Key Documentation Links

- [What Is AWS Config?](https://docs.aws.amazon.com/config/latest/developerguide/WhatIsConfig.html)
- [Conformance Packs](https://docs.aws.amazon.com/config/latest/developerguide/conformance-packs.html)
- [Components of an AWS Config Rule](https://docs.aws.amazon.com/config/latest/developerguide/evaluate-config_components.html)

📖 **Documentation**: [AWS Config User Guide](https://docs.aws.amazon.com/config/latest/developerguide/)

---

## 🔐 AWS Security Lake

### What You Need to Know (NEW for SCS-C02)

- Centralizes security data in **OCSF format** (Open Cybersecurity Schema Framework)
- **Sources**: CloudTrail, VPC Flow Logs, Route 53 DNS Logs, Security Hub, custom sources
- **Subscribers**: Query access for SIEM/analytics tools
- Built on S3 with Lake Formation

📖 **Documentation**: [Security Lake User Guide](https://docs.aws.amazon.com/security-lake/latest/userguide/)

---

## 📺 Recommended Videos

- [AWS re:Invent 2022: Setting up controls at scale (COP318)](https://www.youtube.com/watch?v=NkE9_okfPG8)

---

## ✅ Exam Tips

- Know CloudTrail event types and when each is logged
- Understand log integrity validation
- Know VPC Flow Log fields and what they mean
- Understand Config rule trigger types
- Know how to aggregate logs across accounts

---

*Last updated: January 2026*
