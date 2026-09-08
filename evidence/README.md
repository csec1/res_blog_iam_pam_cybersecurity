# Project Evidence & Verification Log

This directory contains visual artifacts, configuration verifications, and operational screenshots documenting the implementation, monitoring, access control, and audit capabilities across the project infrastructure.

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
│   ├── pam-policy.png
│   ├── secret-version-history.png
│   ├── vault-audit-enabled.png
│   └── vault-audit-event.png
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
```

## Artifact Descriptions

### IAM

- **`iam/okta-identity-center-federation.png`** — Shows identity federation between Okta and AWS IAM Identity Center, demonstrating centralized identity integration.
- **`iam/aws-temporary-role-access.png`** — Shows temporary AWS role access obtained through the federated identity workflow.

### Authorization

- **`authorization/permitted-action.png`** — Demonstrates a permitted action successfully authorized by the configured access-control policy.
- **`authorization/denied-action.png`** — Demonstrates an unauthorized action being denied by the authorization controls.

### PAM

- **`pam/privileged-access-request.png`** — Shows the protected privileged-access record stored in HashiCorp Vault under `secret/pam/test-privileged`.
- **`pam/pam-policy.png`** — Shows the `pam-privileged` Vault policy and its controlled permissions for PAM-managed secrets and metadata.
- **`pam/secret-version-history.png`** — Shows Vault KV version history for the privileged-access record, including four tracked versions and their creation/update metadata.
- **`pam/vault-audit-enabled.png`** — Shows Vault audit logging enabled through the file audit device at `/opt/vault/log/audit.log`.
- **`pam/vault-audit-event.png`** — Shows an audit event recording an authorized read operation against the PAM secret metadata path.

### HashiCorp Vault

- **`vault/vault-private-healthy.png`** — Shows the private Vault deployment operating in a healthy state.
- **`vault/vault-policy-audit.png`** — Shows Vault policy configuration and access controls applied to protected secret paths.

### Wazuh SIEM

- **`wazuh/wazuh-private-dashboard.png`** — Shows the central Wazuh security monitoring dashboard.
- **`wazuh/wazuh-agent-active.png`** — Shows active Wazuh agents connected to the monitoring infrastructure.
- **`wazuh/wazuh-security-results.png`** — Shows security alerts, detection results, rule matches, and monitoring findings.

### Audit & Recovery

- **`audit-recovery/cloudtrail-audit-evidence.png`** — Shows AWS CloudTrail audit evidence recording activity and API calls within the environment.
- **`audit-recovery/vault-backup-restore.png`** — Shows evidence of Vault backup creation and restoration testing for disaster recovery validation.
