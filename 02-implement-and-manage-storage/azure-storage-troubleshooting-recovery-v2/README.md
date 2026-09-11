# Azure Storage Troubleshooting & Recovery

## Project Overview

This project demonstrates the administration, troubleshooting, backup, recovery, access control, and monitoring of Azure Storage using Azure Files, Recovery Services vaults, Microsoft Entra ID, Azure RBAC, Log Analytics, and KQL.

The environment was intentionally used to simulate realistic storage incidents, including accidental file deletion, file modification, backup interruption, and data-access failures. Each issue was investigated, remediated, and validated to demonstrate practical Azure Administrator skills.

## Business Scenario

A company stores shared departmental files in Azure Files and requires reliable protection against accidental deletion, unwanted file changes, backup interruptions, and unauthorized or misconfigured access.

The cloud administrator is responsible for protecting the file share, maintaining recovery points, restoring affected files, troubleshooting user access, validating backup health, and monitoring backup-related activity through centralized logging.

## Project Highlights
Configured Azure Files backup using a Recovery Services vault and backup policy.
Created and validated recovery points for the company-files share.
Recovered an accidentally deleted business file from backup.
Restored a modified Excel file using an earlier recovery point and Overwrite Existing.
Troubleshot Microsoft Entra ID and Azure RBAC data-plane access for Azure Files.
Simulated disabled backup protection, retained existing recovery data, resumed protection, and validated a successful backup.
Configured Recovery Services vault diagnostic settings to send backup telemetry to Log Analytics.
Used KQL to investigate protected-instance status and recovery-point activity.

## Azure Resources and Services Used

- Azure Storage Account
- Azure Files
- Recovery Services Vault
- Azure Backup
- Microsoft Entra ID
- Azure RBAC
- Azure Monitor Diagnostic Settings
- Log Analytics Workspace
- Kusto Query Language (KQL)

---

### 1. Storage Environment Deployment

