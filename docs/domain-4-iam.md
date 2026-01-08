# Domain 4: Identity & Access Management (16%)

> 🚧 **Status:** In Progress

## Overview

This domain covers identity management, access control, and federation in AWS.

---

## Key Services

| Service | Purpose |
|---------|---------|
| **AWS IAM** | Users, groups, roles, policies |
| **IAM Identity Center** | Centralized SSO (formerly AWS SSO) |
| **AWS Organizations** | Multi-account management |
| **AWS STS** | Temporary security credentials |
| **Amazon Cognito** | User identity for applications |
| **IAM Access Analyzer** | Analyze resource access |

---

## 🔑 AWS IAM

### Policy Evaluation Logic

1. **Explicit Deny** → DENY
2. **Organization SCP** → must allow
3. **Resource-based policy** → may allow
4. **Identity-based policy** → may allow
5. **IAM Permissions Boundary** → must allow
6. **Session policy** → must allow
7. **Implicit Deny** → DENY

### Policy Types

| Type | Attached To | Use Case |
|------|-------------|----------|
| **Identity-based** | Users, Groups, Roles | Grant permissions |
| **Resource-based** | Resources (S3, KMS, etc.) | Cross-account access |
| **Permissions Boundaries** | Users, Roles | Delegate permission management |
| **SCPs** | OUs, Accounts | Restrict maximum permissions |
| **Session Policies** | STS sessions | Limit session permissions |

### Best Practices

- Enable MFA for all users
- Use roles for applications
- Grant least privilege
- Use groups for permissions
- Rotate credentials regularly
- Remove unused credentials

### Key Documentation Links

- [Security best practices and use cases in IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices-use-cases.html)
- [Security best practices in IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html)
- [IAM users](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users.html)
- [What is IAM?](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html)
- [IAM roles](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles.html)

📖 **Documentation**: [IAM Best Practices](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html)

---

## 🏢 AWS Organizations

### Service Control Policies (SCPs)

- **Maximum permissions** for accounts in OU
- **Do not grant permissions** - only restrict
- **Don't affect management account**
- **Inheritance**: Parent → Child

### Common SCP Patterns

```json
// Deny all regions except specific ones
{
  "Effect": "Deny",
  "Action": "*",
  "Resource": "*",
  "Condition": {
    "StringNotEquals": {
      "aws:RequestedRegion": ["us-east-1", "eu-west-1"]
    }
  }
}
```

### Key Documentation Links

- [Service Control Policies (SCPs)](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_scps.html)
- [SCP examples](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_scps_examples.html)
- [Management policies](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_management_policies.html)
- [Choosing an AWS cloud governance service](https://docs.aws.amazon.com/decision-guides/latest/cloud-governance-on-aws-how-to-choose/cloud-governance-on-aws-how-to-choose.html)

📖 **Documentation**: [SCPs User Guide](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_scps.html)

---

## 🔐 IAM Identity Center (AWS SSO)

### What You Need to Know (Renamed for SCS-C02)

- **Centralized access** to multiple AWS accounts
- **Identity sources**: Identity Center directory, AD Connector, external IdP
- **Permission sets**: Collections of IAM policies
- **SAML 2.0** and **OIDC** federation

📖 **Documentation**: [IAM Identity Center User Guide](https://docs.aws.amazon.com/singlesignon/latest/userguide/)

---

## 🎫 AWS STS

### Temporary Credentials

- **AssumeRole**: For AWS resources or cross-account
- **AssumeRoleWithSAML**: For SAML federation
- **AssumeRoleWithWebIdentity**: For web/mobile apps
- **GetSessionToken**: For MFA-protected API access
- **GetFederationToken**: For federated users

### Cross-Account Access

1. Create role in target account with trust policy
2. Grant assume role permission in source account
3. Use STS AssumeRole to get temporary credentials

📖 **Documentation**: [STS User Guide](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_temp.html)

---

## 👤 Amazon Cognito

### User Pools

- **User directory** for sign-up/sign-in
- **MFA support**
- **Lambda triggers** for customization
- **JWT tokens** for authentication

### Identity Pools

- **Federated identities** (Google, Facebook, SAML, etc.)
- **Temporary AWS credentials**
- **Guest access** support

📖 **Documentation**: [Cognito User Guide](https://docs.aws.amazon.com/cognito/latest/developerguide/)

---

## 🔍 IAM Access Analyzer

### What You Need to Know

- Identifies resources shared with **external entities**
- **Zone of trust**: Account or Organization
- **Findings**: Resources accessible outside zone of trust
- **Policy validation**: Check policies for errors
- **Policy generation**: Generate policies from CloudTrail

📖 **Documentation**: [Access Analyzer User Guide](https://docs.aws.amazon.com/IAM/latest/UserGuide/what-is-access-analyzer.html)

---

## 📺 Recommended Videos

- [AWS re:Inforce 2022: Security best practices with AWS IAM (IAM201)](https://www.youtube.com/watch?v=SMjvtxXOXdU)
- [AWS re:Invent 2022: Harness power of IAM policies with Access Analyzer (SEC313)](https://www.youtube.com/watch?v=x-Kh8hKVX74)
- [AWS re:Invent 2018: Become an IAM Policy Master (SEC316-R1)](https://www.youtube.com/watch?v=YQsK4MtsELU)

---

## ✅ Exam Tips

- Memorize the policy evaluation order
- Know the difference between policy types
- Understand SCPs (don't grant, only restrict)
- Know cross-account access patterns
- Understand Cognito User Pools vs Identity Pools
- Know Access Analyzer zone of trust concept

---

*Last updated: January 2026*
