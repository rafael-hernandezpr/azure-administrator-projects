# Azure Storage Private Networking Architecture — V3

## Project Overview

This project demonstrates how to secure Azure Storage by combining private networking, DNS integration, network access restrictions, and connectivity validation.

The environment was designed to allow authorized Azure resources to access Blob Storage through a Private Endpoint while restricting public access. A separate Service Endpoint path was also configured to compare both connectivity models and demonstrate how subnet-based access control differs from Private Link.

The project also includes an intentional DNS failure scenario where the Private DNS A record was removed, causing name resolution and connectivity to fail. The issue was then diagnosed, remediated, and validated by restoring the correct private DNS record.

## Business Problem

An organization stores sensitive files in Azure Storage and needs to reduce exposure to the public internet while still allowing approved Azure resources to access the data.

The environment must support secure private connectivity, restrict unauthorized public access, and provide a controlled alternative using Service Endpoints for subnet-based access.

The organization also needs administrators to be able to identify and resolve DNS-related connectivity failures affecting Private Endpoint access.

## Project Objectives

- Implement private connectivity to Azure Blob Storage using a Private Endpoint.
- Configure Private DNS so the storage account resolves to its private IP from inside the virtual network.
- Restrict public access to the storage account and validate that unauthorized external access is blocked.
- Configure and test a Service Endpoint to compare subnet-based access with Private Link.
- Validate connectivity using PowerShell from dedicated test virtual machines.
- Simulate a Private DNS failure, troubleshoot the issue, restore the DNS record, and confirm connectivity is recovered.

## Project Highlights

- Built a segmented Azure virtual network with dedicated subnets for client access, Private Endpoint connectivity, and Service Endpoint testing.
- Secured Azure Blob Storage with a Private Endpoint and validated private connectivity through the private IP `10.30.2.4`.
- Configured Azure Private DNS using `privatelink.blob.core.windows.net` and verified name resolution from inside the VNet.
- Restricted public network access and confirmed unauthorized access from an external client was blocked.
- Configured a Microsoft.Storage Service Endpoint and validated access from an approved subnet while external public access remained denied.
- Compared Private Endpoint and Service Endpoint connectivity behavior using real PowerShell and SAS-based tests.
- Simulated a DNS outage by deleting the storage A record, reproduced the connectivity failure, restored the record, and validated recovery.
- Performed end-to-end troubleshooting using `nslookup`, `Test-NetConnection`, and `curl`.

## Azure Resources and Services Used

- Azure Storage Account
- Azure Virtual Network and Subnets
- Azure Private Endpoint
- Azure Private DNS Zone
- Azure Service Endpoint
- Azure Virtual Machines
- Storage Network Access Rules
- Shared Access Signature (SAS)
- PowerShell connectivity testing

