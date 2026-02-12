# 🎮 Practice Quizzes

Interactive HTML-based quizzes for AWS Security Specialty exam preparation.

## Features

| Feature | Description |
|---------|-------------|
| **📚 Learn Mode** | Reveal answers one at a time with immediate feedback |
| **📝 Exam Mode** | Timed assessment (2.5 min/question), submit all at once |
| **🔀 Shuffle** | Questions and options randomize on every restart |
| **✅ Pass/Fail** | 80% threshold with clear visual feedback |
| **📖 Explanations** | Detailed answers with AWS documentation links |

## Available Quizzes

### Domain 1: Detection (130 questions)

| Quiz | Topic | Questions | 
|------|-------|-----------|
| [security-hub-comprehensive.html](./security-hub-comprehensive.html) | **AWS Security Hub (All Topics)** | 25 |
| [guardduty-comprehensive.html](./guardduty-comprehensive.html) | **Amazon GuardDuty (All Topics)** | 25 |
| [cloudtrail-comprehensive.html](./cloudtrail-comprehensive.html) | **AWS CloudTrail (All Topics)** | 25 |
| [cloudwatch-security-comprehensive.html](./cloudwatch-security-comprehensive.html) | **Amazon CloudWatch Security** | 20 |
| [security-lake-comprehensive.html](./security-lake-comprehensive.html) | **Amazon Security Lake** | 20 |
| [guardduty-extended-threat-detection.html](./guardduty-extended-threat-detection.html) | GuardDuty Extended Threat Detection | 15 |

### Domain 2: Incident Response (152 questions)

| Quiz | Topic | Questions | 
|------|-------|-----------|
| [incident-response-fundamentals.html](./incident-response-fundamentals.html) | **Incident Response Fundamentals** | 25 |
| [automated-remediation.html](./automated-remediation.html) | **Automated Remediation** | 20 |
| [detective-comprehensive.html](./detective-comprehensive.html) | **Amazon Detective** | 20 |
| [fault-injection-resilience-hub-comprehensive.html](./fault-injection-resilience-hub-comprehensive.html) | **Fault Injection & Resilience Hub** | 25 |
| [application-recovery-controller-comprehensive.html](./application-recovery-controller-comprehensive.html) | **Application Recovery Controller** | 20 |
| [forensics-orchestrator-opscenter-comprehensive.html](./forensics-orchestrator-opscenter-comprehensive.html) | **Forensics Orchestrator & OpsCenter** | 22 |
| [shield-advanced-comprehensive.html](./shield-advanced-comprehensive.html) | **Shield Advanced** | 20 |

### Domain 3: Infrastructure Security (Complete - 223 questions!)

| Quiz | Topic | Questions | 
|------|-------|-----------|
| [vpc-security-comprehensive.html](./vpc-security-comprehensive.html) | **Amazon VPC Security** | 25 |
| [waf-comprehensive.html](./waf-comprehensive.html) | **AWS WAF** | 20 |
| [shield-ddos-comprehensive.html](./shield-ddos-comprehensive.html) | **AWS Shield & DDoS Protection** | 18 |
| [network-firewall-comprehensive.html](./network-firewall-comprehensive.html) | **AWS Network Firewall** | 20 |
| [inspector-comprehensive.html](./inspector-comprehensive.html) | **Amazon Inspector** | 20 |
| [imagebuilder-ssm-comprehensive.html](./imagebuilder-ssm-comprehensive.html) | **EC2 Image Builder & Systems Manager** | 20 |
| [verifiedaccess-directconnect-vpn-comprehensive.html](./verifiedaccess-directconnect-vpn-comprehensive.html) | **AWS Verified Access, Direct Connect & VPN** | 25 |
| [networkanalyzer-cloudfront-comprehensive.html](./networkanalyzer-cloudfront-comprehensive.html) | **Network Access Analyzer & CloudFront Security** | 25 |
| [qdeveloper-codeguru-comprehensive.html](./qdeveloper-codeguru-comprehensive.html) | **Amazon Q Developer & CodeGuru Security** | 25 |
| [genai-owasp-top10-comprehensive.html](./genai-owasp-top10-comprehensive.html) | **GenAI OWASP Top 10 Security** | 25 |

### Domain 4: Identity & Access Management (108 questions)

| Quiz | Topic | Questions | 
|------|-------|-----------|
| [iam-policies-comprehensive.html](./iam-policies-comprehensive.html) | **IAM Policies & Permissions** | 25 |
| [organizations-scps-comprehensive.html](./organizations-scps-comprehensive.html) | **AWS Organizations & SCPs** | 20 |
| [identity-center-federation-comprehensive.html](./identity-center-federation-comprehensive.html) | **IAM Identity Center & Federation** | 20 |
| [cognito-sts-comprehensive.html](./cognito-sts-comprehensive.html) | **Amazon Cognito & AWS STS** | 18 |
| [verified-permissions-comprehensive.html](./verified-permissions-comprehensive.html) | **AWS Verified Permissions (Cedar)** | 25 |

### Domain 5: Data Protection (Complete - 81 questions!)

| Quiz | Topic | Questions | 
|------|-------|-----------|
| [kms-comprehensive.html](./kms-comprehensive.html) | **AWS KMS (All Topics)** | 25 |
| [secrets-manager-cloudhsm-comprehensive.html](./secrets-manager-cloudhsm-comprehensive.html) | **Secrets Manager & CloudHSM** | 20 |
| [acm-s3-encryption-comprehensive.html](./acm-s3-encryption-comprehensive.html) | **ACM & S3 Encryption** | 18 |
| [macie-comprehensive.html](./macie-comprehensive.html) | **Amazon Macie** | 18 |

### Domain 6: Security Governance (Complete - 58 questions!)

| Quiz | Topic | Questions | 
|------|-------|-----------|
| [control-tower-comprehensive.html](./control-tower-comprehensive.html) | **AWS Control Tower** | 20 |
| [config-compliance-comprehensive.html](./config-compliance-comprehensive.html) | **AWS Config & Compliance** | 20 |
| [audit-manager-artifact-comprehensive.html](./audit-manager-artifact-comprehensive.html) | **Audit Manager & Artifact** | 18 |

## How to Use

### Option 1: Direct File Access
Simply double-click any `.html` file to open in your default browser.

### Option 2: Local HTTP Server (Recommended)

```bash
# Navigate to quizzes folder
cd quizzes

# Start a simple HTTP server
python -m http.server 8080

# Open in browser
# http://localhost:8080/guardduty-extended-threat-detection.html
```

### Option 3: GitHub Pages
If this repo is published to GitHub Pages, quizzes will be available at:
```
https://radulupan.github.io/aws-security-specialty-study-guide/quizzes/
```

## Quiz Modes

### 📚 Learn Mode
- Answer one question at a time
- Click "Show Answer" to reveal if correct
- See explanation and documentation link immediately
- Good for: Initial learning, studying new topics

### 📝 Exam Mode
- Timer starts (2.5 minutes per question)
- Answer all questions before submitting
- All answers revealed at once after submission
- Shows pass/fail (80% threshold)
- Good for: Testing yourself, simulating exam conditions

## Requesting New Quizzes

Want a quiz on a specific topic? [Open an issue](../../../issues/new) with:
- Topic name
- AWS service(s) involved
- Any specific areas to focus on

## Contributing Quiz Questions

See [CONTRIBUTING.md](../CONTRIBUTING.md) for guidelines on submitting quiz questions.

---

**Good luck with your exam preparation! 🎓**
