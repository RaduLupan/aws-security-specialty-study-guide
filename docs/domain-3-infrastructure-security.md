# Domain 3: Infrastructure Security (18%)

> 🚧 **Status:** In Progress

## Overview

This domain covers network security, edge protection, and compute security in AWS.

---

## Key Services

| Service | Purpose |
|---------|---------|
| **Amazon VPC** | Network isolation |
| **Security Groups** | Stateful instance-level firewall |
| **Network ACLs** | Stateless subnet-level firewall |
| **AWS WAF** | Web application firewall |
| **AWS Shield** | DDoS protection |
| **AWS Network Firewall** | Managed network firewall |
| **AWS Firewall Manager** | Central firewall management |

---

## 🌐 Amazon VPC Security

### Security Groups vs NACLs

| Feature | Security Groups | NACLs |
|---------|-----------------|-------|
| **Level** | Instance (ENI) | Subnet |
| **State** | Stateful | Stateless |
| **Rules** | Allow only | Allow and Deny |
| **Evaluation** | All rules | Numbered order |
| **Default** | Deny all inbound | Allow all |

### VPC Endpoints

- **Gateway Endpoints**: S3, DynamoDB (free, route table entry)
- **Interface Endpoints**: Other services (PrivateLink, ENI with private IP)
- **Endpoint Policies**: Restrict access to specific resources

### VPC Peering vs Transit Gateway

- **Peering**: 1-to-1, non-transitive
- **Transit Gateway**: Hub-and-spoke, transitive routing

### Key Documentation Links

- [Control subnet traffic with NACLs](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-network-acls.html)
- [Security best practices for VPC](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-security-best-practices.html)
- [Infrastructure security in VPC](https://docs.aws.amazon.com/vpc/latest/userguide/infrastructure-security.html)
- [VPC Sharing](https://docs.aws.amazon.com/whitepapers/latest/building-scalable-secure-multi-vpc-network-infrastructure/amazon-vpc-sharing.html)

📖 **Documentation**: [VPC Security Best Practices](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-security-best-practices.html)

---

## 🛡️ AWS WAF

### What You Need to Know

- **Web ACLs**: Container for rules
- **Rules**: Conditions that match web requests
- **Rule Groups**: Reusable collections of rules
- **Managed Rule Groups**: AWS and Marketplace rules

### Rule Types

- IP match
- Geographic match
- Size constraint
- SQL injection
- XSS (Cross-site scripting)
- Rate-based rules

### Integration Points

- CloudFront
- Application Load Balancer
- API Gateway
- AppSync
- Cognito User Pools

📖 **Documentation**: [AWS WAF User Guide](https://docs.aws.amazon.com/waf/latest/developerguide/)

---

## 🛡️ AWS Shield

### Shield Standard (Free)

- Automatic protection for all AWS customers
- Layer 3/4 DDoS protection
- Integrated with CloudFront, Route 53

### Shield Advanced ($3,000/month)

- Layer 7 DDoS protection
- Cost protection (credits for scaling during attack)
- 24/7 DDoS Response Team (DRT)
- Advanced metrics and reporting
- WAF included at no additional cost

### Key Documentation Links (WAF & Shield)

- [How AWS Shield works](https://docs.aws.amazon.com/waf/latest/developerguide/ddos-overview.html)
- [Manually mitigating application layer DDoS](https://docs.aws.amazon.com/waf/latest/developerguide/ddos-responding-manual.html)
- [Resource-level DDoS protection for ALB](https://docs.aws.amazon.com/waf/latest/developerguide/waf-anti-ddos-alb.html)
- [Advanced Anti-DDoS with WAF managed rules](https://docs.aws.amazon.com/waf/latest/developerguide/waf-anti-ddos-advanced.html)
- [Automatic app layer DDoS mitigation](https://docs.aws.amazon.com/waf/latest/developerguide/shield-policies-auto-app-layer-mitigation.html)

📖 **Documentation**: [AWS Shield User Guide](https://docs.aws.amazon.com/waf/latest/developerguide/shield-chapter.html)

---

## 🔥 AWS Network Firewall

### What You Need to Know

- **Managed service** - scales automatically
- **Stateful and stateless** rule groups
- **Deep packet inspection**
- **Domain filtering** (allow/deny lists)
- **IPS/IDS capabilities** (Suricata-compatible rules)

### Deployment Models

- **Distributed**: Firewall endpoint per AZ
- **Centralized**: Firewall in inspection VPC
- **Combined**: Mix of both

📖 **Documentation**: [Network Firewall User Guide](https://docs.aws.amazon.com/network-firewall/latest/developerguide/)

---

## 🎛️ AWS Firewall Manager

### What You Need to Know

- **Centrally manage** WAF, Shield Advanced, Security Groups, Network Firewall
- Requires **AWS Organizations**
- **Policy types**: WAF, Shield Advanced, Security Group, Network Firewall, Route 53 Resolver DNS Firewall
- **Auto-remediation** of non-compliant resources

📖 **Documentation**: [Firewall Manager User Guide](https://docs.aws.amazon.com/waf/latest/developerguide/fms-chapter.html)

---

## 🔐 AWS Verified Access

### What You Need to Know

- **Zero-trust network access** for applications
- No VPN required
- Identity-based access (IAM Identity Center, Okta, etc.)
- Device posture evaluation
- Per-request authorization

📖 **Documentation**: [Verified Access User Guide](https://docs.aws.amazon.com/verified-access/latest/ug/)

---

## 📺 Recommended Videos

- [AWS re:Invent 2022: Introducing AWS Verified Access (NET214)](https://www.youtube.com/watch?v=Kkxn-bAIlnI)
- [AWS re:Invent 2018: Advanced VPC Design (NET303)](https://www.youtube.com/watch?v=fnxXNZdf6ew)

---

## ✅ Exam Tips

- Know the difference between Security Groups and NACLs
- Understand VPC endpoint types and use cases
- Know WAF rule types and integration points
- Understand Shield Standard vs Advanced features
- Know Network Firewall deployment architectures
- Understand Verified Access zero-trust model

---

*Last updated: January 2026 (SCS-C03)*
