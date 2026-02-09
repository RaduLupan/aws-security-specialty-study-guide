# Domain 6: Management & Security Governance (14%)

> 🚧 **Status:** In Progress

## Overview

This domain covers security governance, compliance, multi-account strategies, and secure deployment in AWS.

---

## Task Statements & Skills (SCS-C03)

### Task 6.1: Develop a strategy to centrally deploy and manage AWS accounts

| Skill | Key Services |
|-------|-------------|
| 6.1.1: Deploy and configure organizations | **AWS Organizations** |
| 6.1.2: Implement and manage AWS Control Tower, deploy optional and custom controls | **AWS Control Tower** |
| 6.1.3: Implement organization policies to manage permissions | **SCPs, RCPs (Resource Control Policies), AI service opt-out policies, declarative policies** |
| 6.1.4: Centrally manage security services | **Delegated administrator accounts** |
| 6.1.5: Manage AWS account root user credentials | **Centralized root access, MFA, break-glass procedures** |

### Task 6.2: Implement a secure and consistent deployment strategy for cloud resources

| Skill | Key Services |
|-------|-------------|
| 6.2.1: Use IaC to deploy cloud resources consistently and securely | **CloudFormation stack sets, CloudFormation Guard, cfn-lint, third-party IaC** |
| 6.2.2: Use tags to organize AWS resources into groups for management | Tag policies, cost center/environment/department tagging |
| 6.2.3: Deploy and enforce policies and configurations from a central source | **AWS Firewall Manager** |
| 6.2.4: Securely share resources across AWS accounts | **AWS Service Catalog, AWS Resource Access Manager (RAM)** |

### Task 6.3: Evaluate the compliance of AWS resources

| Skill | Key Services |
|-------|-------------|
| 6.3.1: Create or enable rules to detect and remediate noncompliant resources | **AWS Config, Security Hub** |
| 6.3.2: Use AWS audit services to collect and organize evidence | **AWS Audit Manager, AWS Artifact** |
| 6.3.3: Evaluate architecture for compliance with AWS security best practices | **AWS Well-Architected Framework tool** |

---

## Key Services

| Service | Purpose |
|---------|---------|
| **AWS Control Tower** | Multi-account landing zone |
| **AWS Organizations** | Account management and governance |
| **AWS Config** | Compliance monitoring and remediation |
| **AWS Audit Manager** | Audit evidence collection |
| **AWS Artifact** | Compliance reports and agreements |
| **AWS CloudFormation** | Infrastructure as Code (stack sets, Guard, cfn-lint) |
| **AWS Firewall Manager** | Central security policy deployment |
| **AWS Service Catalog** | Governed self-service resource provisioning |
| **AWS Resource Access Manager (RAM)** | Cross-account resource sharing |
| **AWS Security Hub** | Compliance standards evaluation |
| **AWS Well-Architected Tool** | Architecture review against best practices |

---

## 🏗️ AWS Control Tower

### What You Need to Know

- **Automated landing zone** setup
- **Account Factory**: Provision new accounts
- **Guardrails**: Preventive (SCPs) and Detective (Config rules)
- **Dashboard**: Compliance visibility

### Guardrail / Controls Categories

| Category | Type | Enforcement |
|----------|------|-------------|
| **Mandatory** | Preventive | Always on |
| **Strongly Recommended** | Preventive/Detective | Best practice |
| **Elective** | Preventive/Detective | Optional |

### Control Types

| Type | Mechanism | Example |
|------|-----------|---------|
| **Preventive** | SCPs | Block actions before they happen |
| **Detective** | Config Rules | Identify non-compliant resources |
| **Proactive** | CloudFormation Hooks | Validate resources before provisioning |

### Shared Accounts

- **Management Account**: Root of organization
- **Log Archive Account**: Centralized logging
- **Audit Account**: Cross-account security access

### Key Documentation Links

