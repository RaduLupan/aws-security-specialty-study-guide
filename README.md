# 🔐 AWS Security Specialty Study Guide

<div align="center">

![AWS Security Specialty](https://img.shields.io/badge/AWS-Security%20Specialty-FF9900?style=for-the-badge&logo=amazon-aws&logoColor=white)
![Exam Code](https://img.shields.io/badge/Exam-SCS--C03-232F3E?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)
![Stars](https://img.shields.io/github/stars/RaduLupan/aws-security-specialty-study-guide?style=for-the-badge)
![Forks](https://img.shields.io/github/forks/RaduLupan/aws-security-specialty-study-guide?style=for-the-badge)

**A comprehensive, community-driven study guide for the AWS Certified Security - Specialty exam (SCS-C03)**

[📚 Study Materials](#-study-materials) • [🎮 Practice Quizzes](#-practice-quizzes) • [📺 Video Resources](#-video-resources) • [🤝 Contributing](#-contributing)

</div>

---

## 📋 About This Guide

This repository contains curated study materials, interactive quizzes, and resources for the **AWS Certified Security - Specialty (SCS-C03)** certification exam.

| Attribute | Details |
|-----------|---------|
| **Exam Code** | SCS-C03 (effective December 2, 2025) |
| **Format** | 65 questions (multiple choice, multiple response, ordering, matching) |
| **Duration** | 170 minutes |
| **Passing Score** | 750/1000 |
| **Cost** | $300 USD |
| **Validity** | 3 years |

### 🏆 Author's Certification Journey

| Year | Status | Exam Version |
|------|--------|--------------|
| 2020 | ✅ Initial Certification | SCS-C01 |
| 2023 | ✅ First Recertification | SCS-C01 |
| 2026 | ✅ Second Recertification | SCS-C03 |

> 💡 Fun fact: Skipped SCS-C02 entirely! C02 was only active from ~2024 to December 2025.

> 💡 See [archive/](./archive/) for previous years' study guides.

---

## 🎯 Exam Domains (SCS-C03)

The SCS-C03 exam covers six domains with updated weights:

| Domain | Weight | Key Topics |
|--------|--------|------------|
| **1. Detection** | 16% | GuardDuty, Security Hub, CloudTrail, CloudWatch, VPC Flow Logs |
| **2. Incident Response** | 14% | Incident Response Plans, Security Events, Forensics |
| **3. Infrastructure Security** | 18% | VPC, WAF, Shield, Network Firewall, Compute Security |
| **4. Identity & Access Management** | 20% | IAM, Organizations, SCPs, Federation, Identity Center |
| **5. Data Protection** | 18% | KMS, Secrets Manager, ACM, Macie, Encryption |
| **6. Security Foundations & Governance** | 14% | Control Tower, Organizations, Compliance, Audit |

---

## 📚 Study Materials

### Official AWS Resources (SCS-C03)

- 📄 [Exam Guide (SCS-C03)](https://docs.aws.amazon.com/aws-certification/latest/examguides/security-specialty-03.html)
- 🎓 [AWS Skill Builder Exam Prep Plan](https://skillbuilder.aws/category/exam-prep/security-specialty-scs-c03)
- 🔄 [Comparison: SCS-C02 vs SCS-C03](https://docs.aws.amazon.com/aws-certification/latest/examguides/security-specialty-03-appendix-b.html)
- 🌐 [AWS Certification Page](https://aws.amazon.com/certification/certified-security-specialty/)

### Domain-Specific Study Guides (SCS-C03)

| Domain | Study Guide | Status |
|--------|-------------|--------|
| Domain 1 | [Detection](./docs/domain-1-detection.md) | ✅ Complete |
| Domain 2 | [Incident Response](./docs/domain-2-incident-response.md) | ✅ Complete |
| Domain 3 | [Infrastructure Security](./docs/domain-3-infrastructure-security.md) | ✅ Complete |
| Domain 4 | [Identity & Access Management](./docs/domain-4-iam.md) | ✅ Complete |
| Domain 5 | [Data Protection](./docs/domain-5-data-protection.md) | ✅ Complete |
| Domain 6 | [Security Foundations & Governance](./docs/domain-6-governance.md) | ✅ Complete |

### AWS Whitepapers (Must Read)

1. 📖 [AWS Security Incident Response Guide](https://docs.aws.amazon.com/whitepapers/latest/aws-security-incident-response-guide/aws-security-incident-response-guide.html)
2. 📖 [AWS Well-Architected Framework - Security Pillar](https://docs.aws.amazon.com/wellarchitected/latest/security-pillar/welcome.html)
3. 📖 [AWS KMS Best Practices](https://d1.awsstatic.com/whitepapers/aws-kms-best-practices.pdf)
4. 📖 [AWS Best Practices for DDoS Resiliency](https://d1.awsstatic.com/whitepapers/Security/DDoS_White_Paper.pdf)
5. 📖 [NIST Cybersecurity Framework on AWS](https://d1.awsstatic.com/whitepapers/compliance/NIST_Cybersecurity_Framework_CSF.pdf)

---

## 🎮 Practice Quizzes

Interactive HTML-based quizzes with two modes:
- **📚 Learn Mode**: Immediate feedback after each question
- **📝 Exam Mode**: Timed assessment (2.5 min/question), all-at-once grading

### Features
- ✅ Questions sourced from official AWS documentation
- ✅ Detailed explanations with documentation links
- ✅ Pass/Fail scoring (80% threshold)
- ✅ Question and answer shuffling on restart
- ✅ No installation required - runs in any browser

### Available Quizzes

> **Total: 1,227 questions across 55 quizzes - ALL 6 DOMAINS COMPLETE!**

> **Plus 5 full-length practice exams (325 questions)!**

#### Domain 1: Detection -- 11 quizzes | 230 questions

| Topic | Questions | Quiz |
|-------|-----------|------|
| **Amazon GuardDuty** | 25 | [View](./quizzes/guardduty-comprehensive.html) |
| **GuardDuty Extended Threat Detection** | 15 | [View](./quizzes/guardduty-extended-threat-detection.html) |
| **AWS Security Hub** | 25 | [View](./quizzes/security-hub-comprehensive.html) |
| **AWS CloudTrail** | 25 | [View](./quizzes/cloudtrail-comprehensive.html) |
| **CloudWatch Security** | 20 | [View](./quizzes/cloudwatch-security-comprehensive.html) |
| **Amazon Security Lake** | 20 | [View](./quizzes/security-lake-comprehensive.html) |
| **Amazon Athena** | 20 | [View](./quizzes/athena-comprehensive.html) |
| **Amazon OpenSearch Service** | 20 | [View](./quizzes/opensearch-comprehensive.html) |
| **Amazon Managed Grafana** | 20 | [View](./quizzes/managed-grafana-comprehensive.html) |
| **VPC Flow Logs and Transit Gateway Flow Logs** | 20 | [View](./quizzes/vpc-flow-logs-transit-gw-comprehensive.html) |
| **Route 53 Resolver Query Logging** | 20 | [View](./quizzes/route53-resolver-logs-comprehensive.html) |

#### Domain 2: Incident Response -- 7 quizzes | 152 questions

| Topic | Questions | Quiz |
|-------|-----------|------|
| **Incident Response Fundamentals** | 25 | [View](./quizzes/incident-response-fundamentals.html) |
| **Automated Remediation** | 20 | [View](./quizzes/automated-remediation.html) |
| **Amazon Detective** | 20 | [View](./quizzes/detective-comprehensive.html) |
| **Fault Injection and Resilience Hub** | 25 | [View](./quizzes/fault-injection-resilience-hub-comprehensive.html) |
| **Application Recovery Controller** | 20 | [View](./quizzes/application-recovery-controller-comprehensive.html) |
| **Forensics Orchestrator and OpsCenter** | 22 | [View](./quizzes/forensics-orchestrator-opscenter-comprehensive.html) |
| **Shield Advanced** | 20 | [View](./quizzes/shield-advanced-comprehensive.html) |

#### Domain 3: Infrastructure Security -- 10 quizzes | 223 questions

| Topic | Questions | Quiz |
|-------|-----------|------|
| **Amazon VPC Security** | 25 | [View](./quizzes/vpc-security-comprehensive.html) |
| **AWS WAF** | 20 | [View](./quizzes/waf-comprehensive.html) |
| **AWS Shield and DDoS Protection** | 18 | [View](./quizzes/shield-ddos-comprehensive.html) |
| **AWS Network Firewall** | 20 | [View](./quizzes/network-firewall-comprehensive.html) |
| **Amazon Inspector** | 20 | [View](./quizzes/inspector-comprehensive.html) |
| **EC2 Image Builder and Systems Manager** | 20 | [View](./quizzes/imagebuilder-ssm-comprehensive.html) |
| **AWS Verified Access, Direct Connect and VPN** | 25 | [View](./quizzes/verifiedaccess-directconnect-vpn-comprehensive.html) |
| **Network Access Analyzer and CloudFront Security** | 25 | [View](./quizzes/networkanalyzer-cloudfront-comprehensive.html) |
| **Amazon Q Developer and CodeGuru Security** | 25 | [View](./quizzes/qdeveloper-codeguru-comprehensive.html) |
| **GenAI OWASP Top 10 Security** | 25 | [View](./quizzes/genai-owasp-top10-comprehensive.html) |

#### Domain 4: Identity and Access Management -- 8 quizzes | 183 questions

| Topic | Questions | Quiz |
|-------|-----------|------|
| **IAM Fundamentals: Users, Groups, Policy Evaluation and Credentials** | 25 | [View](./quizzes/iam-fundamentals-comprehensive.html) |
| **IAM Policies and Permissions** | 25 | [View](./quizzes/iam-policies-comprehensive.html) |
| **AWS Organizations and SCPs** | 20 | [View](./quizzes/organizations-scps-comprehensive.html) |
| **IAM Identity Center and Federation** | 20 | [View](./quizzes/identity-center-federation-comprehensive.html) |
| **Amazon Cognito and AWS STS** | 18 | [View](./quizzes/cognito-sts-comprehensive.html) |
| **AWS Verified Permissions (Cedar)** | 25 | [View](./quizzes/verified-permissions-comprehensive.html) |
| **IAM Roles Anywhere and Directory Service** | 25 | [View](./quizzes/rolesanywhere-directoryservice-comprehensive.html) |
| **IAM Access Analyzer, Policy Simulator and ABAC/RBAC** | 25 | [View](./quizzes/accessanalyzer-policysim-abac-comprehensive.html) |

#### Domain 5: Data Protection -- 11 quizzes | 256 questions

| Topic | Questions | Quiz |
|-------|-----------|------|
| **AWS KMS** | 25 | [View](./quizzes/kms-comprehensive.html) |
| **Secrets Manager and CloudHSM** | 20 | [View](./quizzes/secrets-manager-cloudhsm-comprehensive.html) |
| **ACM and S3 Encryption** | 18 | [View](./quizzes/acm-s3-encryption-comprehensive.html) |
| **Amazon Macie** | 18 | [View](./quizzes/macie-comprehensive.html) |
| **AWS PrivateLink and VPC Endpoints** | 25 | [View](./quizzes/privatelink-comprehensive.html) |
| **S3 Object Lock and Glacier Vault Lock** | 25 | [View](./quizzes/s3objectlock-glaciervaultlock-comprehensive.html) |
| **AWS Backup and Data Lifecycle Manager** | 25 | [View](./quizzes/awsbackup-vaultlock-dlm-comprehensive.html) |
| **KMS Imported Keys and External Key Store** | 25 | [View](./quizzes/kms-imported-keys-xks-comprehensive.html) |
| **CloudWatch Logs and SNS Data Protection** | 25 | [View](./quizzes/cwlogs-sns-dataprotection-comprehensive.html) |
| **AWS Private Certificate Authority** | 25 | [View](./quizzes/privateca-comprehensive.html) |
| **Nitro / EMR / EKS Encryption** | 25 | [View](./quizzes/nitro-emr-eks-encryption-comprehensive.html) |

#### Domain 6: Security Foundations and Governance -- 7 quizzes | 163 questions

| Topic | Questions | Quiz |
|-------|-----------|------|
| **AWS Control Tower** | 20 | [View](./quizzes/control-tower-comprehensive.html) |
| **AWS Config and Compliance** | 20 | [View](./quizzes/config-compliance-comprehensive.html) |
| **Audit Manager and Artifact** | 23 | [View](./quizzes/audit-manager-artifact-comprehensive.html) |
| **Resource Control Policies and Declarative Policies** | 25 | [View](./quizzes/rcp-declarative-policies-comprehensive.html) |
| **CloudFormation Guard and cfn-lint** | 25 | [View](./quizzes/cfn-guard-cfn-lint-comprehensive.html) |
| **Firewall Manager and Service Catalog** | 25 | [View](./quizzes/firewall-manager-service-catalog-comprehensive.html) |
| **Resource Access Manager and Well-Architected Tool** | 25 | [View](./quizzes/ram-wellarchitected-comprehensive.html) |

#### Cross-Domain -- 1 quiz | 20 questions

| Topic | Questions | Quiz |
|-------|-----------|------|
| **What's New in SCS-C03** | 20 | [View](./quizzes/scs-c03-new-topics.html) |

Covers new topics added to the 2026 SCS-C03 exam version:
- Open Cybersecurity Schema Framework (OCSF) with Security Lake
- Generative AI security and OWASP Top 10 for LLM Applications
- Inter-resource encryption (EMR, EKS, SageMaker, Nitro)
- CloudWatch Logs and SNS message data protection
- KMS imported key material vs AWS-generated keys
- AWS Private Certificate Authority multi-region support

### Full-Length Practice Exams

> **📝 5 complete practice exams -- 325 questions total, all 6 domains covered**

Simulates the real SCS-C03 exam format: 65 questions, timed (170 minutes), all-at-once grading with detailed answer review.

| Exam | Questions | Link |
|------|-----------|------|
| **Practice Exam 1** | 65 | [View](./exams/practice-exam-1.html) |
| **Practice Exam 2** | 65 | [View](./exams/practice-exam-2.html) |
| **Practice Exam 3** | 65 | [View](./exams/practice-exam-3.html) |
| **Practice Exam 4** | 65 | [View](./exams/practice-exam-4.html) |
| **Practice Exam 5** | 65 | [View](./exams/practice-exam-5.html) |

### Running Quizzes Locally

**Option 1: Direct file access**
```
Double-click any .html file in the quizzes/ folder
```

**Option 2: Local HTTP server (recommended)**
```bash
cd quizzes
python -m http.server 8080
# Open http://localhost:8080 in your browser
```

> 💡 **Want more quizzes?** [Open an issue](../../issues/new) to request a specific topic!

---

## 📺 Video Resources

### AWS re:Invent & re:Inforce (Recommended)

<details>
<summary><b>🔍 Threat Detection & Incident Response</b></summary>

- [AWS re:Invent 2025 - Detect and stop malware threats using Amazon GuardDuty (SEC350)](https://www.youtube.com/watch?v=E5p_WnP4pw8&list=WL&index=135)
- [AWS re:Invent 2024 - Uncovering sophisticated cloud threats with Amazon GuardDuty (SEC219)](https://www.youtube.com/watch?v=3fR2PMtW7fs&list=WL&index=140&t=1849s)
- [AWS re:Inforce 2022: Introducing Amazon GuardDuty Malware Protection (TDR210)](https://www.youtube.com/watch?v=9wCxAZtrjpw)
- [AWS re:Inforce 2022: What's new with AWS threat detection services (TDR202)](https://www.youtube.com/watch?v=uDvP6tlkpjQ)
- [AWS re:Inforce 2022: Running effective security incident response simulations (TDR201)](https://www.youtube.com/watch?v=63EdzHT25_A)
- [AWS re:Inforce 2022: A proactive approach to zero-days: Lessons from Log4j (TDR301)](https://www.youtube.com/watch?v=CEq5wGJjh1g)

</details>

<details>
<summary><b>🔑 Identity & Access Management</b></summary>

- [AWS re:Invent 2025 - IAM Access Analyzer Deep Dive: From Configuration to Remediation (SEC340)](https://www.youtube.com/watch?v=IJVe5GxEo44&list=WL&index=130)
- [AWS re:Inforce 2022: Security best practices with AWS IAM (IAM201)](https://www.youtube.com/watch?v=SMjvtxXOXdU)
- [AWS re:Inforce 2022: Designing a well-architected IAM solution (IAM309)](https://www.youtube.com/watch?v=qrQzUzDyjks)
- [AWS re:Invent 2022: Harness power of IAM policies with Access Analyzer (SEC313)](https://www.youtube.com/watch?v=x-Kh8hKVX74)
- [AWS re:Invent 2018: Become an IAM Policy Master in 60 Minutes (SEC316-R1)](https://www.youtube.com/watch?v=YQsK4MtsELU)

</details>

<details>
<summary><b>🔒 Data Protection & Encryption</b></summary>

- [AWS re:Invent 2022: Protecting secrets, keys, and data: Cryptography for the long term (SEC403)](https://www.youtube.com/watch?v=9vr3oMODIUE)
- [AWS re:Invent 2022: Amazon S3 security and access control best practices (STG301)](https://www.youtube.com/watch?v=VeE-O0imUVY)
- [AWS re:Inforce 2019: Achieving Security Goals with AWS CloudHSM (SDD333)](https://www.youtube.com/watch?v=_gezaWmwzYY)

</details>

<details>
<summary><b>🛡️ Infrastructure & Network Security</b></summary>

- [AWS re:Invent 2022: Introducing AWS Verified Access (NET214)](https://www.youtube.com/watch?v=Kkxn-bAIlnI)
- [AWS re:Invent 2022: Protect against ransomware with Zero Trust (STG208)](https://www.youtube.com/watch?v=ELSm3WgR8RE)
- [AWS re:Invent 2022: Architecting secure serverless applications (SVS302-R)](https://www.youtube.com/watch?v=A8iHQjHv8nY)

</details>

<details>
<summary><b>🛠️ Security Development & Operations</b></summary>

- [AWS re:Invent 2025 - AWS Security Agent: Proactive AppSec from Design to Deployment (SEC348)](https://www.youtube.com/watch?v=LPo4kI656bY&list=WL&index=127)

</details>

---

## 🗺️ Study Plan (SCS-C03)

A suggested 10-week study plan based on new domain weights:

| Week | Focus Area | Activities |
|------|------------|------------|
| 1-2 | Domain 4: IAM (20%) | Policies, SCPs, Federation, Identity Center |
| 3-4 | Domain 3 & 5: Infrastructure & Data Protection (36%) | VPC, WAF, Shield, KMS, Encryption |
| 5-6 | Domain 1: Detection (16%) | GuardDuty, Security Hub, CloudTrail, CloudWatch |
| 7-8 | Domain 2: Incident Response (14%) | Response plans, forensics, automation |
| 9 | Domain 6: Security Foundations & Governance (14%) | Control Tower, Organizations, Compliance |
| 10 | Review & Practice | Quizzes, sample questions, weak areas |

---

## 🆕 What's New in SCS-C03

> **SCS-C03 launched December 2, 2025** - Key changes from SCS-C02:

### New Content Added
| Topic | Description | AWS Resources |
|-------|-------------|---------------|
| **Generative AI Security** | OWASP Top 10 for LLM Applications protections | [Guardrails for Amazon Bedrock](https://docs.aws.amazon.com/bedrock/latest/userguide/guardrails.html) • [Responsible AI on AWS](https://aws.amazon.com/ai/responsible-ai/) • [Blog: Security best practices for generative AI](https://aws.amazon.com/blogs/security/category/artificial-intelligence/generative-ai/) |
| **OCSF Format Integration** | Open Cybersecurity Schema Framework for data ingestion | [OCSF Schema Documentation](https://schema.ocsf.io/) • [Amazon Security Lake OCSF Support](https://docs.aws.amazon.com/security-lake/latest/userguide/open-cybersecurity-schema-framework.html) |
| **Inter-Resource Encryption** | EMR, EKS, SageMaker AI, Nitro encryption configs | [EMR Encryption Options](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-data-encryption-options.html) • [EKS Encryption Best Practices](https://docs.aws.amazon.com/eks/latest/best-practices/security.html) • [SageMaker Encryption](https://docs.aws.amazon.com/sagemaker/latest/dg/encryption-at-rest.html) • [Nitro Enclaves](https://docs.aws.amazon.com/enclaves/latest/user/nitro-enclave.html) |
| **Data Masking** | CloudWatch Logs data protection, SNS message data protection | [CloudWatch Logs Data Protection](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/mask-sensitive-log-data.html) • [SNS Message Data Protection](https://docs.aws.amazon.com/sns/latest/dg/sns-message-data-protection.html) |
| **Multi-Region Key Management** | KMS keys and certificates across regions | [KMS Multi-Region Keys](https://docs.aws.amazon.com/kms/latest/developerguide/multi-region-keys-overview.html)  |

### New Question Types
- **Ordering Questions** - Select and arrange steps in correct sequence
- **Matching Questions** - Pair items from two lists correctly

### Domain Restructuring
- Domain 1 renamed to "Detection" (16%, was 14%)
- Domain 2 is now separate "Incident Response" (14%)
- Domain 4 (IAM) increased to 20% (was 16%) - now highest weighted!
- Domain 3 (Infrastructure) decreased to 18% (was 20%)

See [full comparison](https://docs.aws.amazon.com/aws-certification/latest/examguides/security-specialty-03-appendix-b.html)

---

## Repository Structure

```
aws-security-specialty-study-guide/
+-- README.md                        # This file
+-- LICENSE                          # MIT License
+-- CONTRIBUTING.md                  # Contribution guidelines
+-- CNAME                            # GitHub Pages custom domain
+-- index.html                       # GitHub Pages landing page
+-- archive/                         # Previous years' study guides
|   +-- README.md
|   +-- 2020-scs-c01-study-guide.md
|   +-- 2023-scs-c01-study-guide.md
+-- assets/                          # Domain infographic images
|   +-- domain-1-detection.png
|   +-- domain-2-incident-response.png
|   +-- domain-3-infrastructure-security.png
|   +-- domain-4-iam.png
|   +-- domain-5-data-protection.png
|   +-- domain-6-governance.png
+-- docs/                            # Domain-specific study guides (SCS-C03)
|   +-- README.md
|   +-- domain-1-detection.md
|   +-- domain-2-incident-response.md
|   +-- domain-3-infrastructure-security.md
|   +-- domain-4-iam.md
|   +-- domain-5-data-protection.md
|   +-- domain-6-governance.md
+-- exams/                           # Full-length practice exams (5 x 65 questions)
|   +-- practice-exam-1.html
|   +-- practice-exam-2.html
|   +-- practice-exam-3.html
|   +-- practice-exam-4.html
|   +-- practice-exam-5.html
|   +-- practice-exam-question-index.md
+-- quizzes/                         # Interactive HTML quizzes (55 quizzes, 1227 questions)
    +-- README.md
    +-- accessanalyzer-policysim-abac-comprehensive.html
    +-- acm-s3-encryption-comprehensive.html
    +-- application-recovery-controller-comprehensive.html
    +-- athena-comprehensive.html
    +-- audit-manager-artifact-comprehensive.html
    +-- automated-remediation.html
    +-- awsbackup-vaultlock-dlm-comprehensive.html
    +-- cfn-guard-cfn-lint-comprehensive.html
    +-- cloudtrail-comprehensive.html
    +-- cloudwatch-security-comprehensive.html
    +-- cognito-sts-comprehensive.html
    +-- config-compliance-comprehensive.html
    +-- control-tower-comprehensive.html
    +-- cwlogs-sns-dataprotection-comprehensive.html
    +-- detective-comprehensive.html
    +-- fault-injection-resilience-hub-comprehensive.html
    +-- firewall-manager-service-catalog-comprehensive.html
    +-- forensics-orchestrator-opscenter-comprehensive.html
    +-- genai-owasp-top10-comprehensive.html
    +-- guardduty-comprehensive.html
    +-- guardduty-extended-threat-detection.html
    +-- iam-fundamentals-comprehensive.html
    +-- iam-policies-comprehensive.html
    +-- identity-center-federation-comprehensive.html
    +-- imagebuilder-ssm-comprehensive.html
    +-- incident-response-fundamentals.html
    +-- inspector-comprehensive.html
    +-- kms-comprehensive.html
    +-- kms-imported-keys-xks-comprehensive.html
    +-- macie-comprehensive.html
    +-- managed-grafana-comprehensive.html
    +-- network-firewall-comprehensive.html
    +-- networkanalyzer-cloudfront-comprehensive.html
    +-- nitro-emr-eks-encryption-comprehensive.html
    +-- opensearch-comprehensive.html
    +-- organizations-scps-comprehensive.html
    +-- privateca-comprehensive.html
    +-- privatelink-comprehensive.html
    +-- qdeveloper-codeguru-comprehensive.html
    +-- ram-wellarchitected-comprehensive.html
    +-- rcp-declarative-policies-comprehensive.html
    +-- rolesanywhere-directoryservice-comprehensive.html
    +-- route53-resolver-logs-comprehensive.html
    +-- s3objectlock-glaciervaultlock-comprehensive.html
    +-- scs-c03-new-topics.html
    +-- secrets-manager-cloudhsm-comprehensive.html
    +-- security-hub-comprehensive.html
    +-- security-lake-comprehensive.html
    +-- shield-advanced-comprehensive.html
    +-- shield-ddos-comprehensive.html
    +-- verified-permissions-comprehensive.html
    +-- verifiedaccess-directconnect-vpn-comprehensive.html
    +-- vpc-flow-logs-transit-gw-comprehensive.html
    +-- vpc-security-comprehensive.html
    +-- waf-comprehensive.html
```

---

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

- 📝 **Add study notes** - Share your domain-specific notes
- ❓ **Suggest quiz questions** - Help expand the question bank
- 🐛 **Report errors** - Found outdated info? Let us know!
- ⭐ **Star the repo** - Help others discover this resource

See [CONTRIBUTING.md](./CONTRIBUTING.md) for detailed guidelines.

---

## ⚖️ Disclaimer

This study guide and all quiz questions are **original content** created by the author based on:
- Official [AWS Documentation](https://docs.aws.amazon.com/)
- AWS Whitepapers and Best Practices guides
- Publicly available AWS training materials

**This repository does NOT contain:**
- ❌ Actual exam questions (which would violate the AWS Certification NDA)
- ❌ Content from commercial exam prep providers (Whizlabs, Tutorials Dojo, A Cloud Guru, etc.)
- ❌ "Brain dumps" or memorized exam content

All questions are designed to test understanding of AWS security concepts and services, not to replicate the actual certification exam. The goal is to help candidates learn the underlying AWS knowledge, not to provide shortcuts.

*AWS, Amazon Web Services, and all related service names are trademarks of Amazon.com, Inc. or its affiliates.*

---

## 📜 License

This project is licensed under the MIT License - see the [LICENSE](./LICENSE) file for details.

---

## 🙏 Acknowledgments

- AWS for their comprehensive documentation
- The AWS certification community for shared insights
- All contributors who help improve this guide

---

<div align="center">

**Found this helpful? Give it a ⭐!**

[![LinkedIn](https://img.shields.io/badge/Share%20on-LinkedIn-0077B5?style=for-the-badge&logo=linkedin)](https://www.linkedin.com/shareArticle?mini=true&url=https://github.com/RaduLupan/aws-security-specialty-study-guide&title=AWS%20Security%20Specialty%20Study%20Guide)
[![Bluesky](https://img.shields.io/badge/Share%20on-Bluesky-0085FF?style=for-the-badge&logo=bluesky)](https://bsky.app/intent/compose?text=Check%20out%20this%20AWS%20Security%20Specialty%20Study%20Guide!%20https://github.com/RaduLupan/aws-security-specialty-study-guide)

</div>
