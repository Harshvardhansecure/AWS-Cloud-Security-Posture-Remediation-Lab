# Finding Register

This register documents relevant Prowler findings that were manually validated in the AWS Console. The full Prowler scan included checks for unused services and all enabled AWS Regions; those are not treated as individual project risks.

| ID | Finding | Prowler Check ID | Service | Severity | Risk Context | Priority | Status |
|---|---|---|---|---|---|---|---|
| F-01 | AWS-managed administrative IAM policy attached | `iam_aws_attached_policy_no_administrative_privileges` | IAM | Critical | Broad `*:*` permissions can enable unauthorized administrative actions and privilege escalation. | Critical | Open |
| F-02 | IAM user without MFA | `iam_user_mfa_enabled_console_access` | IAM | High | A stolen password could allow console access without a second authentication factor. | High | Open |
| F-03 | Internet-exposed security group rule | `ec2_securitygroup_allow_ingress_from_internet_to_tcp_port_22` and `ec2_securitygroup_allow_ingress_from_internet_to_any_port` | EC2 / Security Groups | High | Public inbound access, including SSH, increases brute-force and unauthorized-access risk. | High | Open |
| F-04 | EC2 instance does not require IMDSv2 | `ec2_instance_imdsv2_enabled` | EC2 | High | IMDSv1 can increase the risk of credential theft through server-side request forgery. | High | Open |
| F-05 | EBS volume is not encrypted | `ec2_ebs_volume_encryption` | EC2 / EBS | High | Data stored on the instance volume is not protected at rest. | High | Open |
| F-06 | No multi-Region CloudTrail trail | `cloudtrail_multi_region_enabled` | CloudTrail | High | Missing centralized audit logging reduces investigation and audit visibility. This finding repeats across Regions and is tracked as one remediation item. | Medium | Planned |
| F-07 | VPC Flow Logs are not enabled | `vpc_flow_logs_enabled` | VPC | Medium | The lab lacks network telemetry for investigation and detection use cases. | Medium | Planned |
| F-08 | IAM password policy does not require 14 characters | `iam_password_policy_minimum_length_14` | IAM | Medium | Weak account password controls increase credential-attack risk. | Medium | Open |
