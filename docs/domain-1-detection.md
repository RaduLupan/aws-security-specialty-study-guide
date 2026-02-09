# Domain 1: Detection (16%)

> 🚧 **Status:** In Progress  
> **SCS-C03 Update:** This domain was restructured from "Threat Detection & Incident Response" in SCS-C02. Incident Response is now a separate Domain 2.

## Overview

This domain covers monitoring, alerting, logging, and threat detection capabilities in AWS.

---

## Task Statements & Skills (SCS-C03)

### Task 1.1: Design and implement monitoring and alerting for an AWS account or organization

| Skill | Key Services |
|-------|-------------|
| 1.1.1: Analyze workloads to determine monitoring requirements | CloudWatch, GuardDuty |
| 1.1.2: Design and implement workload monitoring strategies (e.g., resource health checks) | CloudWatch, Systems Manager |
| 1.1.3: Aggregate security and monitoring events | Security Hub, Security Lake, EventBridge |
| 1.1.4: Create metrics, alerts, and dashboards to detect anomalous data and events | **GuardDuty, Security Lake, Security Hub, Macie** |
| 1.1.5: Create and manage automations to perform regular assessments and investigations | **AWS Config conformance packs, Security Hub, Systems Manager State Manager** |

### Task 1.2: Design and implement logging solutions

| Skill | Key Services |
|-------|-------------|
| 1.2.1: Identify sources for log ingestion and storage based on requirements | CloudTrail, CloudWatch Logs, S3, Security Lake |
| 1.2.2: Configure logging for AWS services and applications | **CloudTrail (org trail), CloudWatch Logs (dedicated logging account, Logs agent)** |
| 1.2.3: Implement log storage and log data lakes, integrate with third-party tools | **Security Lake (OCSF format)** |
| 1.2.4: Use AWS services to analyze logs | **CloudWatch Logs Insights, Amazon Athena, Security Hub findings** |
| 1.2.5: Normalize, parse, and correlate logs | **Amazon OpenSearch Service, AWS Lambda, Amazon Managed Grafana** |
| 1.2.6: Determine and configure appropriate log sources based on network design, threats, and attacks | **VPC Flow Logs, Transit Gateway flow logs, Route 53 Resolver logs** |

### Task 1.3: Troubleshoot security monitoring, logging, and alerting solutions

| Skill | Key Services |
|-------|-------------|
| 1.3.1: Analyze functionality, permissions, and configuration of resources | **Lambda function logging, API Gateway logging, health checks, CloudFront logging** |
| 1.3.2: Remediate misconfiguration of resources | CloudWatch Agent configurations, troubleshooting missing logs |

---

## Key Services

| Service | Purpose |
|---------|---------|
| **Amazon GuardDuty** | Threat detection using ML and threat intelligence |
| **AWS Security Hub** | Security posture management and aggregation |
| **AWS CloudTrail** | API activity logging |
| **Amazon CloudWatch** | Metrics, logs, alarms, dashboards |
| **VPC Flow Logs** | Network traffic logging (VPC, subnet, ENI, Transit Gateway) |
| **AWS Config** | Resource configuration tracking and conformance packs |
| **Amazon Security Lake** | Centralized security data lake (OCSF format) |
| **Amazon Macie** | Sensitive data discovery and classification in S3 |
| **Amazon Athena** | Serverless SQL query engine for log analysis |
| **Amazon OpenSearch Service** | Log normalization, parsing, and correlation |
| **Amazon Managed Grafana** | Security dashboards and log visualization |
| **AWS Systems Manager** | State Manager for automated assessments |
| **AWS Lambda** | Log parsing, normalization, and custom processing |
| **Amazon Route 53 Resolver** | DNS query logging for threat detection |

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

## 🔍 Amazon Macie

### What You Need to Know

- **Discovers sensitive data** in S3 (PII, PHI, financial data)
- **Machine learning** for automated data classification
- Findings integrate with **Security Hub** for centralized alerting
- **Managed data identifiers**: 100+ predefined patterns
- **Custom data identifiers**: Regex patterns for org-specific data
- Relevant to Domain 1 for detecting anomalous data exposure and data loss

### Exam Relevance (Skill 1.1.4)

- Macie can trigger alerts when sensitive data is detected in unexpected locations
- Integrates with EventBridge for automated response to sensitive data findings
- Multi-account support via AWS Organizations

