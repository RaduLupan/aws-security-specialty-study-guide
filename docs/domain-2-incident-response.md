# Domain 2: Incident Response (14%)

> 🚧 **Status:** In Progress  
> **SCS-C03 Update:** This is now a separate domain (was part of "Threat Detection & Incident Response" in SCS-C02)

## Overview

This domain covers incident response planning, execution, and security event handling in AWS.

---

## Task Statements & Skills (SCS-C03)

### Task 2.1: Design and test an incident response plan

| Skill | Key Services |
|-------|-------------|
| 2.1.1: Design and implement response plans and runbooks to respond to security incidents | **Systems Manager OpsCenter, Amazon SageMaker AI notebooks** |
| 2.1.2: Configure services to be prepared for incidents (provisioning access, deploying security tools, minimizing blast radius) | **AWS Shield Advanced protections** |
| 2.1.3: Recommend procedures to test and validate the effectiveness of an incident response plan | **AWS Fault Injection Service, AWS Resilience Hub** |
| 2.1.4: Use AWS services to automatically remediate incidents | **Systems Manager, Automated Forensics Orchestrator for Amazon EC2, AWS Step Functions, Amazon Application Recovery Controller, Lambda** |

### Task 2.2: Respond to security events

| Skill | Key Services |
|-------|-------------|
| 2.2.1: Capture and store relevant system and application logs as forensic artifacts | CloudTrail, CloudWatch Logs, S3, EBS Snapshots |
| 2.2.2: Search and correlate logs for security events across applications and AWS services | Security Lake, Athena, OpenSearch, CloudWatch Logs Insights |
| 2.2.3: Validate findings from AWS security services to assess the scope and impact of an event | Security Hub, GuardDuty, Inspector |
| 2.2.4: Respond to affected resources (containment, eradication, recovery) | Security Groups, NACLs, IAM deny policies, backups |
| 2.2.5: Conduct root cause analysis | **Amazon Detective** |

### New in SCS-C03
- **Skill 2.1.3**: Testing incident response with **AWS Fault Injection Service** and **AWS Resilience Hub**
- **Skill 2.1.4**: **Automated Forensics Orchestrator for Amazon EC2** and **Amazon Application Recovery Controller**
- **Skill 2.2.3**: Validate findings to assess scope and impact of an event

---

## Key Services

| Service | Purpose |
|---------|---------|
| **Amazon Detective** | Security investigation and root cause analysis |
| **AWS Security Hub** | Central finding aggregation and automation |
| **Amazon EventBridge** | Event-driven automation for responses |
| **AWS Lambda** | Automated remediation actions |
| **AWS Systems Manager** | Runbook automation (OpsCenter, Automation, Incident Manager) |
| **AWS Step Functions** | Orchestration of incident response workflows |
| **AWS Fault Injection Service** | Chaos engineering to test incident response plans |
| **AWS Resilience Hub** | Assess and improve application resilience |
| **Automated Forensics Orchestrator for EC2** | Automated forensic evidence collection |
| **Amazon Application Recovery Controller** | Application recovery readiness and routing control |
| **AWS Shield Advanced** | DDoS protection with incident response support (DRT) |
| **Amazon SageMaker AI** | Notebooks for incident investigation and analysis |

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

## 💥 AWS Fault Injection Service (Skill 2.1.3)

### What You Need to Know

- **Chaos engineering service** for testing resilience and incident response plans
- Previously known as **AWS Fault Injection Simulator (FIS)**
- Runs controlled **experiments** that inject faults into your AWS resources
- Supports **stop conditions** to halt experiments if thresholds are breached
- Uses **experiment templates** that define actions, targets, and stop conditions

### Supported Fault Actions

