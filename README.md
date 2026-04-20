# CI/CD Pipeline Security in AWS: Attack Simulation & Detection Evaluation

**MSc Dissertation — Umesh Udayan**
**University of Salford, Manchester — 2025**
**Programme: MSc Cyber Security, Threat Intelligence & Cyber Forensics**

---

## Overview

This dissertation investigates a critical and underexplored risk in modern software delivery: 
the security of CI/CD pipelines hosted on AWS. While organisations increasingly rely on 
automated pipelines for deployment, the security of those pipelines — and the ability of 
native AWS tooling to detect attacks against them — has received limited empirical study.

This research addresses that gap through a fully reproducible, evidence-based methodology.

---

## What Was Built

A real AWS attack testbed was designed and deployed using:

- **Terraform** — Infrastructure as Code for reproducible environment provisioning
- **GitHub Actions** — CI/CD pipeline simulation with controlled misconfigurations
- **AWS Services** — EC2, S3, VPC, IAM, GuardDuty, CloudTrail, IAM Access Analyzer

Controlled misconfigurations were deliberately introduced including hardcoded secrets, 
wildcard IAM policies, and unpinned GitHub Actions — mirroring real-world supply chain risks.

---

## Attack Scenarios Simulated

Three attack scenarios were executed, each mapped to MITRE ATT&CK:

| Attack | MITRE TTP | CVSS Score |
|--------|-----------|------------|
| PR Title Injection | T1059 | 9.0 Critical |
| Poisoned GitHub Action Supply Chain | T1554 | 8.5 High |
| IAM Credential Reuse | T1078 | 8.2 High |

---

## Key Finding

> **GuardDuty generated zero alerts on trusted-identity pipeline abuse despite 100% 
> CloudTrail logging coverage** — proving a critical detection gap in AWS-native security 
> posture that has direct implications for organisations relying solely on GuardDuty for 
> pipeline security monitoring.

Additionally, a head-to-head tool comparison revealed:
- **Gitleaks** successfully detected injected AWS credentials
- **TruffleHog** returned zero matches on the identical dataset

This validates the need for layered, multi-tool detection strategies.

---

## Five-Pillar DevSecOps Framework

The research produced a practical, actionable framework for engineering teams:

| Pillar | Focus |
|--------|-------|
| 1. Secrets Management | Prevent hardcoded credentials in repositories and pipelines |
| 2. Least-Privilege IAM | Eliminate wildcard policies and enforce minimum permissions |
| 3. Action Pinning | Pin GitHub Actions to specific commit SHAs to prevent supply chain attacks |
| 4. Pipeline Sanitisation | Validate and sanitise all pipeline inputs including PR titles |
| 5. Detection Integration | Layer GuardDuty with Gitleaks, TruffleHog, Terrascan, and TFSec |

Framework aligned to: **OWASP CI/CD Top 10**, **MITRE ATT&CK**, **Google SLSA**

---

## Tools & Technologies Used

**AWS:** EC2, S3, VPC, IAM, CloudFront, GuardDuty, CloudTrail, IAM Access Analyzer

**IaC & CI/CD:** Terraform, GitHub Actions

**Security Tooling:** Gitleaks, TruffleHog, Terrascan, TFSec, OPA Rego

**Languages:** Python (log analysis automation), Bash

**Frameworks:** MITRE ATT&CK, OWASP CI/CD Top 10, CVSS v3.1, Google SLSA, NIST

---

## Dissertation Document

The full dissertation is available here:

[Umesh_Udayan_MSc_Dissertation_2025.pdf](./Umesh_Udayan_MSc_Dissertation_2025.pdf)

---

## Ethical Statement

All offensive security research and attack simulations were conducted exclusively within 
isolated, controlled AWS environments built and owned by the researcher. No live systems, 
real users, or external infrastructure were affected at any point. All research adheres to 
responsible disclosure principles and the UK Computer Misuse Act 1990.

---

## Author

**Umesh Udayan**
MSc Cyber Security, Threat Intelligence & Cyber Forensics
University of Salford, Manchester — 2025

[LinkedIn](https://linkedin.com/in/umeshudayan9961) | 
[GitHub](https://github.com/umeshudayan)
