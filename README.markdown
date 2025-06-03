# Secure Cloud Architecture for E-Commerce Store

This project outlines a secure, scalable, and compliant cloud architecture for an e-commerce store hosted on Amazon Web Services (AWS). The architecture is designed to address vulnerabilities identified by the IriusRisk Threat Modeler, ensuring robust security, high availability, and cost optimization. The accompanying [Cloud Security Policy](#cloud-security-policy) establishes a framework to protect data, infrastructure, and user interactions, aligning with industry standards like ISO 27001, GDPR, and the AWS Well-Architected Framework.

## Table of Contents
- [Project Overview](#project-overview)
- [Architecture Design](#architecture-design)
- [Key Features](#key-features)
- [Technologies Used](#technologies-used)
- [Threat Mitigations](#threat-mitigations)
- [Cloud Security Policy](#cloud-security-policy)
- [Benefits of the Architecture](#benefits-of-the-architecture)
- [Setup and Installation](#setup-and-installation)
- [Contributing](#contributing)
- [License](#license)

## Project Overview
This project delivers a secure cloud-based architecture for an e-commerce store, designed using **draw.io** and implemented on AWS. The system addresses critical security threats such as spoofing, tampering, information disclosure, denial of service, and elevation of privilege, as identified by the IriusRisk Threat Modeler. After implementing recommended mitigations, the updated architecture achieved **zero vulnerabilities** in the final threat model analysis, ensuring a secure and resilient environment for e-commerce operations.

## Architecture Design
The architecture follows a modular, microservices-oriented approach with distinct tiers:
- **Web Tier**: Public subnet hosting web servers (EC2 instances) accessible via Elastic Load Balancer and AWS WAF for protection against web exploits.
- **App Tier**: Private subnet hosting application servers for business logic, isolated from public access.
- **Data Tier**: Amazon RDS in a dedicated database subnet with Multi-AZ deployment for high availability and automated failover.
- **Storage**: Amazon S3 for static assets (e.g., product images, invoices) with encryption and access controls.
- **Network**: Amazon VPC with public and private subnets, Security Groups, NACLs, and NAT Gateway for secure connectivity.

The design incorporates trust zones, proper segregation of public and private subnets, and enhanced security services to ensure data flow consistency and protection.

## Key Features
- **Scalability**: Multi-AZ deployment and Auto Scaling Groups ensure high availability and dynamic scaling.
- **Security**: AWS WAF, Security Groups, and IAM roles enforce fine-grained access control and protect against common threats.
- **Compliance**: Aligns with ISO 27001 and GDPR through encryption, user consent mechanisms, and regular audits.
- **Monitoring**: AWS CloudTrail and CloudWatch provide real-time logging and anomaly detection.
- **Cost Optimization**: Leverages Reserved Instances, Spot Instances, and S3 for cost-effective resource management.

## Technologies Used
- **AWS Services**:
  - Amazon VPC: Network configuration and subnet management.
  - EC2 Instances: Scalable compute for web and app servers.
  - Elastic Load Balancer: Traffic distribution for performance and availability.
  - Amazon RDS: Managed relational database with Multi-AZ and encryption.
  - Amazon S3: Secure storage for static assets.
  - AWS WAF: Protection against SQL injection, XSS, and other web exploits.
  - AWS IAM: Role-based access control and least privilege enforcement.
  - AWS CloudTrail & CloudWatch: Logging, monitoring, and auditing.
  - AWS Security Hub & GuardDuty: Centralized security alerts and threat detection.
  - AWS KMS: Customer-managed keys for encryption.
  - AWS Config: Compliance tracking and configuration audits.
  - AWS CloudFront: CDN for faster content delivery with signed URLs/cookies.
- **Tools**:
  - Draw.io: Architecture diagramming.
  - IriusRisk Threat Modeler: Threat identification and mitigation.

## Threat Mitigations
The IriusRisk Threat Modeler identified several threats, which were addressed in the updated architecture:
- **Spoofing**: MFA, AWS Cognito, and WAF with rate limiting prevent identity impersonation.
- **Tampering**: S3 bucket policies, input sanitization, and secure CI/CD pipelines mitigate data modification risks.
- **Repudiation**: CloudTrail, VPC Flow Logs, and CloudWatch ensure comprehensive auditing.
- **Information Disclosure**: S3 encryption, RDS encryption, and TLS 1.2+ secure data at rest and in transit.
- **Denial of Service**: AWS Shield, auto-scaling, and rate limiting protect against traffic spikes.
- **Elevation of Privilege**: Least privilege IAM policies, VPC Endpoint policies, and GuardDuty monitoring prevent unauthorized access.

The updated design achieved **zero vulnerabilities** after implementing these mitigations.

## Cloud Security Policy
The Cloud Security Policy ensures a secure and compliant environment:
- **Access Control**: RBAC via AWS IAM, MFA enforcement, and regular key rotation.
- **Encryption**: AES-256 for data at rest (RDS, EBS) and TLS 1.2+ for data in transit (CloudFront, ELB).
- **Logging & Monitoring**: CloudTrail for API logging, CloudWatch for real-time monitoring, and Security Hub for centralized alerts.
- **Incident Response**: Immediate system isolation using Security Groups/NACLs, stakeholder notification within one hour, and WAF rules for injection attack prevention.
- **Compliance**: Adherence to ISO 27001 and GDPR through risk assessments, data protection, and regular audits.

## Benefits of the Architecture
- **Performance**: Auto-scaling and load balancing ensure fast response times.
- **Security**: Multi-layered defenses (WAF, Security Groups, IAM) and encryption protect against threats.
- **Compliance**: Meets PCI DSS, ISO 27001, and GDPR requirements.
- **Resilience**: Multi-AZ RDS and auto-healing components ensure 24/7 availability.
- **Cost Efficiency**: Optimized with Reserved/Spot Instances and S3 versioning.
- **Analytics**: Supports integration with Amazon Athena or Redshift for customer behavior analysis.

## Setup and Installation
1. **Clone the Repository**:
   ```bash
   git clone https://github.com/your-repo/secure-ecommerce-architecture.git
   ```
2. **Configure AWS Services**:
   - Set up a VPC with public and private subnets.
   - Deploy EC2 instances for web and app tiers with Auto Scaling Groups.
   - Configure RDS with Multi-AZ and encryption.
   - Set up S3 buckets with encryption and access policies.
   - Enable CloudTrail, CloudWatch, and Security Hub for monitoring.
   - Configure WAF and Security Groups for traffic control.
3. **Deploy the Architecture**:
   - Use AWS CloudFormation or Terraform for automated deployment (templates not included in this repo).
   - Validate configurations using AWS Config and IAM Access Analyzer.
4. **Run Threat Modeling**:
   - Use IriusRisk to validate the architecture for vulnerabilities.

## Contributing
Contributions are welcome! To contribute:
1. Fork the repository.
2. Create a feature branch (`git checkout -b feature/your-feature`).
3. Commit changes (`git commit -m 'Add your feature'`).
4. Push to the branch (`git push origin feature/your-feature`).
5. Open a pull request.

Please ensure your contributions align with the project’s security and compliance goals.

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.