- [Security Pillar - Welcome](https://docs.aws.amazon.com/wellarchitected/latest/security-pillar/welcome.html)
- [Security overview in Well-Architected](https://docs.aws.amazon.com/wellarchitected/latest/framework/security.html)
- [Well-Architected Framework overview](https://docs.aws.amazon.com/wellarchitected/latest/framework/welcome.html)
- [Introduction to AWS Security](https://docs.aws.amazon.com/whitepapers/latest/introduction-aws-security/welcome.html)
- [Security and Compliance overview](https://docs.aws.amazon.com/whitepapers/latest/aws-overview/security-and-compliance.html)

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

## 📜 Organization Policy Types (Skill 6.1.3)

### Service Control Policies (SCPs)

- **Maximum permissions** for IAM principals in member accounts
- Do NOT grant permissions, only restrict
- Apply to OUs or individual accounts
- Do not affect the management account

### Resource Control Policies (RCPs) - NEW

- Control **maximum permissions for resources** in member accounts
- Complement SCPs: SCPs restrict principals, **RCPs restrict resources**
- Control what actions external principals can perform on resources in your accounts
- Example: Prevent cross-account access to S3 buckets except from allowed accounts

📖 **Documentation**: [Resource Control Policies](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_rcps.html)

### Declarative Policies - NEW

- Enforce **desired state** for AWS service configurations across an organization
- Currently supports: EC2 (e.g., enforce IMDSv2, block public AMIs)
- Apply at organization, OU, or account level
- Override individual account settings without per-account configuration

📖 **Documentation**: [Declarative Policies](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_declarative.html)

### AI Service Opt-Out Policies

- Control whether AWS AI services can store and use your content for **service improvement**
- Apply across organization to enforce consistent AI data usage policies
- Opt out of content processing for services like Lex, Polly, Comprehend, etc.

📖 **Documentation**: [AI Services Opt-Out Policies](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_ai-opt-out.html)

### Tag Policies (Skill 6.2.2)

- Enforce **consistent tagging** across organization accounts
- Define allowed tag keys, values, and case conventions
- Detect non-compliant tags (does not prevent resource creation)
- Useful for cost allocation, security grouping, and compliance

📖 **Documentation**: [Tag Policies](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_tag-policies.html)

### Root User Management (Skill 6.1.5)

- **Centralize root access** for member accounts in Organizations
- Perform **privileged actions** on behalf of member accounts without root credentials
- Enable **root MFA** for all accounts
- **Break-glass procedures**: Documented process for emergency root access
- Remove root credentials from member accounts where possible

📖 **Documentation**: [Centrally manage root access](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_root-user-manage-root-credentials.html)

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

### CloudFormation Guard (Skill 6.2.1)

- **Policy-as-code** validation tool for CloudFormation templates
- Write rules in **Guard DSL** to check templates before deployment
- Validates: resource properties, encryption enabled, public access blocked, etc.
- Run in **CI/CD pipeline** or locally during development
- Also works with **Terraform plans** (JSON format)

📖 **Documentation**: [CloudFormation Guard](https://docs.aws.amazon.com/cfn-guard/latest/ug/what-is-guard.html)

### cfn-lint (Skill 6.2.1)

- **CloudFormation linter** for validating template syntax and best practices
- Checks for resource specification compliance, deprecated properties, and errors
- Community-maintained with extensive rule set
- Run locally or in CI/CD

📖 **Repository**: [cfn-lint GitHub](https://github.com/aws-cloudformation/cfn-lint)

📖 **Documentation**: [CloudFormation Best Practices](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/best-practices.html)

---

## 🔥 AWS Firewall Manager (Skill 6.2.3)

### What You Need to Know

- **Centrally manage security policies** across multiple accounts in an organization
- Requires **AWS Organizations** and a **Firewall Manager administrator account**
- **Auto-remediation**: Automatically applies policies to new and existing resources

### Policy Types

| Policy Type | What It Manages |
|-------------|----------------|
| **WAF policies** | AWS WAF rules across accounts |
| **Shield Advanced** | DDoS protection enrollment |
| **Security Group** | Common/audit security groups across VPCs |
| **Network Firewall** | AWS Network Firewall rules across VPCs |
| **Route 53 Resolver DNS Firewall** | DNS filtering rules |
| **Third-party firewall** | Palo Alto, Fortigate policies |

📖 **Documentation**: [Firewall Manager User Guide](https://docs.aws.amazon.com/waf/latest/developerguide/fms-chapter.html)

---

## 📦 AWS Service Catalog (Skill 6.2.4)

### What You Need to Know

- **Governed self-service provisioning** of pre-approved AWS resources
- **Portfolios**: Collections of products shared with specific accounts/OUs
- **Products**: CloudFormation templates that users can deploy
- **Constraints**: Launch constraints (IAM role), template constraints (parameter limits), notification constraints
- **TagOption Library**: Enforce tags on provisioned products

### Security Use Cases

- Ensure teams only deploy approved, security-compliant resource configurations
- Use launch constraints to provision with specific IAM roles (least privilege)
- Share approved architectures across accounts via portfolio sharing

📖 **Documentation**: [Service Catalog Admin Guide](https://docs.aws.amazon.com/servicecatalog/latest/adminguide/)

---

## 🔗 AWS Resource Access Manager (RAM) (Skill 6.2.4)

### What You Need to Know

- **Securely share AWS resources** across accounts within an organization (or with external accounts)
- **Shareable resources**: VPC subnets, Transit Gateway, Route 53 Resolver rules, License Manager configs, and more
- Sharing within an organization does NOT require invitations (trusted access)
- **No data duplication**: Resources are shared in place, not copied

### Security Considerations

- Use **Organizations** integration to share only within your org (prevent external sharing)
- Monitor shared resources via **CloudTrail** and **Config**
- Apply SCPs to restrict which resources can be shared

📖 **Documentation**: [RAM User Guide](https://docs.aws.amazon.com/ram/latest/userguide/)

---

## 🏗️ AWS Well-Architected Tool (Skill 6.3.3)

### What You Need to Know

- **Evaluate architectures** against AWS Well-Architected Framework pillars
- **Security pillar**: IAM, detection, infrastructure protection, data protection, incident response
- **Workload reviews**: Answer questions to identify high-risk areas
- **Lenses**: Custom lenses for specific industry or technology requirements
- **Milestones**: Track improvement over time
- **Integration**: Links to remediation guidance and AWS documentation

### Security Pillar Focus Areas

| Area | Description |
|------|------------|
| **Security foundations** | AWS account management, operating securely |
| **Identity and access management** | Human and machine credentials |
| **Detection** | Detection controls and investigation |
| **Infrastructure protection** | Network and compute protection |
| **Data protection** | Data classification, encryption |
| **Incident response** | Preparation and simulation |

📖 **Documentation**: [Well-Architected Tool](https://docs.aws.amazon.com/wellarchitected/latest/userguide/)  
📖 **Security Pillar**: [Security Pillar Whitepaper](https://docs.aws.amazon.com/wellarchitected/latest/security-pillar/welcome.html)

---

## 📺 Recommended Videos

- [AWS re:Invent 2022: Setting up controls at scale (COP318)](https://www.youtube.com/watch?v=NkE9_okfPG8)

---

## ✅ Exam Tips

- Know Control Tower account structure and control types (preventive, detective, proactive)
- Understand guardrail types (preventive vs detective vs proactive)
- Know Config conformance packs use cases
- Understand delegated administrator concept
- Know Audit Manager evidence collection methods
- Understand SCP inheritance in OU hierarchy
- Know **Resource Control Policies (RCPs)** vs SCPs: RCPs restrict resources, SCPs restrict principals (Skill 6.1.3)
- Understand **declarative policies** for enforcing service configurations (e.g., IMDSv2) (Skill 6.1.3)
- Know **AI service opt-out policies** for controlling data use by AI services (Skill 6.1.3)
- Understand **CloudFormation Guard** for policy-as-code template validation (Skill 6.2.1)
- Know **Firewall Manager** policy types and auto-remediation (Skill 6.2.3)
- Understand **Service Catalog** for governed self-service provisioning (Skill 6.2.4)
- Know **RAM** for cross-account resource sharing within an org (Skill 6.2.4)
- Understand **Well-Architected Tool** Security Pillar for architecture reviews (Skill 6.3.3)
- Know **root user credential management** and centralized root access (Skill 6.1.5)

---

*Last updated: February 2026 (SCS-C03)*
