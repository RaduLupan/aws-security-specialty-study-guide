# Domain 3: Infrastructure Security (18%)

> 🚧 **Status:** In Progress

## Overview

This domain covers network edge security, compute workload security, and network security controls in AWS.

---

## Task Statements & Skills (SCS-C03)

### Task 3.1: Design, implement, and troubleshoot security controls for network edge services

| Skill | Key Services |
|-------|-------------|
| 3.1.1: Define and select edge security strategies based on anticipated threats and attacks | CloudFront, WAF, Shield Advanced |
| 3.1.2: Implement appropriate network edge protection | **CloudFront headers, AWS WAF, AWS IoT policies, OWASP Top 10, S3 CORS, Shield Advanced** |
| 3.1.3: Design and implement AWS edge controls and rules | Geography, geolocation, rate limiting, client fingerprinting |
| 3.1.4: Configure integrations with AWS edge services and third-party services | **OCSF format ingestion, third-party WAF rules** |

### Task 3.2: Design, implement, and troubleshoot security controls for compute workloads

| Skill | Key Services |
|-------|-------------|
| 3.2.1: Design and implement hardened EC2 AMIs and container images | **Systems Manager, EC2 Image Builder** |
| 3.2.2: Apply instance profiles, service roles, and execution roles | IAM roles for EC2, ECS, Lambda |
| 3.2.3: Scan compute resources for known vulnerabilities | **Amazon Inspector (container images, Lambda), GuardDuty runtime monitoring** |
| 3.2.4: Deploy patches to maintain secure and compliant environments | **Systems Manager Patch Manager, Amazon Inspector** |
| 3.2.5: Configure secure administrative access to compute resources | **Systems Manager Session Manager, EC2 Instance Connect** |
| 3.2.6: Configure security tools to discover and remediate vulnerabilities within a pipeline | **Amazon Q Developer, Amazon CodeGuru Security** |
| 3.2.7: Implement protections and guardrails for generative AI applications | **GenAI OWASP Top 10 for LLM Applications, Amazon Bedrock Guardrails** |

### Task 3.3: Design and troubleshoot network security controls

| Skill | Key Services |
|-------|-------------|
| 3.3.1: Design and troubleshoot network controls to permit/prevent traffic | **Security Groups, Network ACLs, AWS Network Firewall** |
| 3.3.2: Design secure connectivity between hybrid and multi-cloud networks | **AWS Site-to-Site VPN, AWS Direct Connect, MACsec** |
| 3.3.3: Determine security requirements for communication between hybrid environments and AWS | **AWS Verified Access** |
| 3.3.4: Design network segmentation based on security requirements | North/south and east/west traffic, isolated subnets |
| 3.3.5: Identify unnecessary network access | **AWS Verified Access, Network Access Analyzer, Amazon Inspector network reachability** |

---

## Key Services

| Service | Purpose |
|---------|---------|
| **Amazon VPC** | Network isolation |
| **Security Groups** | Stateful instance-level firewall |
| **Network ACLs** | Stateless subnet-level firewall |
| **AWS WAF** | Web application firewall |
| **AWS Shield / Shield Advanced** | DDoS protection |
| **AWS Network Firewall** | Managed network firewall |
| **AWS Firewall Manager** | Central firewall management |
| **Amazon Inspector** | Vulnerability scanning for EC2, containers, Lambda |
| **EC2 Image Builder** | Automated AMI/container image hardening pipeline |
| **AWS Systems Manager** | Patch Manager, Session Manager, State Manager |
| **EC2 Instance Connect** | Secure SSH/RDP access to EC2 instances |
| **Amazon Q Developer** | AI-powered security vulnerability detection in code |
| **Amazon CodeGuru Security** | Automated code security analysis |
| **Amazon CloudFront** | CDN with edge security features |
| **AWS Site-to-Site VPN** | Encrypted connectivity to on-premises |
| **AWS Direct Connect** | Dedicated network connection with MACsec |
| **AWS Verified Access** | Zero-trust network access |
| **Network Access Analyzer** | Identify unintended network access paths |
| **AWS IoT Core** | IoT device security policies |

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

## 🔍 Amazon Inspector (Skills 3.2.3, 3.2.4, 3.3.5)

### What You Need to Know

