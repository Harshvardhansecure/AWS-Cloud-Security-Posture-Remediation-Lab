# AWS Cloud Security Posture & Remediation Lab

An end-to-end AWS Cloud Security Posture Management (CSPM) lab using Prowler to identify and validate misconfigurations across IAM, EC2, VPC, and security groups. Findings are prioritized by exposure and impact, remediated using AWS security controls, and re-scanned to demonstrate measurable posture improvement.

> **Scope:** This is a controlled, non-production learning environment. No real customer data, credentials, or sensitive resource details are included in this repository.

## Objectives

- Build a small AWS security lab with realistic, controlled misconfigurations.
- Run a baseline CSPM assessment with Prowler.
- Validate findings manually instead of relying only on scanner output.
- Prioritize remediation based on exposure, exploitability, identity permissions, and impact.
- Apply security improvements and verify them through a post-remediation scan.

## Lab Environment

| Component | Purpose |
| --- | --- |
| AWS IAM | Identity, MFA, and least-privilege assessment |
| Amazon EC2 | Compute-security and instance-exposure checks |
| Amazon VPC | Network segmentation and exposure assessment |
| Security Groups | Inbound-access and attack-surface review |
| Prowler | CSPM assessment, reporting, and remediation validation |

## Methodology

```text
AWS Lab
  → Baseline Prowler Scan
  → Finding Validation
  → Risk Prioritization
  → Remediation
  → Post-Remediation Scan
  → Evidence-Based Report
```

## Baseline Assessment

Prowler was connected to AWS using a dedicated read-only scan role. The baseline scan assessed the AWS account configuration and produced findings across identity, network, compute, logging, and account-security domains.

### Findings Selected for Review

| Finding | Area | Risk | Status |
| --- | --- | --- | --- |
| IAM user without MFA | IAM | Stolen credentials could enable account access | Open / remediated |
| Excessive IAM permissions | IAM | Privilege escalation or unintended administrative actions | Open / remediated |
| SSH exposed to the Internet | Security Group | Increases brute-force and unauthorized-access risk | Open / remediated |
| Public EC2 exposure | EC2/VPC | Expands the external attack surface | Under review |
| Missing centralized audit trail | Logging | Limits investigation and audit visibility | Planned |

> Replace the status values above after reviewing your Prowler results. Only include findings you personally validated.

## Risk Prioritization Approach

Findings were not prioritized by severity alone. Each finding was evaluated using the following context:

- Is the resource internet-facing?
- Does the affected identity have privileged permissions?
- Is the resource used for a production-like workload or a test workload?
- Does successful exploitation enable lateral movement or access to other services?
- Are compensating controls already in place?

For example, public SSH access combined with a public EC2 instance is a higher priority than a similar configuration on an isolated resource with no public route.

## Remediation Plan

| Issue | Remediation | Validation |
| --- | --- | --- |
| IAM user without MFA | Enable MFA or remove the non-essential user | Re-run relevant Prowler IAM checks |
| Excessive permissions | Replace broad permissions with a least-privilege policy | Review policy and re-scan |
| Public SSH rule | Restrict TCP/22 to a trusted administrative IP range or remove it | Inspect security group and re-scan |
| Public EC2 exposure | Remove public access where it is not required | Verify route, IP assignment, and findings |
| Missing audit trail | Enable a minimal, cost-controlled CloudTrail configuration in a later phase | Verify applicable CloudTrail checks |

## Evidence

Add only sanitized evidence to this repository:

- `evidence/baseline-summary.png` — baseline Prowler summary
- `evidence/remediation-summary.png` — post-remediation Prowler summary
- `reports/` — redacted CSV or HTML extracts, if needed
- `findings/` — finding register and manual-validation notes

Before publishing, redact AWS account IDs, public IP addresses, resource names, email addresses, ARNs, and all credentials or session tokens.

## Results

_Update this section once the remediation scan is complete._

| Metric | Baseline | After Remediation |
| --- | ---: | ---: |
| Critical findings | TBD | TBD |
| High findings | TBD | TBD |
| Medium findings | TBD | TBD |
| Selected findings remediated | 0 | TBD |

## Skills Demonstrated

- AWS IAM security and least-privilege review
- EC2, VPC, and security-group hardening
- CSPM assessment with Prowler
- Manual validation of cloud-security findings
- Risk-based remediation prioritization
- Security posture measurement and reporting

## Disclaimer

This repository is for educational and portfolio purposes. The environment is intentionally small and uses controlled misconfigurations only. It must not be treated as a production AWS security design.
