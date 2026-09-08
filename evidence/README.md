# Project Evidence & Verification Log

This directory contains visual artifacts, configuration verifications, and operational screenshots documenting the implementation, active monitoring, and audit capabilities across the project infrastructure.

---

## Directory Structure

```text
evidence/
├── README.md
├── iam/
│   ├── okta-identity-center-federation.png
│   └── aws-temporary-role-access.png
├── authorization/
│   ├── permitted-action.png
│   └── denied-action.png
├── pam/
│   ├── privileged-access-request.png
│   └── jit-access-expiration.png
├── vault/
│   ├── vault-private-healthy.png
│   └── vault-policy-audit.png
├── wazuh/
│   ├── wazuh-private-dashboard.png
│   ├── wazuh-agent-active.png
│   └── wazuh-security-results.png
└── audit-recovery/
    ├── cloudtrail-audit-evidence.png
    └── vault-backup-restore.png

Evidence Inventory
1. Identity & Access Management (IAM)
iam/okta-identity-center-federation.png: Verification of identity federation configured between Okta and AWS IAM Identity Center.

iam/aws-temporary-role-access.png: Screenshot showing temporary credentials issued for federated role access.

2. Authorization Rules
authorization/permitted-action.png: Demonstration of a successful request where fine-grained authorization policies allow execution.

authorization/denied-action.png: Proof of access enforcement blocking unauthorized or out-of-scope actions.

3. Privileged Access Management (PAM)
pam/privileged-access-request.png: Audit log/UI confirmation of a privileged session request flow.

pam/jit-access-expiration.png: Evidence of Just-In-Time (JIT) elevated privileges automatically revoking after timeout.

4. HashiCorp Vault
vault/vault-private-healthy.png: Status dashboard showing HashiCorp Vault operating in a healthy, sealed/unsealed operational state.

vault/vault-policy-audit.png: Output showing configured access policies applied to key-value engines and secrets paths.

5. Security Monitoring (Wazuh SIEM)
wazuh/wazuh-private-dashboard.png: Overview of the central SIEM monitoring dashboard.

wazuh/wazuh-agent-active.png: Confirmation of active endpoints and log agents connected to the manager.

wazuh/wazuh-security-results.png: Verification of threat detection alerts, rule matches, and compliance checks.

6. Audit & Disaster Recovery
audit-recovery/cloudtrail-audit-evidence.png: AWS CloudTrail audit logs validating API call recording across the environment.

audit-recovery/vault-backup-restore.png: Verification of successful backup creation and restore testing for Vault state files.
