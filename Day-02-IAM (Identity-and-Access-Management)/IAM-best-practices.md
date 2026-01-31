# Day 2 – AWS IAM

This section focused on setting up AWS IAM in a way that supports secure access, traceability, and future team usage.

---

## Starting State

Initial account review showed:
- Root account MFA not enabled
- No IAM users present
- Permissions not structured through groups

  <img width="800" height="600" alt="image" src="https://github.com/user-attachments/assets/037c3e1b-8f3e-4c9f-8bb8-57cb9aeadbc3" />


---

## Root Account Hardening

Actions:
- MFA enabled on the root account
- Root access restricted to billing and account-level configuration


Root credentials should never be used for day-to-day operations.

---

## IAM User Setup

Configuration applied:
- Dedicated IAM user provisioned for daily access
- Console and programmatic access enabled

User:
```
devops-user
```

Purpose:
Individual IAM users improve accountability and reduce blast radius.

---

## Permission Structure (Group-Based)

Implementation details:
- IAM group `Developers` created
- Managed policies attached:
  - AmazonEC2ReadOnlyAccess
  - AmazonS3ReadOnlyAccess
- User associated with the group

  <img width="806" height="600" alt="image" src="https://github.com/user-attachments/assets/af88a1ad-2a29-4e3a-9bba-1971e5779bf5" />

---

## Least Privilege Validation

A minimal custom policy was applied to understand permission boundaries.

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": ["s3:ListBucket", "s3:GetObject"],
      "Resource": "*"
    }
  ]
}
```

Validation results:
- Read operations permitted
- Write and delete operations denied

Guidance:
Permissions should always be verified through testing, not assumed.

---

## Multi-Factor Authentication

MFA configuration:
- Virtual MFA device assigned to IAM user
- MFA enforcement verified during login

Guidance:
Console-access users should always have MFA enabled.

---

## Programmatic Access (AWS CLI)

Local CLI configuration:
```bash
aws configure
```

Identity verification:
```bash
aws sts get-caller-identity
```
<img width="880" height="609" alt="image" src="https://github.com/user-attachments/assets/c95563b6-30aa-4979-bc0f-90e4dd05752d" />

---


## Auditing and Visibility

Audit checks:
- CloudTrail reviewed for IAM-related activity
- Verified logging for user and policy changes


---

## Notes

- Group-based IAM simplifies long-term access management
- MFA significantly reduces credential-related risk
- Least privilege requires validation
- CloudTrail is essential for traceability

---

Day 2 complete — IAM configured with security and operational scalability in mind.
