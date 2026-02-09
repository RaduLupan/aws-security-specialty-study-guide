# Domain 5: Data Protection (18%)

> 🚧 **Status:** In Progress

## Overview

This domain covers data protection in transit, at rest, and management of confidential data, credentials, secrets, and cryptographic keys in AWS.

---

## Task Statements & Skills (SCS-C03)

### Task 5.1: Design and implement controls for data in transit

| Skill | Key Services |
|-------|-------------|
| 5.1.1: Design and configure mechanisms to require encryption when connecting to resources | **ELB security policies, TLS configurations** |
| 5.1.2: Design and configure mechanisms for secure and private access to resources | **AWS PrivateLink, VPC endpoints, AWS Client VPN, AWS Verified Access** |
| 5.1.3: Design and configure inter-resource encryption in transit | **Amazon EMR inter-node encryption, Amazon EKS, SageMaker AI, Nitro encryption** |

### Task 5.2: Design and implement controls for data at rest

| Skill | Key Services |
|-------|-------------|
| 5.2.1: Design, implement, and configure data encryption at rest | **AWS CloudHSM, AWS KMS, client-side/server-side encryption** |
| 5.2.2: Design and configure mechanisms to protect data integrity | **S3 Object Lock, S3 Glacier Vault Lock, versioning, digital code signing** |
| 5.2.3: Design automatic lifecycle management and retention solutions | **S3 Lifecycle policies, S3 Object Lock, Amazon EFS Lifecycle policies, Amazon FSx for Lustre backup policies** |
| 5.2.4: Design and configure secure data replication and backup solutions | **Amazon Data Lifecycle Manager, AWS Backup, ransomware protection, AWS DataSync** |

### Task 5.3: Design and implement controls to protect confidential data, credentials, secrets, and cryptographic key materials

| Skill | Key Services |
|-------|-------------|
| 5.3.1: Design management and rotation of credentials and secrets | **AWS Secrets Manager** |
| 5.3.2: Manage and use imported key material | **KMS imported key material, external key stores (XKS)** |
| 5.3.3: Describe differences between imported key material and AWS generated key material | KMS key material origins |
| 5.3.4: Mask sensitive data | **CloudWatch Logs data protection policies, Amazon SNS message data protection** |
| 5.3.5: Create and manage encryption keys and certificates across Regions | **AWS KMS customer managed keys, AWS Private Certificate Authority** |

---

## Key Services

| Service | Purpose |
|---------|---------|
| **AWS KMS** | Key management and encryption |
| **AWS CloudHSM** | Hardware security modules |
| **AWS Secrets Manager** | Secrets rotation and management |
| **AWS Certificate Manager** | SSL/TLS certificates |
| **AWS Private Certificate Authority** | Private CA for internal certificates |
| **Amazon Macie** | Data discovery and classification |
| **S3 Encryption** | Object encryption options |
| **AWS PrivateLink** | Private connectivity to services without internet |
| **AWS Client VPN** | Managed VPN for remote access |
| **AWS Verified Access** | Zero-trust access to applications |
| **Amazon Data Lifecycle Manager** | Automated EBS snapshot/AMI lifecycle |
| **AWS Backup** | Centralized backup across AWS services |
| **AWS DataSync** | Secure data transfer and replication |
| **S3 Object Lock / Glacier Vault Lock** | Immutable data storage (WORM) |
| **Amazon EFS** | Shared file storage with lifecycle policies |
| **Amazon FSx for Lustre** | High-performance file storage with backup policies |

---

## 🔐 AWS KMS

### Key Types

| Type | Management | Use Case |
|------|------------|----------|
| **AWS Managed Keys** | AWS manages | Default encryption for AWS services |
| **Customer Managed Keys** | You manage | Custom key policies, rotation control |
| **AWS Owned Keys** | AWS owns | Shared across accounts (SSE-S3) |

### Key Operations

- **Encrypt/Decrypt**: Up to 4KB of data
- **GenerateDataKey**: Create data key for client-side encryption
- **GenerateDataKeyWithoutPlaintext**: For envelope encryption

### Key Policies

