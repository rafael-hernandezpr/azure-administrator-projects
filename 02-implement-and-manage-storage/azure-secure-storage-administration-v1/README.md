# Azure Secure Storage Administration — V1

## Project Overview

This project demonstrates the design and administration of a secure Azure Storage environment using Azure Blob Storage and Azure Files.

The environment was configured with Microsoft Entra ID and Azure RBAC for identity-based access, storage account access keys for administrative testing, network restrictions, data protection features, lifecycle management, SAS-based delegated access, file-share snapshots, monitoring, and alerting.

The project also validates real operational scenarios including mapped Azure Files access from a local Windows computer, blob version recovery, SAS expiration, file restoration from snapshots, storage transaction monitoring, and an Azure Monitor alert that successfully triggered and sent an SMS notification.

## Business Problem

Organizations need secure, reliable, and cost-effective storage for both unstructured data and shared files. Poorly configured storage can expose sensitive data, make recovery difficult, increase costs, and leave administrators without visibility into activity.

This project addresses those risks by:

- securing access with Microsoft Entra ID, Azure RBAC, access keys, and SAS
- protecting and recovering data with versioning, soft delete, and file-share snapshots
- reducing cost and improving visibility through lifecycle management, metrics, and alerting

## Project Objectives

- Build a secure Azure Storage environment for blob and file-based workloads.
- Implement identity-based and key-based access methods.
- Protect data using versioning, soft delete, and file-share snapshots.
- Automate storage tiering and cleanup with lifecycle management.
- Validate delegated access using SAS and stored access policies.
- Monitor storage activity and configure an alert that notifies administrators when transaction activity exceeds a defined threshold.

## Project Highlights

- Secured Azure Storage access using Microsoft Entra ID, Azure RBAC, storage account keys, and time-limited SAS access.
- Configured Blob versioning and soft delete, then validated recovery after overwriting and deleting data.
- Mounted Azure Files to a local Windows computer as a `Z:` drive and verified bidirectional file access.
- Created and tested Azure Files snapshots by deleting a live file and restoring it successfully.
- Implemented lifecycle management to move blobs from Hot → Cool → Cold and delete inactive data after 90 days.
- Monitored Ingress, Egress, and Transactions with Azure Monitor and successfully triggered a transaction-based SMS alert.

## Azure Resources and Services Used

- Azure Storage Account
- Azure Blob Storage and Azure Files
- Microsoft Entra ID and Azure RBAC
- Storage Account Access Keys and SAS
- Blob Versioning, Soft Delete, and File Share Snapshots
- Lifecycle Management
- Azure Monitor Metrics, Alerts, and Action Groups
- Storage Account Network Restrictions


## Implementation

### 1. Create the Secure Storage Environment

### 2. Configure Blob Storage

### 3. Configure Microsoft Entra ID and Azure RBAC

### 4. Configure Blob Versioning and Soft Delete Recovery

### 5. Configure Azure Files and Map the Z: Drive

### 6. Validate Access Key and Microsoft Entra Authentication

### 7. Configure Lifecycle Management

### 8. Configure Stored Access Policy and SAS Expiration

### 9. Configure Azure Files Snapshot and Restore

### 10. Configure Azure Monitor Metrics and Alerts
