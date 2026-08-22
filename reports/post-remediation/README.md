# Post-Remediation Prowler Assessment Report

## Purpose

This report will document the security posture of the AWS lab after selected high-priority findings have been remediated.

## Planned Remediation Scope

The initial remediation phase will focus on:

- Removing excessive IAM permissions
- Enabling MFA for the test IAM user
- Restricting public SSH and other unnecessary inbound security-group rules
- Requiring IMDSv2 on the EC2 instance
- Encrypting the EBS volume
- Strengthening the IAM password policy

CloudTrail and VPC Flow Logs are planned as a later cloud-detection-and-response phase.

## Validation Method

After remediation, Prowler will be run again. The post-remediation results will be compared with the baseline scan to verify that selected findings are resolved or reduced.

## Results

| Metric | Baseline | Post-Remediation |
|---|---:|---:|
| Critical findings | 3 | TBD |
| High findings | 33 | TBD |
| Medium findings | 98 | TBD |
| Low findings | 114 | TBD |
| Selected findings remediated | 0 | TBD |

Sanitized post-remediation evidence will be added as:

`../../evidence/remediation-summary.png`
