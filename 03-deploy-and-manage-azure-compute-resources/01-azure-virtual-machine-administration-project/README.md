# Azure Virtual Machine Administration, Troubleshooting & High Availability Project

## Project Overview

This project demonstrates hands-on administration and troubleshooting of Azure virtual machines in a realistic cloud environment. The work included VM deployment, disk management, performance testing, VM resizing, Encryption at Host, NSG troubleshooting, high-availability design, load balancing, failover testing, Availability Sets, VM Scale Sets, and resource movement between resource groups.

Several incidents were intentionally introduced to practice identifying problems, applying remediation, and validating that services continued working after the changes.

## Project Highlights

- Deployed and administered a Windows Server virtual machine in Azure
- Attached, initialized, formatted, and managed a dedicated data disk
- Simulated disk capacity pressure and expanded the disk from 32 GiB to 64 GiB
- Generated sustained CPU load and monitored Percentage CPU in Azure Monitor
- Resized the VM from 2 vCPUs / 4 GiB RAM to 4 vCPUs / 8 GiB RAM
- Enabled and validated Encryption at Host
- Configured NSG rules to restrict RDP access to the administrator's public IP
- Simulated an RDP outage with a higher-priority deny rule and restored access
- Deployed a VM Scale Set with instances across Availability Zones
- Configured a Standard Public Load Balancer, backend pool, TCP health probe, and HTTP rule
- Installed IIS on VMSS instances and validated traffic failover between zones
- Created an Availability Set with 2 fault domains and 2 update domains
- Deployed two VMs into the Availability Set and verified their placement
- Moved `vm-admin-01` to a different resource group and validated RDP access after the move

## Business Scenario

A company is running a Windows workload in Azure and needs to improve its reliability, security, performance, and operational resilience. The environment initially depends heavily on a standalone virtual machine, creating risks related to performance bottlenecks, storage limitations, access misconfiguration, and single-instance availability.

The Azure administrator is responsible for troubleshooting these issues, improving the VM configuration, strengthening network access, and introducing a more resilient architecture using VM Scale Sets, Availability Zones, Availability Sets, and Load Balancer health probes.

The final environment demonstrates how an administrator can investigate incidents, implement corrective actions, validate recovery, and improve the overall availability and manageability of Azure compute resources.

## Business Requirements

The company requires a secure and resilient Azure virtual machine environment that supports reliable administrative access, scalable compute capacity, additional storage, and high availability. The solution must allow administrators to monitor and resolve performance, disk, and connectivity issues, protect VM data with Encryption at Host, distribute traffic across healthy backend instances, and maintain service availability during VM or zone failures. The environment must also support common lifecycle operations such as resizing, disk expansion, availability configuration, and moving resources between resource groups.

## Azure Resources and Services Used

- Azure Virtual Machines, Virtual Machine Scale Sets, Availability Sets, and Availability Zones
- Azure Virtual Network, Subnet, Network Interfaces, Public IP Addresses, and Network Security Groups
- Azure Managed Disks, OS/Data Disks, disk resizing, and Encryption at Host
- Azure Load Balancer, Backend Pools, Health Probes, and Load-Balancing Rules
- Azure Monitor Metrics for CPU performance validation
- Azure Resource Groups and resource movement between groups
- Azure Cloud Shell, Azure CLI, PowerShell, and IIS for deployment, testing, and validation