- **Automated vulnerability management** service
- Scans **EC2 instances**, **container images** (ECR), and **Lambda functions**
- Uses **Common Vulnerabilities and Exposures (CVE)** database
- **Network reachability** findings: identifies unintended network exposure
- Findings integrate with **Security Hub** and **EventBridge**
- **Continuous scanning**: automatically rescans when new CVEs are published or packages change

### Scan Types

| Type | What It Scans |
|------|--------------|
| **EC2 scanning** | OS packages, software vulnerabilities (SSM agent required) |
| **ECR scanning** | Container image vulnerabilities on push and continuously |
| **Lambda scanning** | Function code and dependency vulnerabilities |
| **Network reachability** | Open ports, security group exposure, internet accessibility |

### Integration with Patch Manager (Skill 3.2.4)

- Inspector finds vulnerabilities, Patch Manager remediates
- Automated patching pipelines with maintenance windows
- Compliance reporting through AWS Config

📖 **Documentation**: [Amazon Inspector User Guide](https://docs.aws.amazon.com/inspector/latest/user/)  
📖 **Network Reachability**: [Inspector network reachability findings](https://docs.aws.amazon.com/inspector/latest/user/findings-types.html)

---

## 🖼️ EC2 Image Builder (Skill 3.2.1)

### What You Need to Know

- **Automated pipeline** for building, testing, and distributing hardened AMIs and container images
- **Components**: Build and test scripts (YAML-based)
- **Recipes**: Define base image and components to apply
- **Pipelines**: Automate the build process on a schedule or trigger
- **Distribution settings**: Share AMIs across accounts and regions

### Security Use Cases

- Embed CIS benchmarks and security hardening into AMI build pipelines
- Pre-install security agents (CloudWatch agent, SSM agent, Inspector agent)
- Run automated security tests (STIG, CIS) before distributing images
- Golden AMI strategy: only allow approved, hardened AMIs in production

📖 **Documentation**: [EC2 Image Builder User Guide](https://docs.aws.amazon.com/imagebuilder/latest/userguide/)

---

## 🔧 AWS Systems Manager - Security Features (Skills 3.2.1, 3.2.4, 3.2.5)

### Patch Manager (Skill 3.2.4)

- **Automated patching** for EC2 instances and on-premises servers
- **Patch baselines**: Define which patches to approve/reject
- **Maintenance windows**: Schedule patching during approved times
- **Compliance reporting**: Track patch compliance across fleet
- Integrates with Inspector for vulnerability-driven patching

📖 **Documentation**: [Patch Manager](https://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-patch.html)

### Session Manager (Skill 3.2.5)

- **Secure shell access** to EC2 without opening SSH/RDP ports
- **No inbound ports** or bastion hosts required
- All sessions logged to **CloudTrail**, **S3**, and **CloudWatch Logs**
- **IAM-based access control** with session policies
- Supports **port forwarding** and **SSH tunneling**

📖 **Documentation**: [Session Manager](https://docs.aws.amazon.com/systems-manager/latest/userguide/session-manager.html)

### EC2 Instance Connect (Skill 3.2.5)

- **Temporary SSH key** pushed to instance metadata for 60 seconds
- No need for long-lived SSH keys
- Works through **AWS Console** or CLI
- Requires **Instance Connect agent** (pre-installed on Amazon Linux 2 and Ubuntu)
- Logged via **CloudTrail** for audit

📖 **Documentation**: [EC2 Instance Connect](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/connect-linux-inst-eic.html)

---

## 🤖 AI-Powered Security Tools (Skills 3.2.6, 3.2.7)

### Amazon Q Developer (Skill 3.2.6)

- **AI-powered code assistant** that identifies security vulnerabilities during development
- Scans code for **security issues**, **secrets**, **misconfigurations**
- Integrated into IDE for real-time feedback
- Provides remediation suggestions with explanations

📖 **Documentation**: [Amazon Q Developer](https://docs.aws.amazon.com/amazonq/latest/qdeveloper-ug/what-is.html)

### Amazon CodeGuru Security (Skill 3.2.6)

- **Static application security testing (SAST)** service
- Detects security vulnerabilities and coding best practices violations
- Supports Java, Python, JavaScript, and more
- **Pipeline integration**: Run as part of CI/CD for automated security scanning
- Findings include severity, remediation guidance, and CWE references

📖 **Documentation**: [CodeGuru Security](https://docs.aws.amazon.com/codeguru/latest/security-ug/what-is-codeguru-security.html)

### GenAI OWASP Top 10 for LLM Applications (Skill 3.2.7)

- **New in SCS-C03**: Understand protections for generative AI applications
- Key threats: Prompt injection, data leakage, model theft, training data poisoning
- **Amazon Bedrock Guardrails**: Content filtering, denied topics, PII redaction
- Implement input validation and output filtering for LLM applications
- Use IAM and VPC controls to isolate AI workloads

📖 **Reference**: [OWASP Top 10 for LLM Applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/)  
📖 **Bedrock Guardrails**: [Amazon Bedrock Guardrails](https://docs.aws.amazon.com/bedrock/latest/userguide/guardrails.html)

---

## 🔗 Hybrid Connectivity Security (Skill 3.3.2)

### AWS Site-to-Site VPN

- **IPSec encrypted tunnels** between on-premises and AWS VPC
- Two VPN tunnels per connection for high availability
- Supports **BGP** for dynamic routing or static routes
- **Accelerated VPN**: Uses AWS Global Accelerator for improved performance
- **VPN CloudWatch metrics**: Monitor tunnel status, data transfer

📖 **Documentation**: [Site-to-Site VPN User Guide](https://docs.aws.amazon.com/vpn/latest/s2svpn/)

### AWS Direct Connect

- **Dedicated network connection** to AWS (1 Gbps, 10 Gbps, 100 Gbps)
- **MACsec (802.1AE)**: Layer 2 encryption for 10 Gbps and 100 Gbps connections
- **Private VIF**: Access VPC resources
- **Transit VIF**: Access VPCs via Transit Gateway
- **Public VIF**: Access AWS public services
- Does NOT provide encryption by default (use VPN over Direct Connect for encryption)

📖 **Documentation**: [Direct Connect User Guide](https://docs.aws.amazon.com/directconnect/latest/UserGuide/)  
📖 **MACsec**: [Direct Connect MACsec](https://docs.aws.amazon.com/directconnect/latest/UserGuide/MACsec.html)

---

## 🔎 Network Access Analyzer (Skill 3.3.5)

### What You Need to Know

- Identifies **unintended network access** to your resources
- Analyzes VPC configurations: security groups, NACLs, route tables, IGWs, VPC endpoints
- Creates **Network Access Scopes** to define what access is expected vs unexpected
- Generates findings for access paths that violate scope definitions
- Helps validate network segmentation and least-privilege network access

📖 **Documentation**: [Network Access Analyzer](https://docs.aws.amazon.com/vpc/latest/network-access-analyzer/)

---

## 🌐 AWS IoT Core Policies (Skill 3.1.2)

### What You Need to Know

- **IoT policies** control what IoT devices can do (connect, publish, subscribe)
- **X.509 certificates** for device authentication
- **Thing groups** for managing device permissions at scale
- Security relevant for edge device protection strategies

📖 **Documentation**: [AWS IoT Core Security](https://docs.aws.amazon.com/iot/latest/developerguide/iot-security.html)

---

## 🌍 CloudFront Security (Skill 3.1.2)

### Security Features

- **Origin Access Control (OAC)**: Restrict S3 access to CloudFront only
- **Custom headers**: Add security headers (X-Frame-Options, Content-Security-Policy, HSTS)
- **Field-level encryption**: Encrypt specific POST fields at the edge
- **Signed URLs and cookies**: Time-limited access to private content
- **Geographic restrictions**: Block or allow by country
- **TLS/SSL**: Enforce HTTPS, configure minimum TLS version

📖 **Documentation**: [CloudFront Security](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/SecurityAndPrivacy.html)

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
- Know **Amazon Inspector** scan types: EC2, ECR container images, Lambda, network reachability (Skill 3.2.3)
- Understand **EC2 Image Builder** for golden AMI hardening pipelines (Skill 3.2.1)
- Know **Session Manager** vs **EC2 Instance Connect** for secure admin access (Skill 3.2.5)
- Understand **Patch Manager** for automated patching with maintenance windows (Skill 3.2.4)
- Know **CodeGuru Security** and **Amazon Q Developer** for pipeline security scanning (Skill 3.2.6)
- Understand **GenAI OWASP Top 10** and **Bedrock Guardrails** for AI application security (Skill 3.2.7)
- Know **Direct Connect MACsec** for Layer 2 encryption and **VPN over DX** for end-to-end encryption (Skill 3.3.2)
- Understand **Network Access Analyzer** for identifying unintended network access (Skill 3.3.5)

---

*Last updated: January 2026 (SCS-C03)*
