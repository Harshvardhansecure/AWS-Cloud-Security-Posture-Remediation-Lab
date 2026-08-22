# Baseline Prowler Assessment Report

## Assessment Overview

A baseline AWS CSPM assessment was conducted using Prowler against a controlled, non-production AWS lab.

The lab included IAM identities, an Amazon EC2 instance, a default VPC, security groups, and a dedicated read-only Prowler scan role.

## Scan Results Summary

| Severity | Failed Checks |
|---|---:|
| Critical | 3 |
| High | 33 |
| Medium | 98 |
| Low | 114 |

> The default Prowler scan evaluates multiple AWS Regions and services. Repeated findings across unused Regions or services not deployed in this lab were excluded from the project’s risk register.

## Selected Findings

The following findings were selected for manual validation and remediation planning:

- Excessive AWS-managed IAM permissions
- IAM user without MFA
- Internet-exposed security group rules
- EC2 instance not requiring IMDSv2
- Unencrypted EBS volume
- Missing multi-Region CloudTrail logging
- VPC Flow Logs not enabled
- Weak IAM password-policy configuration

## Evidence Handling

The original Prowler CSV, HTML, and JSON reports are retained locally. They are not published because they contain AWS account and resource details.

Sanitized findings are documented in:

- `../../findings/finding-register.md`
- `../../evidence/baseline-summary.png`
