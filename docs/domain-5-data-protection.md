# Domain 5: Data Protection (18%)

> 🚧 **Status:** In Progress

## Overview

This domain covers encryption, key management, and data security in AWS.

---

## Key Services

| Service | Purpose |
|---------|---------|
| **AWS KMS** | Key management and encryption |
| **AWS CloudHSM** | Hardware security modules |
| **AWS Secrets Manager** | Secrets rotation and management |
| **AWS Certificate Manager** | SSL/TLS certificates |
| **Amazon Macie** | Data discovery and classification |
| **S3 Encryption** | Object encryption options |

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

---

*Last updated: January 2026*
