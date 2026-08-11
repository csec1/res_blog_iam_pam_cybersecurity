# res_blog_iam_pam_cybersecurity
Enterprise IAM, PAM, and Secrets Management architecture on AWS using Okta, AWS IAM Identity Center, HashiCorp Vault, and CyberArk concepts.
# IAM, PAM & Cloud Security Lab

A hands-on cybersecurity portfolio demonstrating identity federation, least-privilege access, privileged access management, temporary credentials, authorization boundaries, and audit validation across **Okta and AWS**.

> **Portfolio note:** This repository intentionally presents selected architecture, reasoning, validation evidence, and lessons learned rather than a turnkey reproduction of the environment.

## Overview

This project explores how enterprise identity and access controls can be designed and validated across a cloud environment.

The lab follows an identity-driven access model:

```text
User
  │
  ▼
Okta
  │
  ▼
AWS IAM Identity Center
  │
  ▼
Permission Set
  │
  ▼
AWS IAM Role
  │
  ▼
Temporary Credentials
  │
  ▼
AWS Resources
```

The objective was not simply to configure access, but to **prove that different identities receive the intended level of access and are denied when crossing authorization boundaries**.

## What I Built

The environment includes:

* Okta as the identity provider
* AWS IAM Identity Center for workforce access
* AWS permission sets representing different job functions
* Federated AWS console access
* Temporary AWS credentials
* Role-based authorization
* EC2 access-control testing
* CloudShell validation
* CloudTrail audit validation
* Positive and negative authorization tests
* Evidence collection and security documentation

## Roles Tested

| Identity | Intended Function | Access Model              |
| -------- | ----------------- | ------------------------- |
| Alice    | Administrator     | Administrative access     |
| Bob      | Developer         | Developer-oriented access |
| Charlie  | Auditor           | Read-only access          |

The important validation was not merely whether a user could log in, but whether the resulting AWS role enforced the intended authorization boundary.

## Validation Approach

Testing followed a simple security principle:

> **Authentication proves who the user is; authorization determines what that identity can do.**

Examples of validation included:

* Confirming successful federation
* Identifying the resulting AWS STS assumed role
* Testing permitted EC2 operations
* Testing prohibited EC2 operations
* Comparing developer and auditor behavior
* Reviewing CloudTrail events
* Correlating the observed activity with the expected identity and permission set

### Temporary Credential Validation

The resulting AWS identity was validated using:

```bash
aws sts get-caller-identity
```

The important observation was that access appeared as an **assumed IAM role**, rather than as a long-lived IAM user.

Example evidence pattern:

```text
AWSReservedSSO_<PermissionSet>_<RoleId>/<user>
```

This demonstrates the intended federation chain:

```text
Okta
 → IAM Identity Center
 → Permission Set
 → IAM Role
 → Temporary Credentials
```

## Authorization Boundary Example

A particularly useful negative test involved the auditor role attempting an operation outside its intended privileges.

Expected result:

```text
AWS-Auditor
    ↓
EC2 StartInstances
    ↓
AccessDenied
```

CloudTrail provided the corresponding audit evidence, allowing the authorization decision to be examined independently of the console experience.

This distinction is important: **being able to reach a service does not imply permission to perform every operation within that service.**

## Evidence Strategy

The public repository intentionally contains only selected evidence.

Evidence is presented to demonstrate:

* What was tested
* Why it was tested
* What result was expected
* What result was observed
* How the result was validated
* What security conclusion can be drawn

Sensitive implementation details, credentials, authentication secrets, unnecessary account information, and complete reproduction instructions are deliberately excluded.

## Architecture

The project is organized around four security layers:

### 1. Identity

Okta establishes the workforce identity and authentication boundary.

### 2. Federation

AWS IAM Identity Center provides the bridge between the external identity system and AWS access.

### 3. Authorization

Permission sets determine what a federated identity can do after entering AWS.

### 4. Detection & Validation

CloudTrail and AWS identity information provide independent evidence of the resulting activity.

## Key Security Lessons

### Least privilege must be tested

A permission set that *looks* restrictive is not enough. The actual authorization boundary should be tested with both allowed and denied actions.

### Access and authorization are different

A user may successfully enter the AWS console and see EC2 while still being unable to perform a particular EC2 operation.

### Temporary credentials reduce credential exposure

Federated access through IAM Identity Center produces temporary role-based credentials rather than requiring every workforce identity to maintain long-lived IAM access keys.

### Negative testing is valuable evidence

A successful login demonstrates authentication.

A correctly generated `AccessDenied` demonstrates that an authorization boundary is actually being enforced.

### Logs complete the story

CloudTrail makes it possible to correlate an action with the identity that performed it and verify whether the observed behavior matches the intended access model.

## Repository Structure

```text
blog/          → Published security write-ups
architecture/  → High-level architecture diagrams
diagrams/      → Supporting security diagrams
evidence/      → Selected, sanitized validation evidence
docs/          → Lessons learned and project notes
```

## Scope

This is a controlled learning and portfolio environment built to demonstrate practical understanding of:

* IAM
* Identity federation
* SSO
* RBAC
* Least privilege
* Temporary credentials
* Authorization testing
* CloudTrail
* AWS security architecture
* PAM concepts

Future work will extend the environment into **privileged access management and secrets management**, including the relationship between identity, privilege elevation, credential lifecycle, and auditability.

## Security Notice

This repository does **not** contain:

* Passwords
* Access keys
* Secret keys
* Session tokens
* MFA recovery information
* Private authentication links
* Sensitive production data
* Complete environment exports
* Unnecessary account-specific configuration

All published evidence is intentionally sanitized.

## Project Status

**IAM / Federation / Authorization Validation:** Completed

**PAM / Privileged Access Controls:** Next phase

**Secrets Management:** Planned

---

## Author

Cybersecurity portfolio project focused on practical **IAM, PAM, cloud security, identity federation, and security validation**.

The emphasis is on demonstrating not only *how access was configured*, but how the resulting security controls were **tested, challenged, observed, and evidenced**.
