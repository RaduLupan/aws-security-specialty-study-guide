# Domain 6: Management & Security Governance (14%)

> 🚧 **Status:** In Progress

## Overview

This domain covers security governance, compliance, and multi-account strategies in AWS.

---

## Key Services

| Service | Purpose |
|---------|---------|
| **AWS Control Tower** | Multi-account landing zone |
| **AWS Organizations** | Account management and governance |
| **AWS Config** | Compliance monitoring |
| **AWS Audit Manager** | Audit evidence collection |
| **AWS Artifact** | Compliance reports |
| **AWS CloudFormation** | Infrastructure as Code |

---

## 🏗️ AWS Control Tower

### What You Need to Know

- **Automated landing zone** setup
- **Account Factory**: Provision new accounts
- **Guardrails**: Preventive (SCPs) and Detective (Config rules)
- **Dashboard**: Compliance visibility

### Guardrail Categories

| Category | Type | Enforcement |
|----------|------|-------------|
| **Mandatory** | Preventive | Always on |
| **Strongly Recommended** | Preventive/Detective | Best practice |
| **Elective** | Preventive/Detective | Optional |

### Shared Accounts

- **Management Account**: Root of organization
- **Log Archive Account**: Centralized logging
- **Audit Account**: Cross-account security access

📖 **Documentation**: [Control Tower User Guide](https://docs.aws.amazon.com/controltower/latest/userguide/)

---

## 🏢 AWS Organizations (Governance Focus)

### Organizational Units (OUs)

Recommended OU structure:

```
Root
├── Security OU
│   ├── Log Archive Account
│   └── Audit Account
├── Infrastructure OU
│   └── Shared Services Account
├── Sandbox OU
│   └── Developer Accounts
├── Workloads OU
│   ├── Prod OU
│   └── Non-Prod OU
└── Suspended OU
    └── Decommissioned Accounts
```

### Delegated Administrator

- Designate member accounts for service management
- Reduces management account usage
- Supported services: Security Hub, GuardDuty, Macie, Config, etc.

📖 **Documentation**: [Organizations Best Practices](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_best-practices.html)

---

## ⚙️ AWS Config (Compliance Focus)

### Conformance Packs

- **Collection of Config rules** as single entity
- **AWS-authored packs**: CIS, PCI DSS, HIPAA
- **Custom packs**: Your own rules
- **Organization-level deployment**

### Remediation

- **Manual remediation**: Guidance only
- **Automatic remediation**: SSM documents
- **Remediation exceptions**: Temporary exemptions

📖 **Documentation**: [Config Conformance Packs](https://docs.aws.amazon.com/config/latest/developerguide/conformance-packs.html)

---

## 📋 AWS Audit Manager

### What You Need to Know

- **Automated evidence collection** for audits
- **Framework library**: SOC 2, GDPR, HIPAA, PCI DSS
- **Custom frameworks**: Your own controls
- **Assessment reports**: Ready for auditors

### Evidence Sources

- CloudTrail logs
- Config rules
- Security Hub findings
- Manual evidence upload

📖 **Documentation**: [Audit Manager User Guide](https://docs.aws.amazon.com/audit-manager/latest/userguide/)

---

## 📄 AWS Artifact

### What You Need to Know

- **Compliance reports**: SOC, PCI, ISO, HIPAA
- **Agreement management**: BAA, NDA
- **On-demand access**: Download reports anytime

📖 **Documentation**: [Artifact User Guide](https://docs.aws.amazon.com/artifact/latest/ug/)

---

## 🏗️ Infrastructure as Code Security

### CloudFormation Security

- **StackSets**: Deploy across accounts/regions
- **Drift detection**: Identify configuration changes
- **Guard rules**: Policy-as-code validation
- **Change sets**: Preview changes before deployment

### Best Practices

- Use parameter constraints
- Enable termination protection
- Use IAM roles for deployments
- Validate templates before deployment

📖 **Documentation**: [CloudFormation Best Practices](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/best-practices.html)

---

## 📺 Recommended Videos

- [AWS re:Invent 2022: Setting up controls at scale (COP318)](https://www.youtube.com/watch?v=NkE9_okfPG8)

---

## ✅ Exam Tips

- Know Control Tower account structure
- Understand guardrail types (preventive vs detective)
- Know Config conformance packs use cases
- Understand delegated administrator concept
- Know Audit Manager evidence collection methods
- Understand SCP inheritance in OU hierarchy

---

*Last updated: January 2026*