```json
{
  "Effect": "Allow",
  "Principal": {"AWS": "arn:aws:iam::111122223333:role/ExampleRole"},
  "Action": [
    "kms:Encrypt",
    "kms:Decrypt",
    "kms:GenerateDataKey"
  ],
  "Resource": "*"
}
```

### Grants

- **Temporary permissions** without modifying key policy
- **GranteePrincipal**: Who receives permissions
- **RetiringPrincipal**: Who can retire the grant
- Use for **service integrations**

### Key Rotation

- **Automatic rotation**: Once per year (365 days)
- **On-demand rotation**: Manual rotation
- Old key material retained for decryption

### Key Documentation Links

- [AWS KMS best practices - Introduction](https://docs.aws.amazon.com/prescriptive-guidance/latest/aws-kms-best-practices/introduction.html)
- [Key management best practices](https://docs.aws.amazon.com/prescriptive-guidance/latest/aws-kms-best-practices/key-management.html)
- [AWS KMS keys concepts](https://docs.aws.amazon.com/kms/latest/developerguide/concepts.html)
- [Create symmetric encryption KMS key](https://docs.aws.amazon.com/kms/latest/developerguide/create-symmetric-cmk.html)
- [Best practices for KMS grants](https://docs.aws.amazon.com/kms/latest/developerguide/grant-best-practices.html)

📖 **Documentation**: [KMS Developer Guide](https://docs.aws.amazon.com/kms/latest/developerguide/)

---

## 🔒 AWS CloudHSM

### What You Need to Know

- **FIPS 140-2 Level 3** validated
- **Single-tenant HSM** in your VPC
- **You control keys** - AWS cannot access
- **Cluster for HA** - minimum 2 HSMs across AZs
- **Custom Key Store**: Integrate with KMS

### Use Cases

- SSL/TLS offloading
- PKCS#11, JCE, CNG interfaces
- Certificate authority (CA)
- Oracle TDE, SQL Server TDE

📖 **Documentation**: [CloudHSM User Guide](https://docs.aws.amazon.com/cloudhsm/latest/userguide/)

---

## 🤫 AWS Secrets Manager

### What You Need to Know

- **Automatic rotation** for RDS, Redshift, DocumentDB
- **Lambda-based rotation** for custom secrets
- **Cross-account access** via resource policies
- **Versioning**: AWSCURRENT, AWSPENDING, AWSPREVIOUS

### Rotation Process

1. **createSecret**: Create new secret version (AWSPENDING)
2. **setSecret**: Update database credentials
3. **testSecret**: Verify new credentials work
4. **finishSecret**: Move AWSPENDING to AWSCURRENT

### Key Documentation Links

- [What is AWS Secrets Manager?](https://docs.aws.amazon.com/secretsmanager/latest/userguide/intro.html)
- [Rotate Secrets Manager secrets](https://docs.aws.amazon.com/secretsmanager/latest/userguide/rotating-secrets.html)
- [Rotate external secrets](https://docs.aws.amazon.com/secretsmanager/latest/userguide/rotate-secrets_external.html)
- [Secrets in Lambda functions](https://docs.aws.amazon.com/secretsmanager/latest/userguide/retrieving-secrets_lambda.html)
- [Manage credentials pattern](https://docs.aws.amazon.com/prescriptive-guidance/latest/patterns/manage-credentials-using-aws-secrets-manager.html)

📖 **Documentation**: [Secrets Manager User Guide](https://docs.aws.amazon.com/secretsmanager/latest/userguide/)

---

## 📜 AWS Certificate Manager (ACM)

### What You Need to Know

- **Free public certificates** for AWS services
- **Automatic renewal** for ACM-issued certificates
- **Import external certificates** (you manage renewal)
- **Private CA**: ACM Private Certificate Authority

### Integration Points

- CloudFront
- Elastic Load Balancer
- API Gateway
- Elastic Beanstalk

📖 **Documentation**: [ACM User Guide](https://docs.aws.amazon.com/acm/latest/userguide/)

---

## 🔍 Amazon Macie

### What You Need to Know

- **Discovers sensitive data** in S3 (PII, PHI, financial)
- **Machine learning** for data classification
- **Findings** in Security Hub
- **Managed data identifiers**: 100+ predefined
- **Custom data identifiers**: Regex patterns

📖 **Documentation**: [Macie User Guide](https://docs.aws.amazon.com/macie/latest/user/)

---

## 🔒 AWS Private Certificate Authority (Skill 5.3.5)

### What You Need to Know

- **Managed private CA** for issuing and managing private certificates
- Supports **X.509 certificates** for internal services, IoT devices, and code signing
- **Certificate hierarchies**: Root CA and subordinate CAs
- **Short-lived certificates**: Mode for cost-effective ephemeral certificates
- Integrates with **ACM** for automatic deployment to AWS services
- **Cross-Region**: Can issue certificates for resources in any region

### Use Cases

- Internal TLS between microservices
- Mutual TLS (mTLS) authentication
- Code signing certificates
- IoT device certificates
- **IAM Roles Anywhere** trust anchors

📖 **Documentation**: [AWS Private CA User Guide](https://docs.aws.amazon.com/privateca/latest/userguide/)

---

## 📦 S3 Encryption Options

| Type | Key Storage | Key Management |
|------|-------------|----------------|
| **SSE-S3** | AWS | AWS |
| **SSE-KMS** | AWS KMS | You control policy |
| **SSE-C** | Customer-provided | Customer |
| **Client-side** | Customer | Customer |

### S3 Bucket Keys

- Reduces KMS requests for SSE-KMS
- Saves costs
- Reduces CloudTrail events

📖 **Documentation**: [S3 Encryption](https://docs.aws.amazon.com/AmazonS3/latest/userguide/UsingEncryption.html)

---

## 🔐 Data Integrity & Immutability (Skill 5.2.2)

### S3 Object Lock

- **WORM (Write Once Read Many)** protection for S3 objects
- **Retention modes**:
  - **Governance mode**: Users with special permissions can override
  - **Compliance mode**: No one can delete or modify, including root account
- **Legal hold**: Independent hold on object (no expiration date)
- Requires **versioning** enabled on the bucket

### S3 Glacier Vault Lock

- **Immutable vault policy** for Glacier archives
- Once locked, policy **cannot be changed or deleted**
- Use for regulatory compliance (e.g., SEC Rule 17a-4)
- Time-based retention controls

### Digital Code Signing

- **AWS Signer**: Managed code signing for Lambda, IoT, container images
- Validates code integrity and publisher identity
- Signing profiles define cryptographic algorithms and validity periods

📖 **S3 Object Lock**: [Object Lock Documentation](https://docs.aws.amazon.com/AmazonS3/latest/userguide/object-lock.html)  
📖 **Glacier Vault Lock**: [Vault Lock Documentation](https://docs.aws.amazon.com/amazonglacier/latest/dev/vault-lock.html)  
📖 **AWS Signer**: [AWS Signer Documentation](https://docs.aws.amazon.com/signer/latest/developerguide/)

---

## 🔗 Data in Transit - Secure Access (Skill 5.1.2)

### AWS PrivateLink

- Access AWS services and third-party services **privately** (no internet gateway, NAT, VPN)
- Creates **interface VPC endpoints** with private IP addresses in your VPC
- Traffic stays on **AWS backbone network**
- Use for: accessing SaaS services, cross-account service access, compliance-sensitive workloads

📖 **Documentation**: [AWS PrivateLink](https://docs.aws.amazon.com/vpc/latest/privatelink/)

### AWS Client VPN

- **Managed VPN service** for remote access to AWS and on-premises resources
- **OpenVPN-based** client
- Supports **Active Directory** and **SAML-based** authentication
- **Mutual TLS** certificate authentication
- Authorization rules control access to specific networks
- Split-tunnel or full-tunnel modes

📖 **Documentation**: [Client VPN Admin Guide](https://docs.aws.amazon.com/vpn/latest/clientvpn-admin/)

### ELB Security Policies (Skill 5.1.1)

- **Predefined security policies** define TLS versions and cipher suites
- **ALB/NLB**: Choose policy to control minimum TLS version (e.g., TLS 1.2, TLS 1.3)
- **Forward secrecy**: Use ECDHE-based cipher suites
- Enforce HTTPS-only with HTTP-to-HTTPS redirect rules

📖 **Documentation**: [ELB Security Policies](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/create-https-listener.html)

---

## 🔒 Inter-Resource Encryption in Transit (Skill 5.1.3)

### Nitro System Encryption

- **Automatic encryption** of traffic between Nitro-based EC2 instances
- No application changes required
- Encrypted at the **hardware level** (Nitro Card)
- Applies to traffic within the same VPC and across peered VPCs

### Service-Specific Encryption in Transit

| Service | Encryption Feature |
|---------|-------------------|
| **Amazon EMR** | In-transit encryption with TLS for inter-node communication |
| **Amazon EKS** | Envelope encryption for Kubernetes secrets, pod-to-pod encryption |
| **SageMaker AI** | Inter-container encryption for training jobs |
| **Amazon RDS** | SSL/TLS for client connections, encrypted replication |

📖 **Nitro Encryption**: [Encryption in Transit on EC2](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/data-protection.html)

---

## 📂 Lifecycle Management & Retention (Skill 5.2.3)

### S3 Lifecycle Policies

- **Transition actions**: Move objects between storage classes (Standard -> IA -> Glacier)
- **Expiration actions**: Delete objects after specified days
- Can apply to specific prefixes or tags
- Use with Object Lock for combined retention + lifecycle management

### Amazon EFS Lifecycle Policies

- Transition files between **Standard** and **Infrequent Access (IA)** storage classes
- Based on **last access time** (e.g., move to IA after 30 days)
- Reduces storage costs automatically

### Amazon FSx for Lustre Backup Policies

- **Automatic daily backups** with configurable retention (0-90 days)
- **Manual backups** for point-in-time recovery
- Backups stored in S3 with encryption

📖 **S3 Lifecycle**: [Managing S3 Lifecycle](https://docs.aws.amazon.com/AmazonS3/latest/userguide/object-lifecycle-mgmt.html)  
📖 **EFS Lifecycle**: [EFS Lifecycle Management](https://docs.aws.amazon.com/efs/latest/ug/lifecycle-management-efs.html)

---

## 💾 Backup & Replication Security (Skill 5.2.4)

### AWS Backup

- **Centralized backup** for EC2, EBS, RDS, DynamoDB, EFS, FSx, S3, and more
- **Backup policies**: Define schedules, retention, lifecycle rules
- **Backup Vault Lock**: WORM protection for backups (compliance mode)
- **Cross-account backup**: Copy backups to another account for ransomware protection
- **Cross-Region backup**: Copy backups to another region for disaster recovery
- **Backup Audit Manager**: Audit backup compliance

### Amazon Data Lifecycle Manager

- Automate **EBS snapshot** and **AMI** creation, retention, and deletion
- **Lifecycle policies**: Schedule-based or event-based
- **Cross-account copy**: Share snapshots with other accounts
- Supports **fast snapshot restore** for critical volumes

### AWS DataSync

- **Secure data transfer** between on-premises storage and AWS (S3, EFS, FSx)
- **In-transit encryption** (TLS) automatic
- **At-rest encryption** at destination
- **Data integrity verification** with checksums
- Bandwidth throttling and scheduling controls

📖 **AWS Backup**: [AWS Backup Developer Guide](https://docs.aws.amazon.com/aws-backup/latest/devguide/)  
📖 **Backup Vault Lock**: [Backup Vault Lock](https://docs.aws.amazon.com/aws-backup/latest/devguide/vault-lock.html)  
📖 **Data Lifecycle Manager**: [DLM User Guide](https://docs.aws.amazon.com/dlm/latest/APIReference/Welcome.html)  
📖 **DataSync**: [DataSync User Guide](https://docs.aws.amazon.com/datasync/latest/userguide/)

---

## 🔑 Imported Key Material & External Key Stores (Skills 5.3.2, 5.3.3)

### Imported Key Material

- Bring your **own key material** into KMS (BYOK)
- **You control** the key material lifecycle (can set expiration date)
- Key material can be **deleted and re-imported**
- **Limitations**: No automatic rotation, no export, manual rotation only
- If you delete imported key material, the KMS key becomes **unusable** until re-import

### AWS vs Imported Key Material Comparison

| Feature | AWS Generated | Imported |
|---------|--------------|----------|
| **Rotation** | Automatic (annual) | Manual only |
| **Availability** | AWS guarantees durability | You must maintain backup |
| **Expiration** | No expiration | Optional expiration date |
| **Deletion** | 7-30 day waiting period | Immediate (key material only) |

### External Key Store (XKS)

- Use KMS keys backed by keys **outside AWS** (your own HSM or key manager)
- **XKS proxy**: Component you manage that connects KMS to your external key manager
- Meets requirements for keys that must never leave your control
- Higher latency due to external key operations

📖 **Imported Keys**: [Importing Key Material](https://docs.aws.amazon.com/kms/latest/developerguide/importing-keys.html)  
📖 **External Key Store**: [External Key Store](https://docs.aws.amazon.com/kms/latest/developerguide/keystore-external.html)

---

## 🛡️ Sensitive Data Masking (Skill 5.3.4)

### CloudWatch Logs Data Protection Policies

- **Automatically detect and mask** sensitive data in log events
- Supports PII patterns: email, SSN, credit card numbers, etc.
- Uses **managed data identifiers** or custom patterns
- Masked data shown as `[REDACTED]` in log output
- Can send unmasked data to a specific audit destination

### Amazon SNS Message Data Protection

- **Audit, mask, or block** sensitive data in SNS messages
- Apply data protection policies to SNS topics
- Detects PII in message payloads using data identifiers
- Actions: **Audit** (log findings), **De-identify** (mask), **Deny** (block message)

📖 **CloudWatch Data Protection**: [Protect Sensitive Log Data](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/mask-sensitive-log-data.html)  
📖 **SNS Data Protection**: [SNS Message Data Protection](https://docs.aws.amazon.com/sns/latest/dg/sns-message-data-protection.html)

---

## 📺 Recommended Videos

- [AWS re:Invent 2022: Protecting secrets, keys, and data (SEC403)](https://www.youtube.com/watch?v=9vr3oMODIUE)
- [AWS re:Invent 2022: Amazon S3 security best practices (STG301)](https://www.youtube.com/watch?v=VeE-O0imUVY)
- [AWS re:Inforce 2019: Achieving Security Goals with CloudHSM (SDD333)](https://www.youtube.com/watch?v=_gezaWmwzYY)

---

## ✅ Exam Tips

- Know KMS key types and when to use each
- Understand envelope encryption
- Know difference between KMS and CloudHSM
- Understand Secrets Manager rotation Lambda steps
- Know S3 encryption options and their characteristics
- Understand ACM certificate types and renewal
- Know **AWS PrivateLink** and **VPC endpoints** for private access to services (Skill 5.1.2)
- Understand **S3 Object Lock** (Governance vs Compliance mode) and **Glacier Vault Lock** for immutability (Skill 5.2.2)
- Know **AWS Backup Vault Lock** for ransomware-resilient backups (Skill 5.2.4)
- Understand **imported key material** vs AWS-generated key material limitations (Skill 5.3.2-5.3.3)
- Know **External Key Store (XKS)** for keys that must remain outside AWS (Skill 5.3.2)
- Understand **CloudWatch Logs data protection** and **SNS message data protection** for masking PII (Skill 5.3.4)
- Know **AWS Private Certificate Authority** for private TLS certificates (Skill 5.3.5)
- Understand **Nitro encryption** for automatic inter-instance encryption (Skill 5.1.3)
- Know **Data Lifecycle Manager** for automated EBS snapshot management (Skill 5.2.4)
- Understand **ELB security policies** for enforcing TLS versions (Skill 5.1.1)
- Know **Client VPN** authentication options: AD, SAML, mutual TLS (Skill 5.1.2)

---

*Last updated: February 2026 (SCS-C03)*
