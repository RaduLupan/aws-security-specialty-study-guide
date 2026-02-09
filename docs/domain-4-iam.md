# Domain 4: Identity & Access Management (20%)

> 🚧 **Status:** In Progress  
> **SCS-C03 Update:** This is now the highest weighted domain at 20% (was 16% in SCS-C02)

## Overview

This domain covers identity management, access control, and federation in AWS.

---

## Task Statements & Skills (SCS-C03)

### Task 4.1: Design, implement, and troubleshoot authentication strategies

| Skill | Key Services |
|-------|-------------|
| 4.1.1: Design and establish identity solutions for human, application, and system authentication | **IAM Identity Center, Amazon Cognito, MFA, IdP integration** |
| 4.1.2: Configure mechanisms to issue temporary credentials | **AWS STS, Amazon S3 presigned URLs** |
| 4.1.3: Troubleshoot authentication issues | **CloudTrail, Amazon Cognito, IAM Identity Center permission sets, AWS Directory Service** |

### Task 4.2: Design, implement, and troubleshoot authorization strategies

| Skill | Key Services |
|-------|-------------|
| 4.2.1: Design and evaluate authorization controls for human, application, and system access | **Amazon Verified Permissions, IAM paths, IAM Roles Anywhere, resource policies (cross-account), IAM role trust policies** |
| 4.2.2: Design ABAC and RBAC strategies | Tag-based and attribute-based access control |
| 4.2.3: Design, interpret, and implement IAM policies following least privilege | **Permission boundaries, session policies** |
| 4.2.4: Analyze authorization failures to determine causes or effects | **IAM Policy Simulator, IAM Access Analyzer** |
| 4.2.5: Investigate and correct unintended permissions | **IAM Access Analyzer** |

---

## Key Services

| Service | Purpose |
|---------|---------|
| **AWS IAM** | Users, groups, roles, policies |
| **IAM Identity Center** | Centralized SSO (formerly AWS SSO) |
| **AWS Organizations** | Multi-account management |
| **AWS STS** | Temporary security credentials |
| **Amazon Cognito** | User identity for applications |
| **IAM Access Analyzer** | Analyze resource access and validate policies |
| **Amazon Verified Permissions** | Fine-grained authorization for applications (Cedar policy language) |
| **IAM Roles Anywhere** | IAM roles for workloads outside AWS |
| **AWS Directory Service** | Managed Active Directory and AD Connector |
| **IAM Policy Simulator** | Test and debug IAM policies |

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

### What You Need to Know

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

## ✅ Amazon Verified Permissions (Skill 4.2.1)

### What You Need to Know

- **Fine-grained authorization** service for applications
- Uses the **Cedar policy language** (developed by AWS) for expressive, auditable policies
- **Externalized authorization**: Remove authorization logic from application code
- **Policy stores**: Collections of Cedar policies for an application
- **Schema**: Define entity types, actions, and relationships
- Supports both **RBAC** and **ABAC** patterns in Cedar

### Key Concepts

| Concept | Description |
|---------|------------|
| **Policy Store** | Container for all policies related to an application |
| **Cedar Policies** | Allow/forbid rules defining who can do what on which resources |
| **Entities** | Principals (users), actions, and resources |
| **Schema** | Type definitions for entities and actions |
| **IsAuthorized API** | Runtime authorization check |

### Use Cases

- API authorization: determine if a user can perform an action on a resource
- Multi-tenant application authorization
- Replace complex application-side authorization logic with centralized policies
- Integrate with **Cognito** for user identity and **Verified Permissions** for authorization decisions