📖 **Documentation**: [Macie User Guide](https://docs.aws.amazon.com/macie/latest/user/)

---

## 🔎 Amazon Athena (Log Analysis)

### What You Need to Know

- **Serverless SQL query engine** for analyzing data in S3
- Query **CloudTrail logs**, **VPC Flow Logs**, **ALB access logs**, **S3 access logs** directly in S3
- Integrates with **AWS Glue Data Catalog** for schema management
- Pay-per-query pricing (per TB scanned)
- Use **partitioning** and **columnar formats** (Parquet/ORC) to reduce cost and improve performance

### Security Use Cases (Skill 1.2.4)

- Investigate CloudTrail events for suspicious API activity
- Analyze VPC Flow Logs for network anomalies
- Query Security Lake data (OCSF format) for cross-source correlation
- Ad-hoc forensic investigation of historical logs

📖 **Documentation**: [Athena User Guide](https://docs.aws.amazon.com/athena/latest/ug/)  
📖 **Querying CloudTrail Logs**: [Querying CloudTrail with Athena](https://docs.aws.amazon.com/athena/latest/ug/cloudtrail-logs.html)

---

## 📊 Amazon OpenSearch Service (Log Correlation)

### What You Need to Know

- **Managed OpenSearch/Elasticsearch** for log analytics
- Real-time **log normalization, parsing, and correlation** at scale
- Built-in dashboards (OpenSearch Dashboards / Kibana)
- Supports **ingestion pipelines** for transforming log data
- Fine-grained access control with IAM and SAML

### Security Use Cases (Skill 1.2.5)

- Centralized security log aggregation and near-real-time search
- Correlation of events across CloudTrail, VPC Flow Logs, and application logs
- Anomaly detection and visualization for security operations
- Integration with CloudWatch Logs via subscription filters

📖 **Documentation**: [OpenSearch Service Developer Guide](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/)

---

## 📈 Amazon Managed Grafana

### What You Need to Know

- **Fully managed Grafana** for security dashboards and visualization
- Integrates with CloudWatch, OpenSearch, Athena, X-Ray, and more
- **SAML and IAM Identity Center** authentication
- Workspace isolation and fine-grained access control

### Security Use Cases (Skill 1.2.5)

- Build security operations dashboards combining multiple data sources
- Visualize parsed and correlated log data from OpenSearch or Athena
- Real-time monitoring dashboards for security metrics

📖 **Documentation**: [Managed Grafana User Guide](https://docs.aws.amazon.com/grafana/latest/userguide/)

---

## 🖥️ AWS Systems Manager State Manager

### What You Need to Know

- **Automated configuration management** for managed instances
- Maintains instances in a **defined state** using associations
- Runs **SSM documents** on a schedule or triggered basis
- Integrates with AWS Config for compliance tracking

### Security Use Cases (Skill 1.1.5)

- Automate regular security assessments (e.g., run CIS benchmarks on schedule)
- Enforce security configurations on EC2 instances
- Automate investigation scripts across fleet of instances

📖 **Documentation**: [Systems Manager State Manager](https://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-state.html)

---

## 🌐 Additional Log Sources (Skill 1.2.6)

### Transit Gateway Flow Logs

- Capture traffic flowing through **AWS Transit Gateway**
- Same format as VPC Flow Logs
- Essential for monitoring **east-west traffic** between VPCs and on-premises networks
- Destinations: CloudWatch Logs, S3, Kinesis Data Firehose

📖 **Documentation**: [Transit Gateway Flow Logs](https://docs.aws.amazon.com/vpc/latest/tgw/tgw-flow-logs.html)

### Amazon Route 53 Resolver DNS Logs

- Log DNS queries made by resources in your VPC
- Capture **internal and external DNS resolution** activity
- Detect DNS exfiltration, tunneling, and communication with malicious domains
- Integrate with **Route 53 Resolver DNS Firewall** for blocking

📖 **Documentation**: [Route 53 Resolver Query Logging](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/resolver-query-logs.html)

### API Gateway Logging (Skill 1.3.1)

- **Execution logs**: Detailed request/response data (CloudWatch Logs)
- **Access logs**: Customizable access log format
- Enable **X-Ray tracing** for distributed tracing
- Common troubleshooting: missing CloudWatch Logs role ARN on API Gateway

📖 **Documentation**: [API Gateway CloudWatch Logging](https://docs.aws.amazon.com/apigateway/latest/developerguide/set-up-logging.html)

### CloudFront Logging (Skill 1.3.1)

- **Standard logs**: Delivered to S3 (per-distribution)
- **Real-time logs**: Delivered to Kinesis Data Streams
- Fields include: client IP, request URI, edge location, HTTP status, cache hit/miss
- Used for detecting web attacks and analyzing traffic patterns

📖 **Documentation**: [CloudFront Logging](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/AccessLogs.html)

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
- Know when to use **Athena** vs **OpenSearch** vs **CloudWatch Logs Insights** for log analysis
- Understand **Macie** for detecting sensitive data in S3 (Skill 1.1.4)
- Know **Transit Gateway flow logs** and **Route 53 Resolver logs** as additional log sources (Skill 1.2.6)
- Understand **Managed Grafana** for security dashboards (Skill 1.2.5)
- Know how to troubleshoot **API Gateway** and **CloudFront** logging (Skill 1.3.1)
- Understand **Systems Manager State Manager** for automated security assessments (Skill 1.1.5)

---

*Last updated: January 2026 (SCS-C03)*
