# 🔐 AWS Security Specialty Study Guide

<div align="center">

![AWS Security Specialty](https://img.shields.io/badge/AWS-Security%20Specialty-FF9900?style=for-the-badge&logo=amazon-aws&logoColor=white)
![Exam Code](https://img.shields.io/badge/Exam-SCS--C02-232F3E?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)
![Stars](https://img.shields.io/github/stars/RaduLupan/aws-security-specialty-study-guide?style=for-the-badge)
![Forks](https://img.shields.io/github/forks/RaduLupan/aws-security-specialty-study-guide?style=for-the-badge)

**A comprehensive, community-driven study guide for the AWS Certified Security - Specialty exam**

[📚 Study Materials](#-study-materials) • [🎮 Practice Quizzes](#-practice-quizzes) • [📺 Video Resources](#-video-resources) • [🤝 Contributing](#-contributing)

</div>

---

## 📋 About This Guide

This repository contains curated study materials, interactive quizzes, and resources for the **AWS Certified Security - Specialty (SCS-C02)** certification exam.

| Attribute | Details |
|-----------|---------|
| **Exam Code** | SCS-C02 |
| **Format** | 65 questions (multiple choice & multiple response) |
| **Duration** | 170 minutes |
| **Passing Score** | 750/1000 |
| **Cost** | $300 USD |
| **Validity** | 3 years |

### 🏆 Author's Certification Journey

| Year | Status | Exam Version |
|------|--------|--------------|
| 2020 | ✅ Initial Certification | SCS-C01 |
| 2023 | ✅ First Recertification | SCS-C01 |
| 2026 | 🎯 Second Recertification | SCS-C02 |

> 💡 See [archive/](./archive/) for previous years' study guides.

---

## 🎯 Exam Domains

The SCS-C02 exam covers six domains:

| Domain | Weight | Key Topics |
|--------|--------|------------|
| **1. Threat Detection & Incident Response** | 14% | GuardDuty, Security Hub, Detective, Incident Response |
| **2. Security Logging & Monitoring** | 18% | CloudTrail, CloudWatch, VPC Flow Logs, Config |
| **3. Infrastructure Security** | 20% | VPC, WAF, Shield, Network Firewall, Security Groups |
| **4. Identity & Access Management** | 16% | IAM, Organizations, SCPs, Federation, Identity Center |
| **5. Data Protection** | 18% | KMS, Secrets Manager, ACM, Macie, Encryption |
| **6. Management & Security Governance** | 14% | Control Tower, Organizations, Compliance, Audit |

---

## 📚 Study Materials

### Official AWS Resources

- 📄 [Exam Guide (PDF)](https://d1.awsstatic.com/training-and-certification/docs-security-spec/AWS-Certified-Security-Specialty_Exam-Guide.pdf)
- 📝 [Sample Questions](https://d1.awsstatic.com/training-and-certification/docs-security-spec/AWS-Certified-Security-Speciality_Sample-Questions.pdf)
- 🎓 [AWS Skill Builder](https://explore.skillbuilder.aws/learn/course/14297/aws-certified-security-specialty-official-practice-question-set-scs-c02-english)

### Domain-Specific Study Guides

| Domain | Study Guide | Status |
|--------|-------------|--------|
| Domain 1 | [Threat Detection & Incident Response](./docs/domain-1-threat-detection.md) | 🚧 In Progress |
| Domain 2 | [Security Logging & Monitoring](./docs/domain-2-logging-monitoring.md) | 🚧 In Progress |
| Domain 3 | [Infrastructure Security](./docs/domain-3-infrastructure-security.md) | 🚧 In Progress |
| Domain 4 | [Identity & Access Management](./docs/domain-4-iam.md) | 🚧 In Progress |
| Domain 5 | [Data Protection](./docs/domain-5-data-protection.md) | 🚧 In Progress |
| Domain 6 | [Management & Security Governance](./docs/domain-6-governance.md) | 🚧 In Progress |

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

| Topic | Questions | Difficulty | Quiz |
|-------|-----------|------------|------|
| **Amazon GuardDuty (Comprehensive)** | 25 | Intermediate | [Start Quiz](./quizzes/guardduty-comprehensive.html) |
| GuardDuty Extended Threat Detection | 15 | Intermediate | [Start Quiz](./quizzes/guardduty-extended-threat-detection.html) |
| *More quizzes coming soon...* | | | |

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

- [AWS re:Inforce 2022: Introducing Amazon GuardDuty Malware Protection (TDR210)](https://www.youtube.com/watch?v=9wCxAZtrjpw)
- [AWS re:Inforce 2022: What's new with AWS threat detection services (TDR202)](https://www.youtube.com/watch?v=uDvP6tlkpjQ)
- [AWS re:Inforce 2022: Running effective security incident response simulations (TDR201)](https://www.youtube.com/watch?v=63EdzHT25_A)
- [AWS re:Inforce 2022: A proactive approach to zero-days: Lessons from Log4j (TDR301)](https://www.youtube.com/watch?v=CEq5wGJjh1g)

</details>

<details>
<summary><b>🔑 Identity & Access Management</b></summary>

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

---

## 🗺️ Study Plan

A suggested 10-week study plan:

| Week | Focus Area | Activities |
|------|------------|------------|
| 1-2 | Domain 3: Infrastructure Security (20%) | VPC, Security Groups, NACLs, WAF, Shield |
| 3-4 | Domain 2 & 5: Logging & Data Protection (36%) | CloudTrail, CloudWatch, KMS, Encryption |
| 5-6 | Domain 4: IAM (16%) | Policies, SCPs, Federation, Identity Center |
| 7-8 | Domain 1: Threat Detection (14%) | GuardDuty, Security Hub, Detective |
| 9 | Domain 6: Governance (14%) | Control Tower, Organizations, Compliance |
| 10 | Review & Practice | Quizzes, sample questions, weak areas |

---

## 🆕 What's New in SCS-C02

Services and features added since SCS-C01:

| Service/Feature | Description |
|-----------------|-------------|
| **GuardDuty Extended Threat Detection** | Multi-stage attack sequence detection |
| **GuardDuty Malware Protection** | EBS volume scanning for malware |
| **AWS Verified Access** | Zero-trust access to applications |
| **IAM Identity Center** | Centralized SSO (formerly AWS SSO) |
| **Security Lake** | Centralized security data lake |
| **Amazon Inspector v2** | Continuous vulnerability scanning |
| **AWS Network Firewall** | Managed network firewall service |

---

## 📂 Repository Structure

```
aws-security-specialty-study-guide/
├── README.md                 # This file
├── LICENSE                   # MIT License
├── CONTRIBUTING.md           # Contribution guidelines
├── archive/                  # Previous years' study guides
│   ├── 2020-scs-c01-study-guide.md
│   └── 2023-scs-c01-study-guide.md
├── docs/                     # Domain-specific study materials
│   ├── domain-1-threat-detection.md
│   ├── domain-2-logging-monitoring.md
│   ├── domain-3-infrastructure-security.md
│   ├── domain-4-iam.md
│   ├── domain-5-data-protection.md
│   └── domain-6-governance.md
├── quizzes/                  # Interactive HTML quizzes
│   ├── README.md
│   └── *.html
└── assets/                   # Images and diagrams
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
[![Twitter](https://img.shields.io/badge/Share%20on-Twitter-1DA1F2?style=for-the-badge&logo=twitter)](https://twitter.com/intent/tweet?text=Check%20out%20this%20AWS%20Security%20Specialty%20Study%20Guide!&url=https://github.com/RaduLupan/aws-security-specialty-study-guide)

</div>
