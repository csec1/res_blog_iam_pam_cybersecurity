# Privileged Access Management Architecture

A practical implementation of a privileged access management architecture using **Okta, AWS IAM Identity Center, AWS IAM, HashiCorp Vault, private AWS networking, a bastion host, and Wazuh**.

## Blog

Read the full implementation and architecture walkthrough:

[Building a Practical Privileged Access Management Architecture with Okta, AWS IAM, HashiCorp Vault, and Wazuh](https://github.com/csec1/csec1.github.io/blob/master/_posts/2026-09-09-practical-privileged-access-management-okta-aws-vault-wazuh.md)

## Technologies

- Okta
- AWS IAM Identity Center
- AWS IAM
- HashiCorp Vault
- AWS VPC
- AWS EC2
- VPC Peering
- Bastion Host
- Wazuh
- Wazuh Agent
- Vault KV Secrets Engine
- Vault Audit Logging

## What the Blog Covers

- Identity federation through Okta and AWS IAM Identity Center
- Temporary AWS IAM role authorization
- Privileged access control concepts
- HashiCorp Vault as a privileged credential boundary
- Vault policies and least-privilege access
- Vault KV version history
- Vault audit logging
- Private AWS networking and VPC peering
- Bastion-based administrative access
- Wazuh endpoint monitoring
- Wazuh Manager, Indexer, and Dashboard architecture
- Temporary NAT-based installation access
- Security validation and evidence collection

## Purpose

This project demonstrates how identity, authorization, privileged credential management, network isolation, security monitoring, and audit logging can work together as a single privileged-access security architecture.

The goal is not simply to deploy individual security products, but to understand how the controls interact and how the resulting architecture can be validated through security evidence.