📖 **Documentation**: [Amazon Verified Permissions User Guide](https://docs.aws.amazon.com/verifiedpermissions/latest/userguide/)  
📖 **Cedar Language**: [Cedar Policy Language Reference](https://docs.cedarpolicy.com/)

---

## 🏢 AWS Directory Service (Skill 4.1.3)

### What You Need to Know

- **AWS Managed Microsoft AD**: Full Microsoft Active Directory in AWS
- **AD Connector**: Proxy to on-premises Active Directory (no caching)
- **Simple AD**: Samba-based basic AD (limited features)

### AWS Managed Microsoft AD

- Two-way **trust relationships** with on-premises AD
- Supports **Group Policy**, **Kerberos**, **LDAP**
- Integrates with: RDS for SQL Server, Amazon WorkSpaces, IAM Identity Center, FSx for Windows
- **Multi-Region replication** for low-latency access
- **Automatic patching** and **snapshot backups**

### AD Connector

- **Does not store directory data** in AWS
- Redirects requests to on-premises AD
- Use when you want to use existing on-premises AD for AWS authentication
- Supports MFA with existing RADIUS server

### Security & Troubleshooting (Skill 4.1.3)

- Verify VPC connectivity and DNS resolution between AD Connector and on-premises AD
- Check security group rules for LDAP (389), LDAPS (636), Kerberos (88), DNS (53)
- Monitor with CloudTrail and CloudWatch for authentication failures
- Use AD Connector health checks for connectivity status

📖 **Documentation**: [AWS Directory Service Admin Guide](https://docs.aws.amazon.com/directoryservice/latest/admin-guide/)

---

## 🌐 IAM Roles Anywhere (Skill 4.2.1)

### What You Need to Know

- Provides **temporary AWS credentials** to workloads **outside of AWS**
- Uses **X.509 certificates** issued by a trusted Certificate Authority (CA)
- **Trust anchors**: Reference to CA (ACM Private CA or external CA)
- **Profiles**: Define which IAM role to assume and session policies
- Eliminates need for **long-term access keys** for on-premises workloads

### Key Components

| Component | Description |
|-----------|------------|
| **Trust Anchor** | CA certificate that IAM Roles Anywhere trusts |
| **Profile** | Maps to an IAM role with optional session policies |
| **Subject** | The workload presenting a certificate |
| **CRL** | Certificate Revocation List for revoked certificates |

### Use Cases

- On-premises servers accessing AWS APIs without access keys
- Hybrid workloads that need temporary AWS credentials
- IoT devices or edge computing with certificate-based authentication

📖 **Documentation**: [IAM Roles Anywhere User Guide](https://docs.aws.amazon.com/rolesanywhere/latest/userguide/)

---

## 🧪 IAM Policy Simulator (Skill 4.2.4)

### What You Need to Know

- **Test IAM policies** without deploying them
- Simulate API calls to see if they would be allowed or denied
- Works with **identity-based**, **resource-based**, **SCPs**, and **permissions boundaries**
- Available as **console tool** and **API** (for automation)
- Use for **troubleshooting** access denied errors

### Use Cases

- Test new policies before attaching to users/roles
- Debug "Access Denied" errors by simulating the exact API call
- Validate SCPs don't block required operations
- Verify cross-account access configurations

📖 **Documentation**: [IAM Policy Simulator](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_testing-policies.html)

---

## 🔗 S3 Presigned URLs (Skill 4.1.2)

### What You Need to Know

- **Time-limited URLs** for S3 object access without AWS credentials
- Generated by IAM users or roles with S3 permissions
- **Expiration**: Configurable (default varies, max depends on credential type)
- Permissions of the presigned URL match the **generating identity's permissions**
- STS temporary credentials: URL expires when the **shorter** of URL expiration or token expiration

### Security Considerations

- Use short expiration times for sensitive content
- Presigned URLs can be used by anyone who has the URL (no additional auth)
- Audit generation via CloudTrail
- Consider using CloudFront signed URLs for broader distribution control

📖 **Documentation**: [S3 Presigned URLs](https://docs.aws.amazon.com/AmazonS3/latest/userguide/using-presigned-url.html)

---

## 🏷️ ABAC and RBAC Strategies (Skill 4.2.2)

### Attribute-Based Access Control (ABAC)

- Authorization based on **tags/attributes** attached to principals and resources
- Use `aws:PrincipalTag`, `aws:ResourceTag`, and `aws:RequestTag` condition keys
- **Scalable**: New resources automatically get correct permissions based on tags
- Fewer policies needed (one policy can cover many resources)

### Role-Based Access Control (RBAC)

- Authorization based on **job function/role** membership
- Create IAM policies per role (e.g., Admin, Developer, ReadOnly)
- More traditional approach, easier to understand
- Requires policy updates when new resources are added

### When to Use Each

| Criteria | ABAC | RBAC |
|----------|------|------|
| **Scale** | Better for large, dynamic environments | Better for smaller, static environments |
| **Policy count** | Fewer policies | More policies |
| **New resources** | Auto-covered by tags | Requires policy updates |
| **Auditing** | Tag-based audit trails | Role membership audit |

📖 **Documentation**: [ABAC for AWS](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction_attribute-based-access-control.html)

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
- Understand **Amazon Verified Permissions** and **Cedar policy language** for application-level authorization (Skill 4.2.1)
- Know **IAM Roles Anywhere** for providing temporary credentials to on-premises workloads (Skill 4.2.1)
- Understand **AWS Directory Service** types: Managed Microsoft AD vs AD Connector vs Simple AD (Skill 4.1.3)
- Know **IAM Policy Simulator** for testing and debugging policies (Skill 4.2.4)
- Understand **S3 presigned URLs** and their expiration behavior with STS credentials (Skill 4.1.2)
- Know **ABAC vs RBAC** patterns and when to use each (Skill 4.2.2)
- Understand **IAM paths** for organizing IAM resources (Skill 4.2.1)

---

*Last updated: January 2026 (SCS-C03)*