| Target | Example Faults |
|--------|---------------|
| **EC2** | Stop/terminate instances, inject CPU/memory stress, network disruption |
| **ECS** | Stop tasks, drain container instances |
| **EKS** | Terminate pods, inject node faults |
| **RDS** | Failover DB instances, reboot |
| **Network** | Disrupt connectivity, add latency, packet loss |
| **Systems Manager** | Run SSM documents as fault actions |
| **IAM** | Test permission boundary scenarios |

### Security & Incident Response Use Cases

- **Validate incident response runbooks**: Inject faults and verify automated responses trigger correctly
- **Test blast radius controls**: Verify isolation mechanisms contain failures
- **Validate monitoring and alerting**: Confirm GuardDuty, CloudWatch alarms, and Security Hub detect injected issues
- **GameDay exercises**: Controlled security simulations with real fault injection
- **Compliance testing**: Demonstrate disaster recovery and incident response capabilities

### IAM Permissions

- FIS requires an **IAM experiment role** with permissions to inject faults
- Follow least privilege: only grant permissions for specific target resources
- Use **stop conditions** (CloudWatch alarms) to automatically halt experiments

📖 **Documentation**: [AWS Fault Injection Service User Guide](https://docs.aws.amazon.com/fis/latest/userguide/what-is.html)  
📖 **Experiment Templates**: [Creating experiment templates](https://docs.aws.amazon.com/fis/latest/userguide/experiment-templates.html)

---

## 🏥 AWS Resilience Hub (Skill 2.1.3)

### What You Need to Know

- **Assess, track, and improve** application resilience posture
- Define **Recovery Time Objective (RTO)** and **Recovery Point Objective (RPO)** targets
- Automatically discovers application resources and dependencies
- Generates **resiliency recommendations** based on assessment results
- Integrates with **AWS Fault Injection Service** for testing

### Security & Incident Response Use Cases

- Set resilience policies for critical security infrastructure
- Assess whether incident response systems meet RTO/RPO requirements
- Generate test recommendations that can be executed with FIS
- Continuous monitoring of resilience posture drift

📖 **Documentation**: [Resilience Hub User Guide](https://docs.aws.amazon.com/resilience-hub/latest/userguide/what-is.html)

---

## 🖥️ AWS Systems Manager OpsCenter (Skill 2.1.1)

### What You Need to Know

- **Centralized operations management** for viewing, investigating, and resolving operational issues
- **OpsItems**: Work items for operational issues, linked to relevant resources
- Automatically creates OpsItems from **CloudWatch Alarms**, **Config rules**, **Security Hub findings**
- Integrates with **Systems Manager Automation** for runbook-based remediation
- **Cross-account and cross-region** OpsItem aggregation

### Security & Incident Response Use Cases

- Central pane-of-glass for security incident tracking
- Link OpsItems to runbooks for automated or guided remediation
- Track incident response actions with timestamps and context
- Integrate with EventBridge for automated OpsItem creation from security events

📖 **Documentation**: [OpsCenter User Guide](https://docs.aws.amazon.com/systems-manager/latest/userguide/OpsCenter.html)

---

## 🔬 Automated Forensics Orchestrator for Amazon EC2 (Skill 2.1.4)

### What You Need to Know

- **AWS Solution** (not a standalone service) for automating forensic evidence collection from EC2 instances
- Triggered by **Security Hub findings** or **GuardDuty** alerts
- Automates: memory acquisition, disk snapshot, instance isolation, metadata collection
- Uses **Step Functions** for orchestration and **Lambda** for individual actions
- Preserves **chain of custody** with S3 Object Lock and CloudTrail logging
- Deploys via **CloudFormation template**

### Key Capabilities

- Automatic instance isolation (quarantine security group)
- EBS volume snapshot for disk forensics
- Memory acquisition using SSM Run Command
- Evidence stored in a dedicated forensic S3 bucket with encryption

📖 **Documentation**: [Automated Forensics Orchestrator](https://aws.amazon.com/solutions/implementations/automated-forensics-orchestrator-for-amazon-ec2/)

---

## 🔄 Amazon Application Recovery Controller (Skill 2.1.4)

### What You Need to Know

- **Readiness checks**: Verify that recovery configurations are in place
- **Routing controls**: Shift traffic between Regions/AZs during incidents
- **Safety rules**: Prevent accidental routing changes (e.g., require at least one healthy cell)
- Works with **Route 53 health checks** for DNS-based failover

### Security & Incident Response Use Cases

- Controlled failover during security incidents (e.g., move traffic away from compromised region)
- Verify recovery readiness for critical security services
- Implement safety rules to prevent human error during incident response

📖 **Documentation**: [Application Recovery Controller User Guide](https://docs.aws.amazon.com/r53recovery/latest/dg/what-is-route53-recovery.html)

---

## 🛡️ AWS Shield Advanced (Skill 2.1.2)

### Incident Response Relevance

- **DDoS Response Team (DRT)**: 24/7 access to AWS experts during DDoS incidents
- **Proactive engagement**: DRT contacts you during detected DDoS events
- **Cost protection**: Credits for scaling charges incurred during DDoS attacks
- **Health-based detection**: Integrates with Route 53 health checks for faster detection
- **Automatic application layer DDoS mitigation**: Creates WAF rules automatically

### Preparation (Skill 2.1.2)

- Pre-configure Shield Advanced on critical resources (CloudFront, ALB, Route 53, Elastic IP)
- Set up DRT access by creating an IAM role and S3 bucket for log sharing
- Configure health checks for proactive engagement
- Define emergency contacts for DRT communication

📖 **Documentation**: [Shield Advanced Incident Response](https://docs.aws.amazon.com/waf/latest/developerguide/ddos-responding.html)

---

## 📓 Amazon SageMaker AI Notebooks (Skill 2.1.1)

### Incident Response Use Cases

- **Jupyter notebooks** for ad-hoc security investigation and data analysis
- Query and visualize CloudTrail, VPC Flow Logs, and GuardDuty data
- Run Python-based forensic analysis scripts
- Build and share investigation runbooks as executable notebooks
- Collaborative incident investigation with shared notebook instances

📖 **Documentation**: [SageMaker Notebook Instances](https://docs.aws.amazon.com/sagemaker/latest/dg/nbi.html)

---

## 📖 Key Documentation Links

- [AWS Security Incident Response Guide - Introduction](https://docs.aws.amazon.com/whitepapers/latest/aws-security-incident-response-guide/introduction.html)
- [Threat Detection - AWS CAF Security Perspective](https://docs.aws.amazon.com/whitepapers/latest/aws-caf-security-perspective/threat-detection.html)
- [AWS Security Incident Response Guide (Full)](https://docs.aws.amazon.com/whitepapers/latest/aws-security-incident-response-guide/)
- [AWS Fault Injection Service User Guide](https://docs.aws.amazon.com/fis/latest/userguide/what-is.html)
- [AWS Resilience Hub User Guide](https://docs.aws.amazon.com/resilience-hub/latest/userguide/what-is.html)
- [Automated Forensics Orchestrator for Amazon EC2](https://aws.amazon.com/solutions/implementations/automated-forensics-orchestrator-for-amazon-ec2/)

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
- Know **AWS Fault Injection Service** for testing incident response plans and runbooks (Skill 2.1.3)
- Understand **Resilience Hub** for assessing RTO/RPO of incident response infrastructure (Skill 2.1.3)
- Know **Automated Forensics Orchestrator** for automated EC2 evidence collection (Skill 2.1.4)
- Understand **Application Recovery Controller** for controlled failover during incidents (Skill 2.1.4)
- Know **OpsCenter** for centralized incident tracking and runbook integration (Skill 2.1.1)
- Understand **Shield Advanced** DRT access and proactive engagement for DDoS response (Skill 2.1.2)

---

*Last updated: January 2026 (SCS-C03)*
